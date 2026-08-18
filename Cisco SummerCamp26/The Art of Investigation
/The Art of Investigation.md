## Part 1 — Investigation Foundations

### 1. The Importance of Investigation

Investigation is one of the primary responsibilities of a **Cyber Defense Analyst** and an important part of an organization's overall security operations. When a security incident occurs, an organization cannot simply start fixing systems immediately; it must first understand **what actually happened**.

A typical investigation needs to answer questions such as:

- Did a security incident actually occur?
- What happened?
- When did it happen?
- Which systems or assets were affected?
- How far did the attacker get?
- What actions did the attacker perform?
- Is the attacker still inside the environment?
- What should the organization do next?

The general idea:

> **Detect → Investigate → Understand → Respond → Recover**

Without a proper investigation, an organization might:

- Treat a harmless event as an attack
- Miss a real attack
- Contain the wrong system
- Delete important evidence
- Fail to identify compromised systems
- Allow an attacker to remain in the environment
- Repeat the same security mistake in the future

Investigation therefore provides the information needed to make good security decisions.

### 2. Recovering from a Security Incident or Breach

Every organization can have its own **Incident Response Plan** depending on its infrastructure, business requirements, security policies, and resources. However, many incident response frameworks follow similar ideas. Two commonly referenced frameworks are:

- **SANS 6-step Incident Response Process**
- **NIST 4-phase Incident Response Framework**

Although these frameworks organize the process differently, they contain many of the same fundamental activities. The SANS-style process consists of six major steps:

1. Preparation
2. Identification
3. Containment
4. Eradication
5. Recovery
6. Lessons Learned

#### 2.1 Preparation

**Preparation** happens before a security incident occurs. The goal is to make sure the organization is ready to respond when something goes wrong. Preparation can include:

- Creating an **Incident Response Plan**
- Defining the roles and responsibilities of security personnel
- Establishing communication channels
- Preparing security tools
- Making sure logs are available
- Establishing procedures for collecting evidence
- Training security teams
- Preparing backups and recovery procedures
- Testing incident response procedures

**Why it matters:** during a serious attack there may be a lot of pressure and confusion. If the organization has already decided "if this happens, this person does this, that person does that, and we communicate through this channel", the team can respond much faster. Without preparation, security teams may waste valuable time deciding what to do while the attacker is still active.

**Example:** a company discovers its database server has been compromised. With a prepared plan it may already know who investigates the incident, who isolates the server, who contacts management, who handles legal requirements, who communicates with affected users, and where investigation records should be stored. That preparation can significantly reduce the impact of the incident.

#### 2.2 Identification

**Identification** is the process of determining whether a suspicious event is actually a security incident and understanding its scope. This is where **investigation and triage** become especially important: security teams receive many alerts, but not every alert represents a real attack. The analyst needs to investigate the available evidence and determine what is actually happening.

**Triage** is the process of analyzing findings and deciding what should happen to them. An analyst may determine that a finding is:

- Harmless activity
- A false positive
- Suspicious activity requiring additional investigation
- A confirmed security incident
- A serious incident requiring immediate escalation

**Why early identification matters:** the earlier an organization identifies a real attack, the greater its chance of limiting the damage. Example: an attacker gains access to one workstation. If the compromise is identified quickly, the workstation may be isolated before the attacker moves to other systems. If it remains undetected for several weeks, the attacker may have stolen credentials, accessed additional systems, installed malware, stolen sensitive information, established persistence, and moved laterally across the network.

> **Early identification can reduce the scope and impact of an incident.**

#### 2.3 Containment

Once an incident has been **validated and scoped**, the organization needs to prevent the attacker or threat from causing additional damage. The basic goal:

> **Stop the incident from spreading while preserving the ability to investigate and recover.**

**Example:** an employee's laptop is infected with malware; one possible containment action is to isolate the laptop from the network. However, containment is not always as simple as "disconnect everything". Immediately disconnecting or shutting down a system can:

- Destroy valuable volatile evidence
- Interrupt an attack that investigators are monitoring
- Prevent investigators from understanding what the attacker was doing
- Cause business disruption
- Alert the attacker that they have been discovered

