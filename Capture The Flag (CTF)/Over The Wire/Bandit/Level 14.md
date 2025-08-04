![](../../../assets/Pasted%20image%2020250804180503.png)

- This Challenge is Very Straight Forward As its mentioned in the Above image, We Need the previous password. If we have that we can just submit that password and get the password for the next level that is all 

![](../../../assets/Pasted%20image%2020250804180746.png)
 
- First we need to get the previous password right. So Go to the directory you saved the passwords and then get the password 
- Second run the commands you see down below.

![](../../../assets/Pasted%20image%2020250804181026.png)
## Command Break Down
### 1. `echo MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

- This simply outputs the password.
    
- The `echo` command sends the string to _standard output_ (the terminal by default).
    

### 2. The `|` (pipe)

- Takes the output from the left side (`echo ...`) and **feeds it as input** to the command on the right (`nc localhost 30000`).
    

### 3. `nc localhost 30000`

- `nc` (short for **netcat**) is like a Swiss Army knife for network connections.
    
- This command opens a **TCP connection to port 30000** on the **localhost** (the same server you're logged into).
    
- It then sends the input it receives (from `echo`) over the network socket.
    

So essentially, you’re **sending your password into a program** running on port `30000`, and that program responds with the password for the next level.

---
## Final Thoughts 

This level introduces a **foundational concept in cybersecurity and networking** — interacting with **network services** over specific **ports** using command-line tools.

---

### 🔍 What We Learned:

- **How to use `nc` (netcat)** to open TCP connections.
    
- How to **send data** over a network socket using simple tools like `echo`.
    
- The idea that **services can run on ports locally**, not just remotely.
    
- That Linux lets you string simple commands together (`echo`, `nc`) to solve real problems.
    

---

### 🧠 Why It Matters:

This challenge is a gentle intro to:

- **Client-server communication**
    
- **Service enumeration** (a key part of reconnaissance in pentesting)
    
- **Command chaining**, which becomes incredibly useful in scripting and exploitation
    

These are the building blocks for more advanced topics like:

- Interacting with vulnerable services
    
- Writing custom clients or exploits
    
- Understanding how backdoors or C2 (Command and Control) systems work
    

---