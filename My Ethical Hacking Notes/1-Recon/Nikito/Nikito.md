# **Nikto — Old but Gold Web Scanner**

Nikto is a **web vulnerability scanner** focusing on outdated software, misconfigurations, insecure headers, and known CVEs.

### **Concept**

Nikto uses a massive **signature database** that checks for:

- Bad configs
    
- Dangerous files
    
- Outdated versions
    
- Default credentials
    

### **Basic Command**

`nikto -h http://<IP>`

### **Tips**

- Nikto is noisy — don’t use it first in real pentests.
    
- But in CTFs? Spam that thing. You might find backup files or exposed configs fast.