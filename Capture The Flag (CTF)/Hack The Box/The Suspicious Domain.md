
# **Write-Up: “The Suspicious Domain” — Hack The Box OSINT Challenge**

# **CHALLENGE DESCRIPTION**

Following the discovery of the suspicious social media profile "TechReviewer2024", investigators have uncovered a review manipulation campaign targeting TechFlow. The domain "alexmorgan-reviews.net" appears to be central to this operation. Use DomainScope to investigate this domain and identify the key identifier linking it to the broader campaign infrastructure. :: Challenge Type :: Interactive Q&A Platform (6 questions + 3 correlation questions). :: How to Play :: (1) Click "Start Instance" and wait for the Docker container to spawn | (2) Open the given URL in your browser - this will take you to "DomainScope" | (3) The domain "alexmorgan-reviews.net" will be pre-loaded | (4) Explore the different tabs (WHOIS, DNS Records, Hosting, etc.) to gather intelligence | (5) Go to the "Investigation Challenge" tab (rightmost tab) | (6) Answer 6 questions about the domain | (7) Once you've answered all 6, you'll unlock the "Correlation Challenge" | (8) Finish the 3 extra correlation questions - the final flag will then show up on the page.

---

# Screenshot Sections to see the screens

## WHOIS & Registration Data

![](../../assets/Pasted%20image%2020251126092756.png)

## DNS Records

![](../../assets/Pasted%20image%2020251126092846.png)

## Hosting & Infrastructure Details

![](../../assets/Pasted%20image%2020251126093039.png)

## Historical Data & Timeline

![](../../assets/Pasted%20image%2020251126092936.png)

## Threat Analysis & Intelligence

![](../../assets/Pasted%20image%2020251126093131.png)

## Website Preview & Content Analysis

![](../../assets/Pasted%20image%2020251126093217.png)

## **1. WHOIS Email Address**

**Answer:** `alex.morgan@tempmail.com`

Found directly in the WHOIS record.  
A disposable email tied to a “professional review company” is already enough to raise both eyebrows and maybe a third one.

---

## **2. Complete Phone Number**

**Answer:** `+1-408-555-0987`

Straightforward pull from WHOIS. The number tries very hard to sound Silicon Valley, and honestly, I respect the commitment.

---

## **3. Domain Creation Date**

**Answer:** `2024-01-20`

New domain, recently activated — classic behavior for operations that don’t plan on sticking around long enough to pay rent.

---

## **4. Organization Name (WHOIS)**

**Answer:** `Morgan Tech Reviews LLC`

Looks official enough until you remember the email is from Temp Mail. Nothing screams “trust us” like mixing legal entities with disposable inboxes.

---

## **5. Registrant City**

**Answer:** `San Jose`

San Jose is a popular choice for people trying to look “tech-adjacent.” Not suspicious on its own — the rest of the setup definitely helps.

---

## **6. Domain Transfer Status**

**Answer:** `clientTransferProhibited`

A standard status, but also a convenient way for shady operators to make sure nobody yoinks their domain out from under them. Even cybercriminals like a bit of stability.


---

## **7. What Company Is Being Targeted?**

**Answer:** **TechFlow**

This one had me questioning my life choices for a moment. The site is literally filled with anti-TechFlow reviews, and the analytics tag _also_ contains “TECHFLOW.”  
It’s the OSINT equivalent of tripping over a giant neon sign that says “THIS IS THE TARGET.”

---

## **8. What Email Service Is the Threat Actor Using?**

**Answer:** **Temp Mail**

Here’s where I tried to be smarter than the challenge. I followed the SPF record breadcrumbs like I was on a top-secret mission, when the answer was simply the disposable email service staring me in the face the whole time. Lesson learned: sometimes OSINT isn’t 4D chess — sometimes it’s “look at the email domain, my friend.”

---

## **9. How Many GitHub Pages IPs?**

**Answer:** `4`

All A-records point to GitHub Pages. Cost-effective, quick to set up, and just shady enough for a throwaway review-manipulation campaign.

Finally The FLAG !

![](../../assets/Pasted%20image%2020251126093319.png)
# **Final Thoughts**

Finished all nine questions after a few graceful stumbles. The domain is clearly part of a low-effort, low-budget influence operation aimed at damaging TechFlow — disposable emails, cookie-cutter WHOIS data, GitHub Pages hosting, and identical analytics tags across multiple domains.

In short:  
**It’s giving “scam startup” energy.**