Containment strategies should match the type of attack, the affected systems, the severity of the incident, the potential damage, the organization's operational requirements, and the evidence that needs to be preserved. **There is no universal containment action that works for every incident** — the correct response depends on the situation.

#### 2.4 Eradication

**Eradication** is the process of removing the root cause of the security incident and ensuring, with a high degree of confidence, that the threat has been eliminated. The goal is not simply to make visible symptoms disappear: the organization needs to understand **how the attacker gained access and what allowed them to remain** in the environment.

Eradication may include:

- Removing malware (using anti-malware tools)
- Reimaging compromised systems
- Applying security patches
- Deleting malicious accounts
- Resetting compromised passwords
- Revoking stolen credentials
- Removing persistence mechanisms
- Fixing the vulnerability that allowed the attack

**Example:** an attacker gained access because a server was running vulnerable software. Simply removing the attacker's malware would not completely solve the problem — the attacker might return because the original vulnerability still exists. A better response:

1. Remove the malicious software
2. Identify the vulnerability
3. Patch the vulnerable software
4. Investigate whether other systems have the same vulnerability
5. Check for additional attacker access
6. Reset compromised credentials if necessary
7. Verify that the attacker no longer has access

> **Eradication means removing the cause of the compromise, not just cleaning up the visible damage.**

#### 2.5 Recovery

After the threat has been removed, the organization can begin **recovery**: restoring normal business operations as quickly and safely as possible. Before recovery begins, the organization should have confidence that the attacker has been removed from the environment. Recovery may involve:

- Restoring systems from trusted backups
- Rebuilding compromised systems
- Restoring services
- Reconnecting systems to the network
- Verifying system configurations
- Monitoring systems for additional suspicious activity
- Confirming that systems are functioning normally

**Known good configuration** is a major concept during recovery: returning a system to a state believed to be secure, trusted, correctly configured, and free from the identified compromise.

**Example:** if a web server was compromised, the organization might rebuild the server, apply the latest security patches, restore the required application, restore clean configuration files, verify security controls, monitor the server, and then return it to production.

#### 2.6 Lessons Learned

After the incident has been resolved, the organization should not simply forget about it. The final step is to determine **what can we learn from what happened**. Examine:

- What caused the incident?
- How was it detected?
- How long did detection take?
- What worked well?
- What did not work?
- Which security controls failed?
- Could the attack have been prevented?
- Could the organization have detected it earlier?
- Did the incident response plan work?
- What should be changed?

Lessons learned help an organization improve its security: an attacker entering through an unpatched server could lead to a better patch management process; an attacker remaining undetected because logs were missing could lead to better logging and monitoring.

> **An incident should not only be something an organization recovers from. It should also be an opportunity to improve.**

#### 2.7 The Six Incident Response Steps at a Glance

| Step | Main Goal |
|---|---|
| **Preparation** | Get ready before an incident occurs |
| **Identification** | Determine whether an incident occurred and understand its scope |
| **Containment** | Prevent the threat from spreading or causing additional damage |
| **Eradication** | Remove the root cause and eliminate the attacker's access |
| **Recovery** | Restore systems and normal business operations |
| **Lessons Learned** | Learn from the incident and improve security |

Easy way to remember the process:

**Prepare → Identify → Contain → Eradicate → Recover → Learn**

### 3. Why the "Art of Investigation"?

The previous steps show something important: **containment, eradication, and recovery all depend on correctly identifying and understanding the problem first**. You cannot properly contain an attack without understanding what is happening; you cannot properly eradicate an attacker without knowing how they gained access or what systems they compromised; you cannot safely recover without knowing whether the attacker is still present. **Investigation is the foundation of effective incident response.**

There is **no single tool, methodology, or procedure** that can answer every investigation question. Cybersecurity incidents can be extremely different: a phishing attack is different from ransomware; ransomware is different from insider activity; a compromised web server is different from a stolen account; a network intrusion is different from data exfiltration. Because of this, analysts need to combine:

