![](../../assets/Pasted%20image%2020251210172103.png)

# **CTF Write‑Up — W1seGuy (TryHackMe)**

## **Challenge Goal**

Break a repeating‑key XOR encryption by leveraging **known plaintext attacks**.

`The source Code`

```

import random
import socketserver 
import socket, os
import string

flag = open('flag.txt','r').read().strip()

def send_message(server, message):
    enc = message.encode()
    server.send(enc)

def setup(server, key):
    flag = 'THM{thisisafakeflag}' 
    xored = ""

    for i in range(0,len(flag)):
        xored += chr(ord(flag[i]) ^ ord(key[i%len(key)]))

    hex_encoded = xored.encode().hex()
    return hex_encoded

def start(server):
    res = ''.join(random.choices(string.ascii_letters + string.digits, k=5))
    key = str(res)
    hex_encoded = setup(server, key)
    send_message(server, "This XOR encoded text has flag 1: " + hex_encoded + "\n")
    
    send_message(server,"What is the encryption key? ")
    key_answer = server.recv(4096).decode().strip()

    try:
        if key_answer == key:
            send_message(server, "Congrats! That is the correct key! Here is flag 2: " + flag + "\n")
            server.close()
        else:
            send_message(server, 'Close but no cigar' + "\n")
            server.close()
    except:
        send_message(server, "Something went wrong. Please try again. :)\n")
        server.close()

class RequestHandler(socketserver.BaseRequestHandler):
    def handle(self):
        start(self.request)

if __name__ == '__main__':
    socketserver.ThreadingTCPServer.allow_reuse_address = True
    server = socketserver.ThreadingTCPServer(('0.0.0.0', 1337), RequestHandler)
    server.serve_forever()
```

What this code does is 

- The server generates a random 5‑character key.
    
- It XOR‑encrypts a predictable plaintext (`THM{…}`), which leaks parts of the key.
    
- The encrypted text is sent to the player.
    
- Because XOR is reversible and plaintext is partially known, we can mathematically derive the key.
    
- Once the correct key is submitted, the server reveals the real flag

---

## Step 1 Connect & Grab the Hex Blob

Command:

```
nc 10.64.184.24 1337
```

You see something like:

![](../../assets/Pasted%20image%2020251210172725.png)


---

## Step 2  Run the XOR Key Recovery Script

- Derive first 4 bytes of key from `"THM{"`
    
- Derive last byte of key from `"}"`
    
- Reconstruct full 5‑byte key
    
- Decrypt full message

```
import random
import socketserver 
import socket, os
import string

flag = open('flag.txt','r').read().strip()

def send_message(server, message):
    enc = message.encode()
    server.send(enc)

def setup(server, key):
    flag = 'THM{thisisafakeflag}' 
    xored = ""

    for i in range(0,len(flag)):
        xored += chr(ord(flag[i]) ^ ord(key[i%len(key)]))

    hex_encoded = xored.encode().hex()
    return hex_encoded

def start(server):
    res = ''.join(random.choices(string.ascii_letters + string.digits, k=5))
    key = str(res)
    hex_encoded = setup(server, key)
    send_message(server, "This XOR encoded text has flag 1: " + hex_encoded + "\n")
    
    send_message(server,"What is the encryption key? ")
    key_answer = server.recv(4096).decode().strip()

    try:
        if key_answer == key:
            send_message(server, "Congrats! That is the correct key! Here is flag 2: " + flag + "\n")
            server.close()
        else:
            send_message(server, 'Close but no cigar' + "\n")
            server.close()
    except:
        send_message(server, "Something went wrong. Please try again. :)\n")
        server.close()

class RequestHandler(socketserver.BaseRequestHandler):
    def handle(self):
        start(self.request)

if __name__ == '__main__':
    socketserver.ThreadingTCPServer.allow_reuse_address = True
    server = socketserver.ThreadingTCPServer(('0.0.0.0', 1337), RequestHandler)
    server.serve_forever()
```

I saved this as solver.py so that i can run it alongside the hex(flag1) i found. this will give the first flag 

Command:

![](../../assets/Pasted%20image%2020251210173154.png)

---

## Step 3 Enter the Real Key Into the Server

Now reconnect:

Paste the key you received first and you will get the second flag 
 
---

### **Final Thoughts**

This challenge was basically a reminder that XOR is only as strong as its key and plaintext. Since the flag format is predictable (`THM{}`), the server leaked enough info to rebuild the 5‑byte key using a simple known‑plaintext attack. Once the key was recovered, the rest fell apart instantly. Solid warm‑up crypto, nothing wild — just classic XOR getting bodied by predictable plaintext