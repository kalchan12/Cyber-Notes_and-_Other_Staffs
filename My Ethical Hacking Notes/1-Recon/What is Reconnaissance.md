
# **What is Reconnaissance**

Recon is basically the “stalking” phase of hacking — but in a professional, legal way.  
It’s about **learning everything about your target before firing a single exploit**. 

Think of recon as:

- **Mapping the attack surface**
    
- Figuring out **what the system exposes**
    
- Spotting **weak points early**
    
- Collecting data to use later during exploitation
    
- Understanding **how the target behaves** on the network
    

Good recon = less guessing, more targeted attacks.

There are two types:

---

## **Passive Recon**

You don’t touch the target directly. You gather info from public sources:

- Search engines
    
- Public DNS data
    
- OSINT
    
- Subdomain enumeration
    
- Metadata scraping
    

It’s low-noise — nobody notices you.

---

## **Active Recon**

You directly interact with the target:

- Port scanning
    
- Service enumeration
    
- Directory fuzzing
    
- Banner grabbing
    
- Web scanner usage
    

It’s more aggressive and might show up in logs.

---

## ** Recon Mindset**

Before touching tools, the mindset matters:

- Don’t brute-force blindly — **collect, correlate, then strike**
    
- You’re building a **map** of the system
    
- Every weird detail could be the key to the whole challenge
    
- Always ask:  
    **“If this port/service exists, what does that imply?”**