- Different security tools
- Different investigative methodologies
- Critical thinking
- Technical knowledge
- Experience
- Logical reasoning
- Sometimes even intuition or instinct

The analyst must adapt their investigation to the situation.

### 4. The Five Ws of an Investigation

A good investigation attempts to build a complete picture of what happened by determining:

- **Who** was responsible?
- **What** happened?
- **When** did it happen?
- **Where** did it happen?
- **Why** did it happen?

These questions help the analyst move beyond simply saying "there was a suspicious alert" and instead understand the entire story behind the alert. **Example:** instead of reporting "a suspicious login occurred", a stronger investigation might determine:

> An attacker used compromised credentials to log into a server from an unusual IP address at 2:13 AM, accessed sensitive files, and then attempted to create another account for persistence.

### 5. Building Your Own Critical Thinking Process

During an investigation or threat-hunting activity, analysts should repeatedly use a **critical thinking process**: continuously examine the available evidence, form conclusions, ask new questions, and then investigate those questions.

**Observe → Question → Investigate → Analyze → Form a conclusion → Look for more evidence**

Then repeat the process until you have a sufficiently complete picture. Security alerts rarely tell you the entire story. For an alert like "a suspicious PowerShell command was executed", the analyst needs to ask:

- Who executed it?
- Which machine executed it?
- Why was PowerShell being used?
- What command was executed?
- Was the command malicious?
- Where did the command come from?
- What happened immediately afterward?
- Did the process connect to another system?
- Was data accessed or stolen?

Investigation is more than simply reading alerts.

### 6. Starting an Investigation

A **Security Operations Center (SOC)** usually has security systems continuously monitoring the organization's environment. Detection engineers create **detection rules** and **correlation searches** that examine available logs and search for suspicious behavior. One common technology used for this purpose is a **SIEM**.

**SIEM** stands for **Security Information and Event Management**. A SIEM collects and analyzes security-related logs and events from different systems, which may include:

- Servers
- Workstations
- Firewalls
- Network devices
- Applications
- Authentication systems
- Security tools
- Cloud services

The SIEM can then search this data for patterns that may indicate suspicious activity.

#### From Detection to Investigation

```text
Logs and Events
       ↓
Detection Rules / Correlation Searches
       ↓
Suspicious Activity Detected
       ↓
Alert / Ticket / Notable Event
       ↓
Analyst Investigation
       ↓
Triage
       ↓
False Positive OR Confirmed Incident
       ↓
Close or Escalate
```

Different security tools may use different names and formats for their detections: an **alert**, a **ticket**, a **notable event**, or a **security finding**. For simplicity, these can be referred to as **findings**.

### 7. What Is a Finding?

A **finding** is an indication generated by a security system that something potentially suspicious or important has occurred. A finding does **not automatically mean that an attack happened** — this distinction is extremely important.

**Example:** a user logs in from an unusual country. That could be:

- A legitimate user traveling
- A VPN connection
- A misconfigured system
- A stolen account

The finding tells the analyst "something deserves attention". The investigation determines what actually happened.

### 8. Triage

**Triage** is the process of reviewing findings and determining what they mean and what should happen next. The analyst investigates the finding and decides whether it should be:

- Closed because it is harmless
- Marked as a **false positive**
- Investigated further
- Escalated as a confirmed incident

Triage is important because SOC analysts may receive many findings at the same time and cannot investigate every event with the same level of attention. They need to quickly determine **which findings are actually important** — this requires prioritization.

### 9. True Positive vs. False Positive

One of the first things an analyst often needs to determine is whether a finding is a **True Positive** or a **False Positive**.

**True Positive:** a security detection correctly identifies genuine suspicious or malicious activity. Example: a detection reports that a user account executed a known malicious command, and investigation confirms the activity was performed by an attacker. The alert was correct.

**False Positive:** a security detection reports suspicious activity, but investigation shows the activity was actually legitimate or harmless. Example: a detection flags a login as suspicious because it came from an unusual location, but the user was legitimately traveling and using a corporate VPN. The alert was triggered, but there was no attack.

