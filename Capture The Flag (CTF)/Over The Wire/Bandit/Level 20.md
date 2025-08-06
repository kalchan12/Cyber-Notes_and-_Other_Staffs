
![](../../../assets/Pasted%20image%2020250806113259.png)


## Challenge Description

> You are given a **setuid binary** called `suconnect`.  
> It connects to `localhost` on a port you specify, reads a single line of input, and checks if that input matches the password for the **current level (bandit20)**.  
> If it matches, the program will print the password for the **next level (bandit21)**.

---

## What’s Going On?

To solve this, we need to simulate a **server** that the `suconnect` binary can talk to.

- The binary expects a **port number** as an argument
    
- It connects to `localhost:<port>`
    
- It waits for input — the input must be **bandit20’s password**
    
- If the password is correct, it prints the password for bandit21
    

This is a simulated **authentication handshake** between a client and server.

---

## 🛠️ Tools Used

I used **`tmux`** to open two panes (virtual terminals) in the same SSH session — making it super easy to run a server and client at the same time.

If you don’t know `tmux`, you should definitely learn it. It lets you:

- Split terminals
    
- Run background tasks
    
- Resume sessions later
    

---

##  Step-by-Step Solution

![](../../../assets/Pasted%20image%2020250806112304.png)


### 🖥️ Pane 1 – Start the Server (using Netcat)

```bash
echo 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO | nc -l -p 4444
```

- `nc` netcat
- `-l` listens for communication 
- This sets up a **server** on port  ` -p 4444`
    
- When `suconnect` connects, it will send the correct password
    

---

### 🖥️ Pane 2 – Run the suconnect binary

```bash
./suconnect 4444
```

✅ Output:

```
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoUMcra2q0dSkYj561DX7s1CpBuOBt
```

🎉 The password for **bandit21** is:

```
EeoUMcra2q0dSkYj561DX7s1CpBuOBt
```

---

## 🧠 Final Thought

This challenge is a great exercise in:

- Working with network sockets using `nc` (Netcat)
    
- Understanding how **authentication over a network** might work
    
- Practicing **parallel execution** using `tmux`
    

---

## 📚 Learn `tmux` (Highly Recommended)

-  Try it online:  
    📎 [https://tmuxcheatsheet.com/try/](https://tmuxcheatsheet.com/try/)
    
-  Beginner Tutorial:  
    📎 [https://linuxize.com/post/getting-started-with-tmux/](https://linuxize.com/post/getting-started-with-tmux/)
    
- 📎 Official Docs:  
    [https://github.com/tmux/tmux/wiki](https://github.com/tmux/tmux/wiki)
    

---

## 📄 Tmux Cheat Sheet

|Keybinding|Description|
|---|---|
|`tmux`|Start a new session|
|`tmux a`|Reattach to last session|
|`Ctrl+b %`|Split vertically|
|`Ctrl+b "`|Split horizontally|
|`Ctrl+b arrow`|Navigate panes|
|`Ctrl+b d`|Detach from session|
|`tmux kill-session`|Kill session|

📝 Tip: Use `tmux new -s bandit` to name your session.

---

## 📄 General Cheat Sheet for any tech related topics

- **Visit this website more cheat sheets** https://cheatography.com/

