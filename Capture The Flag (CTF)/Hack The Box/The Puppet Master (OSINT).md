

---
# The Puppet Master (OSINT)

# CHALLENGE DESCRIPTION

An anonymous source has shared a photograph of an unidentified military armored vehicle during field operations. Your mission is to conduct a comprehensive OSINT analysis to identify this vehicle and its specifications.

**Difficulty = Easy**
**Category = OSINT**


# **Let the investigation Begin** 

We will see something like this when we visit the website 

![](assets/Pasted%20image%2020251124212549.png)


Please do Read everything here because it will make your life easier i will explain why i said this later

Next screen is the evidence we have to answer the questions 

![](assets/Pasted%20image%2020251124212821.png)

We suppose to get information about this vehicle there are many ways to reverse image searching but i used **yandex** and there others like **google lens , bing etc ** 

Next page is where we answer all the question and get the flag at the end 

# 1. Vehicle Identification


![](assets/Pasted%20image%2020251124213216.png)

here i used yandex to reverse search the image and there are many ways you can even paste in chatgpt or other AI

As you can see in the image there are many many sources like youtube and other articles to get more info.

The answer is below 

![](assets/Pasted%20image%2020251124213454.png)


## Evidence Collection

I even ran `Exiftool` to check for metadata 
![](assets/Pasted%20image%2020251124214130.png)

- **Source:** Screenshot of a military vehicle, filename: `20230525_NZDF_P1061532_025__FocusFillWyIwLjAwIiwiMC4wMCIsNjAwLDQwMF0.jpeg`
    
- **EXIF Analysis:**
    
    ```text
    File Type: JPEG
    Image Size: 600x400
    Comment: CREATOR: gd-jpeg v1.0 (using IJG JPEG v62)
    ```
    
- **Metadata Notes:**
    
    - No GPS/location data available.
        
    - Image resolution small — 600x400 pixels.
        
    - Filename suggests NZDF (New Zealand Defence Force), but this may be **a red herring**.
        

---

# 2. Manufacturer Identification


We need to find who (Company) and where (Country) it was manufactured 
Simple google search would answer this ( Since we know the vehicle we look for is Bushmaster)

![](assets/Pasted%20image%2020251124214931.png)

There is our answer 

![](assets/Pasted%20image%2020251124214322.png)
  

---

# 3. Service History

This one is the most confusing part of this Challenge. There are many variant of this vehicle and even tho it was originally manufactured in **Thales , Australia**.The image that was shown as evidence points to the **New Zealand** variant from the image name `20230525_NZDF_P1061532_025__FocusFillWyIwLjAwIiwiMC4wMCIsNjAwLDQwMF0.jpeg`. 

I have Searched many potential date for **Bushmaster** first Service in **New Zealand**. Many articles point to many dates that is why i said read everything the first screen. 

Truth to be told i have entered manually the year from 2000 up to 2025 ( Which only means i was being a fool) but later it hit me that i was barking in the wrong tree 

then i have started looking at the Australian side of things. I have already time traveled through 2000 - 2025. i looked something in the 19s, i found some sources in 1995 but that not and later i found out the vehicle was **signed in 1997** and that was the answer which makes no sense because the vehicle signed during that time not the **service date**



![](assets/Pasted%20image%2020251124215340.png)

- **Initial Confusion / Mistakes:**
    
    - We first tried **New Zealand DF delivery dates** (2017, 2023) since the filename suggested NZDF — none worked.
        
    - Next, we tried **Australian Army operational deployment dates**. Conflicting sources caused confusion:
        
        - Some sources listed **1995**, the first prototype/operational fielding for East Timor deployment planning.
            
        - Some sources suggested **1997**, referring to the **contract signing and design rework**.
            
        - NZ and other variants were considered but were **irrelevant for the HTB challenge**.
            
- **HTB Accepted Answer:**
    
    - **1997** — this corresponds to the **first contract / prototype design milestone**, not actual deployment.
        
    - Note: The challenge does **not require the first combat use or first delivery**, just a verifiable milestone in service lifecycle.
        
- **OSINT Sources:**
    
    - ANAO Bushranger / Bushmaster report (1997 contract) ([ANAO.gov.au](https://www.anao.gov.au/))
        
    - Thales Australia project pages ([thalesgroup.com](https://www.thalesgroup.com/))
        
    - Historical summaries / War Memorial documents ([awm.gov.au](https://www.awm.gov.au/))
        

---
# 4.Country of Origin
We already know that from our first Answer.
The all mighty Australia innit!

![](assets/Pasted%20image%2020251124221306.png)
## 5. Passenger & Crew Capacity

There are many variants here so try finding the one presented in the image 

![](assets/Pasted%20image%2020251124221507.png)


- **Initial Guesses & Errors:**
    
    - First tried `10 passengers and 2 crew` — too high.
        
    - Then tried `9 passengers and 1 driver` — incorrect.
        
    - `7 passengers and 2 crew` — also rejected.
        
    - Confusion caused by multiple variant specifications:
        
        - Prototype vs. NZDF variants vs. Australian standard.
            
        - Differences between troop carrier, command, ambulance, and other variants.
            
- **Accepted / Correct Answer:**
    
    - HTB’s expected answer format: **`12 passengers and 1 driver`**
        
    - Likely refers to **maximum troop transport configuration**, not standard Australian Army loadout.
    
---

## 6. References / OSINT Chain

- Thales Australia – Bushmaster PMV: [https://www.thalesgroup.com/en/land/bushmaster](https://www.thalesgroup.com/en/land/bushmaster)
    
- Australian Army Fact Sheet – Bushmaster: [https://www.army.gov.au/equipment/vehicles-and-surveillance/bushmaster](https://www.army.gov.au/equipment/vehicles-and-surveillance/bushmaster)
    
- ANAO Report (1997 Contract Milestone): [https://www.anao.gov.au](https://www.anao.gov.au/)
    
- Australian War Memorial – Bushmaster B3 prototype: [https://www.awm.gov.au/collection/C1010561](https://www.awm.gov.au/collection/C1010561)
    
- Defence Major Projects Report – NZ & Australia: [https://www.defence.gov.au](https://www.defence.gov.au/)
    

---


> Lessons: HTB challenges often expect **documented milestone years**, not field deployment; and **vehicle capacity answers must match exact format** requested.

---

