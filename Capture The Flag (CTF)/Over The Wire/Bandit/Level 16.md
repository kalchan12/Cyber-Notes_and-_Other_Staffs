
![](../../../assets/Pasted%20image%2020250805162815.png)

- The task is to identify which port (between **31000 and 32000**) is running a **TLS/SSL-enabled** service that expects a password input, using various scanning techniques.


## 1️⃣ Method 1: **Fast Nmap Scan for Open Ports**

![](../../../assets/Pasted%20image%2020250805161840.png)
### ✅ Command:

`nmap -p 30000-40000 -T5 --min-rate=1000 --open localhost`

### 📖 What it does:

- Scans ports from **30000 to 40000**
    
- `-T5`: Aggressive speed (fastest timing)
    
- `--min-rate=1000`: Sends at least 1000 probes/sec
    
- `--open`: Only show ports that are open (ignore closed/filtered)
    
- `localhost`: Scan the local machine
    

### 🧾 Result:

- Returned **4 open ports**
    
- These are **candidates**, but we don't yet know if they use TLS.
---


## 2️⃣ Method 2: **Nmap Script Scan for TLS/SSL Services**

![](../../../assets/Pasted%20image%2020250805162229.png)
### ✅ Command:

`nmap -p 30000-40000 --open --script ssl-cert,ssl-enum-ciphers localhost`

### 📖 What it does:

- Scans same port range
    
- Uses Nmap **NSE scripts** to check for TLS services:
    
    - `ssl-cert`: Gets SSL certificate info
        
    - `ssl-enum-ciphers`: Lists supported encryption ciphers
        
- Helps identify which open ports are actually **TLS-enabled**
    

### 🧾 Result:

- Narrowed the results to **2 ports** with TLS-based services
    
- This is more specific than Method 1
- As you can see down below we got ports that uses SSL Services
## The First Open port (31518)

- This port Returns the password the exact password which only means it is a decoy 

![](../../../assets/Pasted%20image%2020250805162308.png)

- Using the previous command i submitted the current password and That Returned The same Password which is weird

![](../../../assets/Pasted%20image%2020250805165313.png)
## The Second Open port (31790)

- I used the same command to connect to this specific port but this one returned an RSA private key instead. This means we can authenticate with this private key instead of using a password.

![](../../../assets/Pasted%20image%2020250805162343.png)


![](../../../assets/Pasted%20image%2020250805165931.png)

- **Out of the identified ports this one is the correct one and the RSA is used as authentication via ssh. You should save the file as bandit17.key and give it a permission `chmod 600`** 
- for the next level you should just use this command below or use it alongside sshpass

`ssh -i **bandit17.key** bandit17@bandit.labs.overthewire.org -p 2220`
## 3️⃣ Method 3: **Bash Script with OpenSSL**

### ✅ Script:


`for port in {30000..40000}; do   echo | timeout 1 openssl s_client -connect localhost:$port -quiet 2>/dev/null && echo " Port $port works" done`

### 📖 What it does:

- Iterates over ports from **30000 to 40000**
    
- For each port:
    
    - Uses `openssl s_client` to try opening a **TLS connection**
        
    - Pipes an empty line (`echo`) to simulate sending input
        
    - `timeout 1`: Waits only 1 second per port to avoid hanging
        
    - `-quiet`: Suppresses SSL handshake details (clean output)
        
    - `2>/dev/null`: Suppresses error output
        
- If a port responds, it prints:
     
    `Port <port_number> works`

### 🧾 Result:

- Identified **1 single working TLS port**
    
- This is likely the correct one right? Well it is not because this port is a dummy service but the script was helpful for automation even tho it was not as good as nmap.

### 🏁 Final Thought 

This challenge was a great blend of **network enumeration**, **TLS communication**, and **SSH authentication**. You learned how to:

- **Scan ports efficiently** using tools like `nmap` and `openssl`
    
- Identify **TLS-enabled services**
    
- Extract and correctly use an **RSA private key**
    
- Log in securely using SSH with a private key instead of a password
    

It reflects a realistic scenario where an attacker or pentester must **enumerate services**, recognize **encrypted protocols**, and then leverage **key-based access** — a common method in secure systems.

By solving this, you now understand:

- How to talk to encrypted services manually
    
- How to recognize misleading ports
    
- How to perform proper key handling and authentication