**Important distinction — Alert ≠ Incident:** an alert is an indication that something deserves investigation; an incident is a confirmed security event that requires a security response.

### 10. The Five Questions to Ask During an Investigation

#### 10.1 Was this an actual attack?

First, determine whether the suspicious activity was actually malicious. Ask: is the activity legitimate? Is there evidence of malicious behavior? Was the detection triggered incorrectly? Can the activity be explained by normal business operations? This helps distinguish a **true positive** from a **false positive**.

#### 10.2 Was the attack successful?

If an attack actually occurred, determine whether the attacker achieved their objective: did they successfully authenticate? Did they execute malicious code? Did they gain unauthorized access? Did they steal credentials? Did they access sensitive information? Did they establish persistence? An attempted attack and a successful attack are not necessarily the same thing. **Example:** an attacker might attempt to exploit a vulnerable server but fail — that is very different from successfully exploiting the server and gaining administrator access.

#### 10.3 What assets were compromised?

Determine which systems or resources were affected: workstations, servers, databases, user accounts, cloud resources, network devices, applications, sensitive files, credentials. This helps determine the **scope of the incident**. **Example:** if one workstation was compromised, the incident may have a limited scope; if the attacker moved from that workstation to a domain controller and accessed the organization's database servers, the scope is much larger.

#### 10.4 What activities did the attacker carry out?

Once you know the affected assets, investigate what the attacker actually did. Determine whether they:

- Executed commands
- Created accounts
- Stole credentials
- Installed malware
- Modified files
- Changed configurations
- Moved laterally
- Accessed sensitive information
- Exfiltrated data
- Established persistence
- Attempted to hide their activity

This helps reconstruct the **attack timeline** and understand the attacker's behavior.

#### 10.5 How should my organization respond?

Finally, use everything discovered during the investigation to determine the appropriate response. Depending on the incident, the organization might need to:

- Isolate affected systems
- Disable compromised accounts
- Reset passwords
- Remove malware
- Patch vulnerabilities
- Restore systems
- Block malicious IP addresses or domains
- Monitor additional systems
- Escalate the incident
- Notify appropriate stakeholders
- Improve security controls

The correct response depends on what the investigation discovered.

#### The Five Questions as an Investigation Framework

```text
1. Was this an actual attack?
             ↓
2. Was the attack successful?
             ↓
3. What assets were compromised?
             ↓
4. What did the attacker do?
             ↓
5. How should we respond?
```

These questions turn a vague alert into a structured investigation. The questions move from **"Is something wrong?"** → **"What happened?"** → **"How bad is it?"** → **"What did the attacker do?"** → **"What should we do now?"** — essentially the core of security investigation.

### 11. Taking Good Investigation Notes

Good note-taking is an important part of cybersecurity investigations. An investigation can involve a large amount of information, and analysts may spend hours or even days working through evidence. Without good notes, it is easy to:

- Forget what you already checked
- Repeat the same investigation steps
- Lose important evidence or observations
- Forget why you reached a particular conclusion
- Have difficulty explaining the incident to another analyst
- Make mistakes when creating the final incident report

**What should you record?**

- What you observed
- When you observed it
- Which systems you investigated
- Which users were involved
- Which IP addresses were involved
- Relevant timestamps
- Important log entries
- Commands or searches you performed
- Evidence you discovered
- Hypotheses you considered
- Conclusions you reached
- Actions that were taken
- Questions that still need to be answered

**Example:** instead of writing "Checked logs. Looks suspicious.", a useful investigation note would be closer to:

> **14:32** — Reviewed authentication logs for the affected server. Found a successful login for the `admin` account from an unfamiliar external IP address. The login occurred outside the user's normal working hours. Further investigation is required to determine whether the account was compromised.

The second note is much more useful because another analyst can understand **what was checked, what was discovered, and what needs to happen next**.

### 12. Key Concepts to Remember

