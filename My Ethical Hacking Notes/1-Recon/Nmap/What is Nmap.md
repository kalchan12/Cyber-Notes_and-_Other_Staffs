# **1. Nmap — The King of Recon**

Nmap is your eyes on the network. It's the tool that tells you:

- Which ports are open
    
- Which services are running
    
- What versions they use
    
- OS detection clues
    
- Possible attack paths
    

### **Concept**

Nmap uses **TCP/IP behavior** to probe targets. Different scans manipulate flags (SYN, FIN, ACK) predicting how the host responds.

### **Most Common Commands**

**Basic scan**
`nmap <IP>1`
**Service + version detection**
`nmap -sV <IP>`
**Default scripts + version detection**
`nmap -sC -sV <IP>`
**Aggressive scan (noisy)**
`nmap -A <IP>`
**Scan all ports**
`nmap -p- <IP>`
**Fast scan**
`nmap -T4 <IP>`
### **Tips**

- Always start with `-sC -sV`.
    
- If you see HTTP => switch to web recon ASAP.
    
- Scan _all_ ports early; many CTF flags hide in weird ports like 8081, 5000, 6666.