![](../../../assets/Pasted%20image%2020250726214322.png)
From the task we understand that we should look for specific properties like what we see above the picture 

![](../../../assets/Pasted%20image%2020250726215403.png)


## Challenge:

Find a file under the `inhere` directory that is:

- ✅ Human-readable
    
- ✅ Exactly **1033 bytes** in size
    
- ✅ **Not executable**
    

---

## ✅ Best Tool for This Job: `find`

You can solve this **efficiently and automatically** using the `find` command with the right filters.

---

## 🚀 Final One-Liner Solution:



`find -type f -size 1033c ! -executable -exec file {} \; | grep "ASCII text"`

### 🔍 Breakdown:

- `find : start looking inside the `inhere` directory
    
- `-type f`: look for files only
    
- `-size 1033c`: size exactly 1033 bytes (c = bytes)
    
- `! -executable`: not executable
    
- `-exec file {} \;`: run `file` on each result to check readability
    
- `grep "ASCII text"`: filter only human-readable files
    

---

## 🧾 What to Do After You Find It:

Let’s say the command outputs something like:

`inhere/maybehere07 : ASCII text`

Then just run:

`cat inhere/maybehere07

And boom 💥— password for Level 6.