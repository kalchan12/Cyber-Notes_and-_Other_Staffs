![](../../../assets/Pasted%20image%2020250731122709.png)

- In this level we don't get the password to the level 14 instead we get sshkey so that we would log into bandit14 using the ` private ssh key ` 

![](../../../assets/Pasted%20image%2020250731122953.png)


## 🧨 Command Breakdown:

```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

### 🔍 Piece by Piece:

| Part                 | Meaning                                                                                       |
| -------------------- | --------------------------------------------------------------------------------------------- |
| `ssh`                | Start an SSH (Secure Shell) connection  used to remotely access another machine               |
| `-i sshkey.private`  | Specifies the **identity file** (a.k.a your **private SSH key**) to use instead of a password |
| `bandit14@localhost` | Login as user `bandit14` on the **local machine** (`localhost` = same server you’re on)       |
| `-p 2220`            | Use **port 2220** (the Bandit server doesn’t use the default SSH port 22)                     |

![](../../../assets/Pasted%20image%2020250731123635.png)

- If we logged in correctly we will see the user is changed into `bandit 14`
- the after that as it is mentioned in the Over The Site, the password is for the next challenge is Stored in the **` /etc/bandit_pass/bandit14 and can only be read by user bandit14`** directory 
- Finally we will just cat the password by using the cat command **` cat  /etc/bandit_pass/bandit14 and can only be read by user bandit14`**

---

## 🧠 Final Thoughts

This challenge was less about brute-forcing commands and more about understanding **SSH authentication**  specifically, how private keys work in place of passwords.

Instead of giving us the password like in previous levels, the game gave us a **private SSH key** to access the next user account. This mimics a real-world situation where SSH keys are commonly used for secure, passwordless login  especially in DevOps, cloud, or cybersecurity workflows.

It also introduced us to:

- **SSH options** like `-i` (identity file) and `-p` (custom port)
    
- The idea of **privilege separation** (only bandit14 can read their own password file)
    
- Logging into the **same machine** (`localhost`) as a different user
    

> We didn't grab the password  we **earned** access to it through secure authentication. 🔐💻

---


