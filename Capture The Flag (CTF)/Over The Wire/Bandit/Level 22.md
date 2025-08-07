
![](../../../assets/Pasted%20image%2020250807140427.png)

## 🔍 Challenge Description

> A program is running automatically at regular intervals from `cron`, the time-based job scheduler.  
> Look in `/etc/cron.d/` for the configuration and see what command is being executed.

---

## 🧠 Initial Thought Process

When dealing with cron jobs in CTFs, especially in OverTheWire, the idea is usually to see **what recurring task is being run**, and if you can **predict where the results go**. In this case, we need to observe what the cronjob is doing and figure out a way to grab the password for `bandit23`.

---

## 👣 Step-by-Step Walkthrough

![](../../../assets/Pasted%20image%2020250807142005.png)

### 1. Look for cron jobs

```bash
cd /etc/cron.d/
ls
```

You’ll see a bunch of files, but the one we're interested in is:

```bash
cronjob_bandit23
```

### 2. Read the cron job configuration

```bash
cat cronjob_bandit23
```

You'll see:

```cron
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```

💡 This tells us that **every minute**, a script (`/usr/bin/cronjob_bandit23.sh`) runs as `bandit23`.

---

### 3. Check what the script actually does

```bash
cat /usr/bin/cronjob_bandit23.sh
```

This is the actual script:

```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

### 🔎 What’s happening here?

- The script gets the **username it's running as** (`bandit23`) with `whoami`.
    
- Then it hashes `"I am user bandit23"` with `md5sum` to get a filename.
    
- Finally, it copies the password from `/etc/bandit_pass/bandit23` to `/tmp/<hashed-filename>`.
    

---

### 4. Recreate the filename

Since we can't run the script as `bandit23`, we simulate the hash manually:

```bash
echo "I am user bandit23" | md5sum | cut -d ' ' -f1
```

This gives:

```bash
8ca319486bfbbc3663ea0fbe81326349
```

---

### 5. Get the password!

Now we simply read the file that the cron job keeps updating:

```bash
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```

Output:

```bash
Redacted##################################
```

🎉 That’s your password for **bandit23**!

---

## 💬 Final Thoughts

This level teaches a really cool concept: how cron jobs work and how to reverse-engineer their behavior even if you can't run them directly. Instead of attacking the script, you just figure out **where it's dropping secrets** and read from there.

---

## 📚 Where to Learn More

- 🔗 [OverTheWire: Bandit Wargame](https://overthewire.org/wargames/bandit/)
    
- 📘 [crontab.guru](https://crontab.guru/) – the easiest way to learn cron expressions
    
- 📘 [MD5 Generator (Online)](https://www.md5hashgenerator.com/)
    
- 📘 [Explaining `md5sum`](https://man7.org/linux/man-pages/man1/md5sum.1.html)
    

---

## 🧾 Useful Cheatsheet

```bash
# Calculate md5sum for "I am user bandit23"
echo "I am user bandit23" | md5sum | cut -d ' ' -f1

# Read the resulting file from /tmp
cat /tmp/<md5_hash>
```

---
