| Concept | Simple Explanation |
|---|---|
| **Investigation** | The process of examining evidence to understand what happened during a security event |
| **Incident Response** | The process an organization follows to detect, contain, remove, and recover from security incidents |
| **Preparation** | Getting the organization ready before an incident occurs |
| **Identification** | Determining whether a security incident occurred and understanding its scope |
| **Containment** | Preventing the threat from spreading or causing additional damage |
| **Eradication** | Removing the attacker, malware, vulnerability, or other root cause of the incident |
| **Recovery** | Returning systems and business operations to a trusted state |
| **Lessons Learned** | Reviewing the incident to improve future security and response |
| **SIEM** | A platform that collects and analyzes security logs and events |
| **Finding** | A security detection indicating that something potentially suspicious occurred |
| **Triage** | Reviewing findings and deciding their importance and appropriate next action |
| **True Positive** | A detection that correctly identifies real malicious or suspicious activity |
| **False Positive** | A detection that appears suspicious but is actually legitimate or harmless |
| **Critical Thinking** | Continuously questioning evidence and testing conclusions during an investigation |
| **Scope** | The overall extent of an incident, including affected systems, accounts, data, and resources |
| **Evidence** | Information that can help an investigator understand and prove what happened |

### 13. Core Takeaways

- **Investigation is a fundamental part of cybersecurity operations.**
- You cannot properly respond to an incident without first understanding what happened.
- **Preparation should happen before an attack**, not after one.
- **Identification and triage** help determine whether a finding represents a real incident.
- **Containment** limits the damage and prevents an attacker from spreading further.
- **Eradication** removes the root cause of the compromise.
- **Recovery** returns systems and services to a trusted state.
- **Lessons learned** help prevent similar incidents in the future.
- There is **no single investigation method or tool** that works for every situation.
- Good analysts combine **tools, technical knowledge, methodologies, critical thinking, and experience**.
- A security **alert does not automatically mean an incident occurred**.
- One of the first investigation goals is determining whether a finding is a **true positive or false positive**.
- The five investigation questions provide a useful framework: (1) Was this an actual attack? (2) Was the attack successful? (3) What assets were compromised? (4) What activities did the attacker carry out? (5) How should the organization respond?
- **Good notes are part of good investigation.** They make investigations easier to continue, review, explain, and report.

## Part 2 — Hands-On Investigations: The Ride-Alongs

### Growing the Business (Context)

One of our SOC customers, Frothly Beverages, has been expanding its business and recently purchased two smaller, local beverage companies: Thirsty Berner Brewing, a kombucha brewer, and Yellow Talon, known for their award-winning ginger ale and cream sodas.

With all this growth, Grace Hopper, the CEO of Frothly Beverages, continues to reinvest in the company. They now have badge readers at all their physical locations and VPN connectivity for all their hybrid and remote employees. Splunk ingests and correlates all their data through the Wonderland SOC. Unfortunately, they still face many threats, including possible insider threats.

It is not always easy to distinguish legitimate work activities from insider behavior until the evidence adds up. With all this increased business come more threats. Grace contacted us and requested we assist by investigating the following:

1. Physical security after an inventory revealed missing supplies
2. Access for remote or hybrid employees after suspected unauthorized access to Frothly's Customer Relationship Management (CRM) platform, SalesForce
3. Increased alerts about file changes on Frothly workstations

We will be using Splunk Enterprise Version 8.2.2 for these investigations since this is what the analysts at Frothly headquarters are using.

### What is an Insider Threat?

An **Insider Threat** refers to the potential for an individual, process, or system to use their authorized access or understanding of an organization to harm that organization.

An "insider" can be anyone or anything with access and authorization, such as current or former employees, contractors, or even systems and processes.

Insider threats don't always involve malicious intent; they can happen unintentionally through accidents, employee mishaps, or incidents related to unclear or incomplete security policies. **Whether caused by negligence or malice, insider threats should be taken seriously** — they can cause a great deal of damage and be difficult to detect.

#### Insider Threat Indicators

The following are just a few events that, when correlated, could potentially indicate an active insider threat:

- Login variations (increasing frequency, remote/local, odd times, etc.)
- Logging in frequently during vacation times
- Email and file transfers of sensitive information
- Unusual outbound traffic
- Increased printer usage
- Export of large reports/downloads from internal systems

