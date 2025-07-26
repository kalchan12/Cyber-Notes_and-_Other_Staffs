![](../../../assets/Pasted%20image%2020250726154215.png)
This is the Challenge we have to solve. 
There is a hidden directory which contains the password for the next level, so we have to find that out.

![](../../../assets/Pasted%20image%2020250726154643.png)

We will log in as usual suing sshpass

![](../../../assets/Pasted%20image%2020250726155202.png)

#### 🎯 **Challenge:**

Find the password for the next level hidden somewhere inside the `inhere` directory.

---

#### 🧠 **Solution Breakdown:**

1. Ran `ls` inside `inhere` showed nothing.
    
2. Tried `ls -l` (long listing)  still showed **no files**.
    
3. Used `ls -a`  **boom**, found hidden file:
    
    `...Hiding-From-You`
    
4. Ran:
    
    `cat ...Hiding-From-You`
    
    and got the password
    
    
---

#### ❓ **Why `ls -l` Didn’t Work:**

- `ls -l` shows **detailed info** (permissions, size, etc.) but **not hidden files** unless combined with `-a`.
    
- Hidden files start with a dot `.` in this case, it's `...Hiding-From-You` (starts with three dots).
    
- So both `ls` and `ls -l` missed it.
    

> Only `ls -a` or `ls -la` shows hidden files **with or without details**.