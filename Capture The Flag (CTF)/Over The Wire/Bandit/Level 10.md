![](../../../assets/Pasted%20image%2020250726224114.png)

![](../../../assets/Pasted%20image%2020250726224733.png)

###  Challenge:

> The password for the next level is stored in the file `data.txt`, which contains **a Base64 encoded string**.

---

### 📂 Step 1: View the file contents


`cat data.txt`

#### Output:

`VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==`

---

### 🧠 Step 2: Decode the Base64 string

You can use `echo` and pipe it into `base64 -d`:

`echo "VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==" | base64 -d`

#### Output:

`The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

---

### 🛠️ Notes:

- Base64 is just **encoding**, not encryption — you don’t need a key to decode it.
    
- Strings ending in `=` or `==` are often Base64 — a big hint during CTFs or pentesting.
    
- You can also decode directly from a file:
    
    `base64 -d data.txt`


**Another Method** 

- There are many websites that can decode base64 
    
![](../../../assets/Pasted%20image%2020250726225859.png)


- The website https://www.base64decode.org/
- Another Website which is literally for almost anything you can think of is Cyberchef
   Cyberchef  https://gchq.github.io/CyberChef/
