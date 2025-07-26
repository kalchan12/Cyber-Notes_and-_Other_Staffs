![](../../../assets/Pasted%20image%2020250726223637.png)

![](../../../assets/Pasted%20image%2020250726223830.png)

## Challenge:

> The password is in `data.txt`, hidden among **a few human-readable strings**, and it’s **preceded by several `=` signs**.

So the key clues are:

- It's human-readable
    
- It comes **after `=` characters**
    
- Most of the file probably looks like garbage (non-printable chars)
    

---

## ✅ Tools for the Job:

- `strings`: to pull human-readable text out of a binary-ish file
    
- `grep`: to filter for lines containing `===...`
    

---

## 🔥 Final Command:


`strings data.txt | grep '===='`

---

### 🔍 Explanation:

|Command|What it does|
|---|---|
|`strings data.txt`|Extracts all **human-readable** ASCII strings|
|`grep '===='`|Filters only lines that contain **multiple equal signs** (likely what the challenge hinted at)|