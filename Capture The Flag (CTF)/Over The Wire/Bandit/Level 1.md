![](../../../assets/Pasted%20image%2020250726115124.png)

Before getting into the CTF, lets learn why we should use sshpass rather than regular ssh .
in the first Challenge we have seen how we logged into ssh server with the regular ssh command and lets see the difference between the two 
First mission was : log into the server as user `bandit0`. Easy? Kinda. Repetitive? Very. Let’s walk through both the **basic** and the **pro** methods.

---

### 🛠️ Method 1: The Normal, Responsible Way

`ssh bandit0@bandit.labs.overthewire.org -p 2220`

- This is your classic SSH login.
    
- `bandit0` = username
    
- `-p 2220` = non-default port
    
- After running it, you get asked for a password manually.
    

👀 **Cool for Day 1**, but imagine typing that password over and over every time you screw something up (which you will 💀).

### 😎 Method 2: The Lazy Hacker™ Way — Using `sshpass`


``sshpass -p `cat bandit0` ssh bandit0@bandit.labs.overthewire.org -p 2220``

Let’s break this spicy one-liner down:

- `sshpass`: Like the UberEats of SSH — delivers your password straight to the server.
    
- `` `cat bandit0` ``: Reads the password from a file named `bandit0`. No copy-pasting.
    
- `ssh ...`: Same SSH command from before.
    

🧠 **Why this :**

- 💨 Fast as hell.
    
- 🙈 No typing passwords every time.
    
- 💻 Makes automation/scripts easier if you're running repeat tasks.


### ⚠️ Real-World Warning

> 🔒 Don’t use `sshpass` in real jobs or secure systems. It’s not secure — storing plaintext passwords is a security sin. This is fine in a CTF where nothing matters but speed and style.


Lets apply what we learned 

![](../../../assets/Pasted%20image%2020250726120745.png)

- First, create a directory (folder) to organize your work.  
    👉 Example: `mkdir otw`
    
- Inside that folder, use `ls` to confirm you have the `bandit0 or etc`  file, which contains the password.  
    👉 `ls`
    
- Create a new file using the `nano` text editor and paste the password you got from the first level.  
    👉 `nano bandit1`
    
- Save and exit the file.
    
- Now, whenever you want to log in to the server using `sshpass`, you can do:  
    👉 `sshpass -p $(cat bandit0) ssh bandit0@bandit.labs.overthewire.org -p 2220`
    
- This is a good habit for automating things and avoiding typing the password every time.

![](../../../assets/Pasted%20image%2020250726122111.png)
- ✅ **Command used:** `cat -`
    
    - 🔍 **What it does:** The `-` is a special argument in Unix tools like `cat`, which tells it to read from **standard input (stdin)** instead of a file.
        
    - ⌨️ **What happened:** It waited for you to **type something**, because it thought you were going to enter input manually. That’s why it didn’t show anything and just sat there blinking.
        
    - 😵 **Why it failed:** You wanted to read a file **named `-`**, but `cat -` didn’t know that — it thought `-` meant “give me some input.”
        



- ✅ **Correct command:** `cat ./-`
    
    - 📂 **What it does:** `./-` tells the shell **“a file literally named `-` that is in the current directory.”**
        
    - 📥 **Why it works:** The `./` prefix disambiguates it from the stdin shortcut and treats it as an actual file path.


**Other Ways to read such files** 

1. **Use double dash to stop option parsing:**
        
    `cat -- -`
    
    This tells `cat` to treat `-` as a filename, not as stdin.
    
2. **Use the full or relative path:**
    
    `cat /full/path/to/-`
    
    Replace `/full/path/to/-` with the actual location of the file.
    
3. **Use `find` with `-exec`:**
        
    `find . -name '-' -exec cat {} \;`
    
    This finds the file named `-` in the current directory and reads it.




If you wanna learn more about `sshpass` https://linux.die.net/man/1/sshpass