For example, if you can connect unusual outbound traffic, large downloads, and sensitive data being sent to an external email, all from the same user and device, there is certainly a chance something bad is happening.

#### Non-Technical Data Sources

Not all data sources may be accessible or available in Splunk, but that doesn't mean they can't provide additional context to an investigation. Non-technical data might be loaded into a local instance of Splunk on an investigator's laptop, for example. Correlating log data with non-technical data, like physical security violations, Acceptable Use Policy (AUP) violations, or credit card expense reports, could provide clues that the logs alone would not.

### Ride Along 1 — Physical Security Audit: Disappearing Supplies

#### The Scenario

After the monthly inventory at the end of July, Frothly's CTO Fyodor Malteskesko reported missing materials from a supply closet to CEO Grace Hopper. Grace requested an audit of the logs from their physical security systems.

We need to review the badge data to determine **which employees are most actively badging** through the supply rooms **during the period when the supplies went missing**, and document any **suspicious access events**.

We use a custom sourcetype named **`st_frothly_events`**, which holds the data from events logged by the badge readers at Frothly's locations.

#### Getting to Know the Data

We can use "interesting fields" in Splunk to get quick snapshots of common values in the fields we are interested in. *Interesting Fields are fields that appear in at least 20% of the events.*

Let's take a look at the fields for **reader_desc** and **event_desc**. Expand each field value to see the values available for these fields.

![](../../assets/Pasted%20image%2020260815134127.png)

![](../../assets/Pasted%20image%2020260815134215.png)

![](../../assets/Pasted%20image%2020260815134552.png)

The general process for these searches — using the stats command with count by, which creates counts of each reader + employee first name + employee job title combination:

```spl
index=main sourcetype=st_frothly_events reader_desc=THIRSTY*
| stats count by reader_desc employee_first_name employee_job_title
```

This shows a count of badge accesses into the areas that include "THIRSTY" in their name:


![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/1_1_a_ThirstyBadgesFinishe.png)

#### Narrowing the Search

Our search is too broad — we don't need access events for the loading dock or other entrances. We need to narrow it down to the area where the supplies are held:

- Limit the search to just the supply room by changing the **reader description field** from "THIRSTY*" to "THIRSTY_BERNER BREW SUPPLY"
- Add a filter for only events where the access was granted (**event_desc** set to "Access Granted")
- Use the timechart command to visualize employees' access to the supply room over the period when the supplies went missing

```spl
index=main sourcetype=st_frothly_events reader_desc="THIRSTY_BERNER BREW SUPPLY" event_desc="Access Granted" employee_first_name="*"
| timechart count by employee_first_name limit=10
```

The **timechart count by** command works like **stats**, but timechart groups the events into buckets of time designated by a time span:

Observations from the visualization:

- Audrey, a brewing assistant, accesses the supply closet regularly.
- Fyodor, the CTO, has also accessed the closet. He performed the inventory of the supplies and reported the discrepancies, so that's not suspicious.
- Mateo, the Head Brewer for Frothly, has been accessing it more frequently than everyone else. Maybe nothing, **but it is an anomaly we need to note.**
- Richard, a Regional Sales Manager, is a hybrid employee and doesn't work in this facility. We don't know why he was in the supply area, so we'll **note this as an anomaly as well.**

#### Failed Access Attempts

Now check for indications of unauthorized access attempts, using an **event_desc** of "Access Denied Unauthorized Entry Level" or "Access Denied Unauthorized Time":

