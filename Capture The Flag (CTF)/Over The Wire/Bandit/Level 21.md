
![](../../../assets/Pasted%20image%2020250807133634.png)


## Challenge Description

> A program is running automatically at regular intervals from `cron`, the time-based job scheduler.  
> Look in `/etc/cron.d/` for the configuration and see what command is being executed.

We need to:

- Investigate the cron job
    
- Understand what it's doing
    
- Extract the password for the next level from it
    

---


## 🗂️ Walkthrough

![](../../../assets/Pasted%20image%2020250807133715.png)

- `ls -l /etc/cron.d/` this will the list the cron jobs and solving for the `bandit22` so our focus is in the `cronjob_bandit22`
### 1. 🔍 Locate the Cron Job

![](../../../assets/Pasted%20image%2020250807134038.png)

`cat /etc/cron.d/cronjob_bandit22`

Output:

`@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null * * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`

This tells us:

- A script is run as user `bandit22`
    
- It runs every minute
    
- The script is located at `/usr/bin/cronjob_bandit22.sh`
    

---

### 2. 📜 Inspect the Script


`cat /usr/bin/cronjob_bandit22.sh`

Output:

`#!/bin/bash chmod 644 /tmp/t706lds9S0RqQh9aMcz6ShpAoZKF7fgv cat /etc/bandit_pass/bandit22 > /tmp/t706lds9S0RqQh9aMcz6ShpAoZKF7fgv`

🔍 What's happening:

- The script changes permissions so anyone can read `/tmp/t706lds9...`
    
- It writes the password for **bandit22** into that file
    

---

### 3. 🔓 Read the Leaked Password

`cat /tmp/t706lds9S0RqQh9aMcz6ShpAoZKF7fgv`

This is the password for **bandit22**.

---


## 🧠 Final Thoughts

This level teaches how insecure scripts running as cron jobs can leak sensitive data — especially when:

- They write to world-readable files (`/tmp`)
    
- They don't restrict file permissions properly
    

This is a **real-world security issue** commonly seen in poorly configured servers.

---

### 📚 Learn More About `cron` and `crontab`:

1. **Crontab Guru (Quick crontab syntax help)**  
    🔗 https://crontab.guru
    
2. **Linuxize: How to Use Cron to Schedule Jobs**  
    🔗 https://linuxize.com/post/scheduling-cron-jobs-with-crontab/
    
3. **man 5 crontab (online version)**  
    🔗 https://man7.org/linux/man-pages/man5/crontab.5.html
    

---







