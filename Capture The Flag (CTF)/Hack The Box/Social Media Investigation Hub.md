# **Social Media Investigation Hub (OSINT)**

# **CHALLENGE DESCRIPTION**

You've discovered Alex Morgan is connected to RivalTech and has been conducting fake review campaigns against TechFlow. Now you need to map Alex's complete digital footprint across social media platforms to understand the full scope of this operation and find evidence of coordination with other actors.

- **Difficulty = Very Easy**
- **Category = OSINT**


---

# HTB: Social Media Investigation Hub — Write-Up

## Overview

This challenge is basically a cross-platform OSINT investigation. You’re given a username — **TechReviewer2024** — and you have to correlate data across three fake social networks:

- **ChirpNet** (Twitter-like)
    
- **ConnectPro** (LinkedIn-like)
    
- **ForumHub** (Reddit-like)
    

Your goal is to dig through all three profiles and answer nine questions to unlock the final flag.

---

## Evidence Screenshots


### ChirpNet

![](../../assets/Pasted%20image%2020251125024613.png)

### ConnectPro

![](../../assets/Pasted%20image%2020251125024206.png)

### ForumHub

![](../../assets/Pasted%20image%2020251125024251.png)

---

## Step-By-Step Investigation

### **1. Finding the real name**

Jumping into **ConnectPro**, the profile instantly leaks the person’s real identity:  
→ **Alex Morgan**  
This is typical OSINT: professional networks almost always spill the real-world identity.

---

### **2. Tracking work history**

Scrolling to the experience section on ConnectPro reveals:

- **Marketing Specialist @ RivalTech Inc (2021–2023)**  
    So the previous workplace = **RivalTech Inc**. Easy clap.
    

---

### **3. Operation codename**

Switching to **ForumHub**, one post about “XyloPhone Pro Campaign Coordination” mentions:  
→ **operation_social_storm_2024**  
The challenge wants this exact string.

---

### **4. Coordinated reviewer accounts**

On **ChirpNet**, the list of suspicious accounts all show creation/following dates from:  
→ **February 2024**  
Classic fake-reviews ring behavior — mass account creation around the same time.

---

### **5. Target product**

Back on ForumHub, the negative-review coordination post focuses entirely on:  
→ **XyloPhone Pro**  
No ambiguity here.

---

### **6. Subreddit role**

ForumHub shows the profile is a **moderator** of r/TechReviews.  
This aligns with someone trying to influence product perception.

---

### **7. Educational background**

ConnectPro again:  
→ **University of California, Berkeley — Bachelor of Science in Marketing (2017–2021)**

---

### **8. Number of professional connections**

ConnectPro lists:  
→ **89 connections**  
Small network for a “professional reviewer,” which is kinda sus — fits the storyline.

---

### **9. ForumHub post karma**

ForumHub shows:  
→ **1,247 post karma**  
High karma + low account age = strong signal of boosted visibility.

---

## Notes 

Even though this challenge looked super easy, there were a couple of moments worth noting for the write-up:

### **1. Everything was hidden in plain sight**

Unlike the vehicle challenge earlier (where service dates were messy as hell), this one was straightforward — all info was visible if you dug through the tabs properly.

### **2. Nothing fuzzy, nothing trick-based**

No metadata, no strings, no scraping, no OSINT acrobatics.  
Just simple enumeration + connections.

### **3. Time spent**

Took roughly **10 minutes**, so the challenge truly belongs in the “Very Easy OSINT” category.

---

## Final Thoughts

Even though this was an easy warm-up, it’s a nice reminder of how cross-platform personas can leak a full identity without any hacking involved. Small crumbs across different networks can connect into one big picture.