```spl
index=main sourcetype=st_frothly_events event_desc="Access Denied Unauthorized Entry Level" OR event_desc="Access Denied Unauthorized Time" reader_desc="THIRSTY_BERNER BREW SUPPLY"
| stats count by reader_desc, employee_first_name employee_job_title
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/1_1_a_unauthorizedAccessFi.png)

Looks like Nathaniel, a new Frothly intern, has been trying to access areas all over the place that he shouldn't be. Maybe honest mistakes by a lost intern, but **something could be going on.**

#### Summary

Physical security data can also be useful for analysts: it is a data source that helps observe behavior. It would be hard to monitor it all the time, so it's always good to consider if any searches used during an investigation can be further refined and turned into alerts later. Operationalizing information like time in and out, location, event type, and the like would facilitate future investigations into unusual behavior.

**Findings:**

1. Mateo accessed the supply room excessively during the period when the inventories were performed.
2. Richard's badge shows access to the supply room. Richard is a hybrid employee and sales manager not assigned to this location.
3. Nathaniel, Richard's nephew and new Frothly intern, attempted to access the supply room but failed because his badge was not programmed to access it.

### Ride Along 2 — Chasing Remote Access

#### The Scenario

Frothly Beverages asked us to review the login activity of one of their employees: Richard Schlitzer. Some activities in Salesforce raised questions while Richard was on-site with a customer in Tijuana, Mexico. Richard says he didn't log into SalesForce while he was in Mexico.

We are going to use events from the Checkpoint Firewall VPN and Frothly's SalesForce logins to investigate:

1. Examine data sources for VPN logins by Richard Schlitzer
2. Use iplocation to see where Richard is logging in from
3. Use geostats to visualize login data
4. Correlate data and analyze for anomalies

**Who is Richard Schlitzer?** Richard is a Regional Sales Manager, so he is on the road often and is expected to access the network remotely while traveling to customer sites. When he is not traveling, he spends most of his time in Northern California, near the headquarters office in San Francisco. Unfortunately for Frothly, Richard has had his credentials compromised several times already. We're going to investigate authentication data to help determine if that has happened again.

Start by searching the last week of the Checkpoint firewall events for Richard's VPN logins:

```spl
index=main sourcetype="cp_log" user=richards
```

![](../../assets/Pasted%20image%2020260815140358.png)

#### Using iplocation

Use the function **iplocation** to get a geographic location for the source IP addresses the user is logging in from. It's often the easiest way to generate a map from events with associated IP addresses. If you have IP address data in your events, iplocation looks up their location information in a third-party database and generates location fields in the search results: City, Country, Region, latitude, and longitude.

```spl
index=main sourcetype="cp_log" user="richards"
| iplocation src
| where City!=""
| table src City Region Country lat long _time
| dedup src
| sort _time
```

Using iplocation with the src field where the city is not (!=) empty removes events with an empty city. The search then builds a table and deduplicates logins from the same IP address, and finally sorts the data by time.

![](../../assets/Pasted%20image%2020260815140927.png)

#### What About Salesforce?

This is good information, but the activities in question happened on Salesforce, so we need to include that authentication data to get a complete picture. Use the iplocation command the same way as before, but with a different sourcetype. Since these are different systems, the username is not necessarily the same.

For Salesforce, the sourcetype is **`sfdc_streaming_api_events://login_events`** and the username for Richard is **`richard@yellowtalon.co`**:

```spl
index=main source="sfdc_streaming_api_events://login_events" Username="richard@yellowtalon.co"
| iplocation src
| where City!=""
| table _time Username SourceIp City
| dedup _time
| sort -_time
```

#### Using geostats

Combine both sources of authentication data and visualize it on a map, showing the location and the frequency of logins from each location. The **geostats** command will help with this, and we can easily turn this data into a map with Splunk's visualizations and count the logins from each city:

```spl
index=main (sourcetype="cp_log" OR source="sfdc_streaming_api_events:///login_events") (user=Richards OR Username="richard@yellowtalon.com")
| iplocation src
| where City!=""
| geostats count by City latfield=lat longfield=lon
```

![](../../assets/Pasted%20image%2020260815141155.png)

#### Correlating Data

Visualization is great, but the map didn't tell us anything. Maybe we aren't looking at this the right way. We have two sources of data — let's combine them and look at them in a table:

```spl
index=main (source="sfdc_streaming_api_events://login_events" OR sourcetype="cp_log") (Username="richard@yellowtalon.co" OR user=richards)
| eval src=coalesce(src,SourceIp)
| eval user=coalesce(Username, user)
| iplocation src
| eval State=coalesce(Region, Subdivision)
| where City!=""
| table _time user src City State Country
| dedup _time
| sort -_time
```

