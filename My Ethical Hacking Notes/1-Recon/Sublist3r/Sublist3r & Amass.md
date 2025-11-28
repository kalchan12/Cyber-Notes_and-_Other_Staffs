# **Sublist3r / Amass — Subdomain Enumeration**

These tools are for **finding subdomains**, which often hide admin panels or weird test apps.

### **Concept**

They collect DNS data from:

- Certificate transparency logs
    
- Search engines
    
- DNS records
    
- Enumerations
    
- Passive sources (OSINT)
    

### **Sublist3r**

`sublist3r -d target.com`

### **Amass (Passive Mode)**

`amass enum -passive -d target.com`

### **Tips**

- If a main domain seems boring, subdomains often aren’t.
    
- Combine with `httpx` after enumeration to see which ones are alive.