# **WhatWeb — Quick Web Fingerprinting**

WhatWeb is like the “What’s this website made of?” tool.

It fingerprints:

- Frameworks
    
- Plugins
    
- Web technologies
    
- Servers
    
- CMS info
    
- Versions
    

### **Concept**

It scans page responses, cookies, headers, and patterns to identify tech stacks.

### **Commands**

`whatweb http://<IP> whatweb -v http://<IP> whatweb -a 3 http://<IP>`

### **Tips**

- Run WhatWeb before Nikto.
    
- Helps you guess attack paths:  
    Example: If it shows “PHP 5.x”, you know old PoCs might land.