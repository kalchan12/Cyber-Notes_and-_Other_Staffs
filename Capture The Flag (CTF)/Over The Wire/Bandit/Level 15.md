
![](../../../assets/Pasted%20image%2020250805153333.png)
- Submit the current level’s password to a specific **port (30001)** on **localhost** using a secure (TLS/SSL) connection, and receive the password for the next level in response.
- This is exactly similar to our previous challenge, where have to connect to our localhost using Netcat(nc)and get our pass when we first deliver our existing pass.

![](../../../assets/Pasted%20image%2020250805153438.png)
- Once logged in we will connect to the our localhost via SSL/TLS using the above Command 

## Command Break Down

``openssl s_client -connect localhost:30001``

### 🔹 `openssl`

- This is the **OpenSSL command-line tool**.
    
- It provides a wide range of cryptographic functions including:
    
    - Generating keys and certificates
        
    - Encrypting/decrypting data
        
    - Testing secure connections
        

---

### 🔹 `s_client`

- A **subcommand** of `openssl`.
    
- Stands for **“SSL/TLS client”**.
    
- It lets you **manually initiate a secure connection** to a server that supports SSL/TLS.
    
- Think of it like a browser or HTTPS client — but in your terminal and much more raw.
    
- Used mostly for testing or debugging TLS/SSL services.
    

---

### 🔹 `-connect localhost:31790`

This tells `s_client` **where to connect**.

Let’s break it further:

#### 🔸 `-connect`

- An **option** that specifies the address and port of the server to connect to.
    
- Format: `host:port`
    

#### 🔸 `localhost`

- The **host name** — refers to your own machine (the one you're SSH’ed into).
    
- It means you're trying to connect to a **local service** running on the same server.
    

#### 🔸 `30001`

- The **TCP port** number the service is listening on.
    
- This must match the port where the challenge or service is expecting your connection.

---

### ✅ Summary :

> “Run OpenSSL as an SSL/TLS client, and connect securely to a service running on **localhost** at port **30001**.”

Once connected, you’ll get a raw SSL session where you can manually **send data (like a password)** and receive the response.

---

![](../../../assets/Pasted%20image%2020250805153528.png)

- As you can see from the terminal When you enter the current password, it will say Correct and give you the password for the next 

- Another Quick way would we tho using the command down below 
  
  ![](../../../assets/Pasted%20image%2020250805155449.png)
- This is quick and dirty way to connect using SSL/TLS.

Explanation:

- `echo` sends the password.
    
- The `|` (pipe) passes that password to the input of the next command.
    
- `openssl s_client -connect localhost:31790`: opens the TLS connection.
    
- `-quiet`: suppresses all SSL negotiation output, only shows raw response from the server.

### 🏁 Final Thought 

This challenge is a great introduction to **secure client-server communication using TLS/SSL**. You learned how to use `openssl s_client` to manually connect to a secure service and send data (your password) over an encrypted channel. This mimics how browsers or secure applications communicate with servers — but here, you did it manually, which helps demystify what happens behind the scenes. It’s a practical lesson in encryption, networking, and how simple command-line tools can interact with secure services.

### Resource 
### 🔐 **TLS/SSL Basics**

1. **SSL vs TLS: What’s the Difference? (Cloudflare)**
    
    - 📎 https://www.cloudflare.com/learning/ssl/what-is-ssl/
        
    - A visual and beginner-friendly overview.
        
2. **How HTTPS Works (Animated)**
    
    - 📎 https://howhttps.works/
        
    - A beautiful interactive guide to how HTTPS/TLS works.
        
3. **MDN Web Docs - HTTPS (TLS)**
    
    - 📎 https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview
        
    - Covers HTTP and secure communication, TLS/SSL layers, etc.
        

---

### 🔧 **OpenSSL and s_client**

4. **OpenSSL `s_client` Documentation**
    
    - 📎 https://www.openssl.org/docs/man1.1.1/man1/openssl-s_client.html
        
    - Official man page — useful as a reference.
        
5. **How to Use OpenSSL s_client to Test SSL Connections**
    
    - 📎 https://www.baeldung.com/linux/openssl-s-client
        
    - Step-by-step examples, great for beginners.
        
6. **OpenSSL Essentials: Working with SSL Certificates, Private Keys and CSRs**
    
    - 📎 https://www.digitalocean.com/community/tutorials/openssl-essentials-working-with-ssl-certificates-private-keys-and-csrs
        
    - Broader OpenSSL usage: key generation, certs, etc.
        

---

### 🎥 **Video Tutorials**

7. **Computerphile – How HTTPS Works**
    
    - 📎 [https://www.youtube.com/watch?v=5Uu3kCEEc98](https://www.youtube.com/watch?v=5Uu3kCEEc98)
        
    - Clear, simple explanation of the TLS handshake and encryption.
        
8. **NetworkChuck – OpenSSL Crash Course**
    
    - 📎 [https://www.youtube.com/watch?v=vz9Xxj1T8-E](https://www.youtube.com/watch?v=vz9Xxj1T8-E)
        
    - Hands-on OpenSSL use cases.
        

---