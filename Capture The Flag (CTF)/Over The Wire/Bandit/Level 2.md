![](../../../assets/Pasted%20image%2020250726125215.png)This Challenge is about reading spaced file 

![](../../../assets/Pasted%20image%2020250726125347.png)### 

🎯 **Challenge**

- Find the password for the next level (bandit3).
    
- The password is stored in a file called `spaces in this filename`.
    

---

### 🧠 **What’s Tricky About It**

- The filename has **spaces**, which messes with how the shell interprets input.
    
- By default, the shell splits on spaces unless you tell it not to.
    

---

### 🧪 **Steps Explained**

1. You run `ls` to list files:

    `bandit2@bandit:~$ ls spaces in this filename`
    
    ✅ Shows a file literally named: `spaces in this filename`.
    
2. You try to read it using:
    
    `cat spaces in this filename`
    
    ❌ **Fails** because the shell sees this as four separate arguments:
    
    - `cat` tries to open:
        
        - `spaces`
            
        - `in`
            
        - `this`
            
        - `filename`
            
3. The correct way:

    `cat "spaces in this filename"`
    
    ✅ Now you’re **quoting** the filename so the shell treats it as **one string**.
    

---

### ✅ **Other Ways You Could Do It**

- Escape spaces:
    
    `cat spaces\ in\ this\ filename`
    
- Tab complete:

    `cat spaces<tab>`
    
    (It auto-fills and escapes spaces)
    
- Single quotes also work:
    
    `cat 'spaces in this filename'`