![](../../../assets/Pasted%20image%2020250806094646.png)

## Challenge Description:

> There are 2 files in the home directory: `passwords.old` and `passwords.new`.  
> The password for the next level is in `passwords.new` and is the **only line** that has been changed between the two files.

![](../../../assets/Pasted%20image%2020250806095314.png)

## Method 1 – Using `diff`


![](../../../assets/Pasted%20image%2020250806094814.png)

### 🧰 Command:

`diff passwords.old passwords.new`

### 📖 Explanation:

- `diff`: compares two files **line by line**
    
- The output shows which lines differ and in what way

---
## Method 2 – Using `uniq`

![](../../../assets/Pasted%20image%2020250806094927.png)
### Command:

`cat passwords.old passwords.new | sort | uniq -u`

###  Explanation:

- `cat ...`: combines both files into one stream
    
- `sort`: sorts all lines (required for `uniq` to work correctly)
    
- `uniq -u`: prints only lines that appear **exactly once** in the combined data
    
---

## Method 3 – Using `comm`

![](../../../assets/Pasted%20image%2020250806094954.png)
### Command:

`comm -13 <(sort passwords.old) <(sort passwords.new)`

### Explanation:

- `sort file`: sorts both files (required for `comm`)
    
- `<(command)`: process substitution (lets us use command output like a file)
    
- `comm -13`: compares both sorted files and:
    
    - `-1`: suppresses lines only in `passwords.old`
        
    - `-3`: suppresses lines in both files
        
    - So it shows **only lines unique to `passwords.new`**
        

 This method also isolated the correct password.

---

## Method 4 – Grepping from `diff` output

![](../../../assets/Pasted%20image%2020250806094901.png)
### Command:

`diff passwords.old passwords.new | grep '>' | cut -d' ' -f2-`

###  Explanation:

- `diff`: shows file differences
    
- `grep '>'`: filters only the new line from `passwords.new`
    
- `cut -d' ' -f2-`: removes the `>` symbol and extracts the password
    

 Result: Clean one-liner to directly extract the password.

---

## **Pro tip**

>  **Always start with the simplest tool or command** that solves the problem.  
> Complexity should only be added **when there's a good reason for it.**

### Fav Quote:

> _"Genius admires simplicity; the fool admires complexity."_

This applies perfectly to this challenge. While `comm`, `uniq`, and `cut` are cool, the `diff` command alone was enough to solve it cleanly and quickly. Use the fancy stuff only when the basic tools fall short.

---

### Final Thought 

This challenge was a great example of how **simple tools solve real problems**. At its core, it tested your ability to **spot a subtle change between two files**, a common task in both security work and general system admin tasks.

More importantly, it reinforced a valuable mindset:

> **Start simple. Expand only when needed.**

Whether using `diff`, `uniq`, `comm`, or `grep`/`cut`, the key takeaway is that Unix provides **many paths to the same answer** — but the best one is often the clearest.

Mastering these tools not only improves your efficiency in CTFs but also builds habits that translate directly to **real-world problem solving**.