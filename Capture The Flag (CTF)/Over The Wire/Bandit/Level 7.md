![](../../../assets/Pasted%20image%2020250726220841.png)


![](../../../assets/Pasted%20image%2020250726221859.png)

### Challenge:

> Find the password for the next level.  
> It is stored in the file `data.txt`, next to the word `millionth`.

---

### 🧠 File Structure:

Each line in `data.txt` looks like a key–value pair, like this:


`first	9iwAhT1wEi6sP1Qw second	odwjnW9ZPwWjKkdc ... millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc ...`

---

### ✅ My Approach:

`grep "millionth" data.txt`

### 🔍 What It Does:

- Scans the entire file
    
- Finds the **exact line** that contains the word `millionth`
    
- Prints that line, including the password
    

---

### 🧾 Output:


`millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

So the password is:

`dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

---

### 🧠 Notes:

- This is a **key-value format**, separated by tabs (`\t`)
    
- You didn’t need to use `tail`, `awk`, or `cut` because `grep` alone gave you the exact match
    
- You could use `cut` to extract the password directly like this:
    


`grep "millionth" data.txt | cut -f2`