
![](../../../assets/Pasted%20image%2020250806105122.png)


## 📌 Challenge Description:

> The password for the next level is stored in `/etc/bandit_pass/bandit20`.  
> You’re provided with a **setuid binary** in the home directory.  
> Running it correctly will give you access to the password.

---

## What is `setuid`?

`setuid` (Set User ID) is a special file permission in Linux. When it's applied to a binary file, it allows that program to run **with the privileges of the file owner**, rather than the user who runs it.

> In short: You temporarily “borrow” someone else’s permissions while running the program.

This is useful for things like allowing users to change passwords or access restricted files — and it's also a common point of interest in privilege escalation during security testing and CTFs.

---

## Step-by-Step Solution

![](../../../assets/Pasted%20image%2020250806105056.png)
### 1️ List files in the home directory:

- `ls

 Output 

- `bandit20-do`

---

### 2️ Check detailed permissions and ownership:

- `ls -la`

 Output:

- `-rwsr-x--- 1 bandit20 bandit19 12345 Aug  5 10:00 bandit20-do`

- `rwsr-x---`: The **`s`** in the user’s execute spot (`rws`) means the file has the **setuid** bit set.

- Owner: `bandit20`  So when we run this, we run it **as bandit20**.

---

### 3️ Run the binary to see how it works:


- `./bandit20-do`

 Output:

- `Run a command as another user. Usage: ./bandit20-do <command>`

This tells us that it can run a command **as bandit20**, which is exactly what we need.

---

### 4️ Check if the password file exists:


- `ls /etc/bandit_pass`

 You’ll see the file we’re after:

   The file we after 
   
- `bandit20`

---

### 5️ Use the SUID binary to read the password:


- `./bandit20-do cat /etc/bandit_pass/bandit20`

 Output:

- `<the_password_for_bandit20>`

Success! You’ve used a `setuid` binary to gain access to the next level.

---

## Final Thought

This challenge is a great intro to the **power of file permissions** in Linux, especially the `setuid` bit. It shows how a file can safely and intentionally grant temporary privilege escalation for specific tasks — something used in both legitimate systems and real-world exploits.

It’s also a reminder that:

> Understanding permissions is just as important as understanding code.

---

## Learn More About `setuid`

Here are a few beginner-to-advanced resources to help you dive deeper:

1. **What is setuid? – HowToGeek**  
    📎 https://www.howtogeek.com/727406/what-are-setuid-setgid-and-sticky-bits-in-linux/
    
2. **DigitalOcean – Linux Permissions: SUID, SGID, and Sticky Bit**  
    📎 https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions
    
3. **GTFOBins – Exploiting SUID in CTFs**  
    📎 https://gtfobins.github.io/  
    _(Great for advanced/CTF-specific use cases)_
    
4. **Explainshell (to break down Linux commands)**  
    📎 https://explainshell.com/


