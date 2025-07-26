
![](../../../assets/Pasted%20image%2020250726220249.png)


![](../../../assets/Pasted%20image%2020250726220342.png)


## 🧠 Challenge 

> You're told:

- The password is **somewhere on the server**
    
- The file:
    
    - ✅ Is **owned by user** `bandit7`
        
    - ✅ Is in **group** `bandit6`
        
    - ✅ Is exactly **33 bytes** in size
        

---

## ✅ Step-by-step Breakdown

### 🔍 Step 1: Run `find` with multiple filters

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

#### What each part means:

|Part|Purpose|
|---|---|
|`find /`|Start searching from the **root** of the filesystem|
|`-type f`|Only return **files**, not directories|
|`-user bandit7`|File must be owned by **user** `bandit7`|
|`-group bandit6`|File must belong to **group** `bandit6`|
|`-size 33c`|File must be **exactly 33 bytes** (`c` means bytes)|
|`2>/dev/null`|Suppress all the **permission denied errors** so output is clean|

### 🧾 Output:

```
/var/lib/dpkg/info/bandit7.password
```

Boom 💥  that’s the **only** file on the system that matches all criteria.

---

### 🐱 Step 2: Read the file with `cat`

```bash
cat /var/lib/dpkg/info/bandit7.password
```

Output:

```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

🎯 And that’s your password for **Bandit Level 7**.

---

## ✅ Why This Solution Is Clean

- You didn't need to dig manually
    
- You filtered **based on metadata**, not content
    
- You avoided permission spam with `2>/dev/null`
    

---
