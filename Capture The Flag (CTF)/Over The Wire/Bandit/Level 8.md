![](../../../assets/Pasted%20image%2020250726222752.png)

![](../../../assets/Pasted%20image%2020250726223135.png)
## Challenge:

> The password is in `data.txt`  
> It's the **only line that appears exactly once**

So, this is a **"find the unique line"** challenge.

---

## 🛠️ Tools You'll Use:

- `sort`: to group identical lines together
    
- `uniq`: to filter duplicates
    
---

## ✅ Final Command:

`sort data.txt | uniq -u`

---

### 🔍 Explanation:

|Command|What it does|
|---|---|
|`sort data.txt`|Groups all identical lines next to each other|
|`uniq -u`|Shows **only** lines that appear **once**|

This will output **only the unique line** — which is your password.