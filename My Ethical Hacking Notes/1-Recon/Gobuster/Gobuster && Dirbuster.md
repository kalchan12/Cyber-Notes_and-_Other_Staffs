# **Gobuster / Dirbuster — Directory & File Bruteforcing**

These tools discover **hidden files and directories** on web servers.

### **Concept**

They send thousands of requests using a wordlist to find:

- `/admin`
    
- `/uploads`
    
- `/backup.zip`
    
- `/login`
    
- `/hidden`
    

Basically, the stuff devs tried to hide.

### **Gobuster Example**

`gobuster dir -u http://<IP> -w /usr/share/wordlists/dirb/common.txt`

### **Tips**

- If there’s a web server, ALWAYS run a directory scan.
    
- Use `-x` when expecting file extensions:
    

`-x php,txt,html`

- For CTFs, try bigger wordlists like `big.txt` or `directory-list-2.3-medium.txt`.