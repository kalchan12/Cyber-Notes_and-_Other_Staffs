![](../../../assets/Pasted%20image%2020250806101404.png)
## Challenge Description:

> The password for the next level is stored in a file called `readme` in the home directory.  
> However, `.bashrc` has been modified to **automatically log you out** as soon as you log in via SSH.

---

## Goal:

> Get the contents of the `readme` file **before** the system logs you out.


![](../../../assets/Pasted%20image%2020250806101653.png)

- When i try to log into via ssh this is what i get. The configured .bashrc file logs me out. That is why i am getting Byebye !



## Solution: Command Injection in SSH

Instead of trying to fix `.bashrc`, I passed a command **inline** when connecting via SSH:
![](../../../assets/Pasted%20image%2020250806101734.png)
### Command:

`ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme`

### Explanation:

- `ssh user@host -p port <command>` lets you execute a command **immediately** after login, **before `.bashrc` runs**.
    
- Since `cat readme` is run before the shell is fully initialized, the auto-logout never gets a chance to trigger.
    

 Output: The password for Level 19 is printed directly in the terminal.


### Final Thought 
This challenge highlights a critical concept in Linux: **not all access needs a full interactive shell**. By modifying `.bashrc`, the system was set up to **instantly terminate interactive sessions**, but you cleverly bypassed that by using non-interactive command execution (`ssh user@host command`) — a real-world tactic used in scripting, automation, and even exploit development. It reinforces the idea that **understanding how the shell works under the hood can help you bypass obstacles, not just overcome them.**

---

## What is `.bashrc`?

`.bashrc` is a **shell initialization file** that runs **automatically** every time a user starts a new **interactive, non-login** shell session (like when opening a terminal or SSHing in). It’s used to set up your shell environment — aliases, environment variables, PATH modifications, functions, etc. However, if malicious or buggy commands are added to it (like `exit`), it can **break or hijack** the shell experience, as seen in this challenge.

---

##  Learn More About `.bashrc`

Here are a few solid resources to understand `.bashrc` better:

1. **GNU Bash Reference Manual – Bash Startup Files**  
    📎 https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html  
    _(Official but technical — great for deep diving)_
    
2. **How-To Geek – What is the .bashrc File?**  
    📎 https://www.howtogeek.com/450883/what-is-the-bashrc-file-in-linux-and-mac/  
    _(Beginner-friendly explanation of `.bashrc` and how it differs from `.bash_profile`)_
    
3. **DigitalOcean – Understanding Bash Startup Files**  
    📎 https://www.digitalocean.com/community/tutorials/bashrc-vs-bash-profile  
    _(Very clear and practical for day-to-day use)_