Explanation of the search:

- List both data sources and usernames, just like we did for the geostats visualization. We use **OR and not AND** — if we looked for events with a Salesforce source AND a VPN sourcetype, we wouldn't get any results: they are different data sources.
- iplocation uses the **src** field from VPN logins. The Salesforce data doesn't have a src field; instead, it has **SourceIp**, so we include SourceIp to make sure we see the location for those events as well.
- Remove authentication events without **City** populated.
- Deduplicate anything with the same timestamp, mainly to clean up duplicate VPN data, then sort by newest time first.

![](../../assets/Pasted%20image%2020260815141411.png)

### Ride Along 3 — Alarming File System Activity

#### The Scenario

The IT department at Frothly has been investigating an increase in alerts for abnormal file system activity and they need our help.

The DTEX InTERCEPT agent that Frothly uses provides contextual human activity intelligence and endpoint telemetry for their on-premise assets. In the SOC, we use the DTEX Splunk Add-on from Splunkbase to collect events and alerts from the system.

We were asked to look for **anomalies related to file system changes**, so the investigation starts pretty broad.

#### File Extensions

Add the interesting field **Source_File_Extension** to our selected fields and take a quick look at what type of files DTEX has activity information for. We see plenty of recognizable file extensions such as .pdf or .jpg, but what is the "lockbit" extension? That file extension looks like trouble!

Normally we use **stats** to calculate or aggregate statistics, but here we use it with "values" to list all values in a field. This way we can start by looking at all the VALUES for Activity_Details, after filtering for just file system activity:

```spl
index=dtex sourcetype=dtex_st_activities Activity_Group=FileSystemActivity Source_File_Extension=lockbit
| stats values(Activity_Details)
```

The results are lexicographical: sorted based on the values used to encode the items in computer memory. In Splunk software, this is almost always UTF-8 encoding, which is a superset of ASCII. You can use values() with other commands too, including tstats, chart, and timechart.

Use your internet browser and search engine of your choice to answer the following questions:

1. **Determine what type of malware we are dealing with.**
2. **(Extra Credit)** What variant(s) of the malware should we suspect here?

After a quick online search, we can confirm that the ".lockbit" extension indicates **LockBit ransomware**, the kind that encrypts data and then asks you to pay for access to the decryption key. It looks like we are dealing with a ransomware infection!

Research shows at least 3 variants of the ransomware:

- **Variant 1** is the original version, which renames files with the ".abcd" extension name. It also includes a ransom note with demands and instructions for alleged restorations in the "Restore-My-Files.txt" file, which has been inserted into every affected folder.
- **Variant 2** uses a ".LockBit" file extension, giving the malware its moniker; however, it is largely identical to the original version.
- **Variant 3** of the malware no longer requires users to download the Tor browser in its ransom instructions. Instead, it sends victims to websites via traditional internet access.

**We are dealing with either variant 2 or 3.** We would be able to narrow that down more with access to the ransom instructions.

#### Finding the Affected Hosts

We need to find out what machines are reporting this. There could be multiple hosts impacted, so search for the lockbit extension across all the DTEX data, and use stats and count to determine how many and which hosts may have been infected:

```spl
index=dtex sourcetype=dtex_st_activities Activity_Group=FileSystemActivity Source_File_Extension=lockbit
| stats count by Device_Name
```

Richard Schlitzer's host has been infected with ransomware. We'll need to notify our incident response team and let Frothly know what we have found so appropriate responses can be taken before this spreads.

#### MITRE ATT&CK Technique

Our event description gave us enough clues to make a hypothesis about this finding, but it also had MITRE Techniques [T1110](https://attack.mitre.org/techniques/T1110/) and [T1201](https://attack.mitre.org/techniques/T1201/) mapped to it that can give us additional information about the type of threat that this finding may have uncovered.

MITRE ATT&CK tactics and techniques are configured by our engineers when they develop correlation searches, and they are a great resource for us analysts.

