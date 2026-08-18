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

## Part 3 — Investigation: Brute Force at a T-Shirt Company

### 2.1.a Learn About the Source IP

This customer's internal IP addresses are in the 192.168.x.x range. We're not sure why we would see a 172.x IP address in our logs (172.16.16.245). Let's gather more information about this IP and figure out who or what it is.

At this moment we have very little information about this IP address, so use a very general SPL search to see the type of logs (sourcetypes) we have that contain this address. Because we are familiar with the T-shirt company's environment and know they are fairly small with good resources in their Splunk instance, we search through ALL our indexes. If this were a larger or more complex company, it could be safer to target a specific index at a time or shorten our time range to avoid running a resource-intensive search:

```spl
index=* 172.16.16.245
| stats count by sourcetype
```

The results show two sourcetypes that call our attention:

- **WinEventLog:** related to Windows events and usually contains authentication information — we might find the logs that triggered our Brute Force search there.
- **ftg_event:** a log from the customer's Fortigate firewall — it could give us a clue as to where this IP address is connecting from or what other activities it has attempted.

Let's take a look at the **ftg_event** records for this IP address:

```spl
index=* 172.16.16.245 sourcetype=fgt_event
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/2.1.a_step3_ftg_NOPROCESS_.png)

Here's a close up of two entries from the ftg_event source that caught our attention:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/2.1.a_step3_ftg_answer_NOP.png)

These logs show the creation and tear-down of an SSL tunnel. 172.16.16.245 was the IP assigned to the tunnel (_tunnel ip), so we assume this is a Virtual Private Network (VPN) client. This connection requires configuration on the client and the customer's firewall, so there has to be a level of trust AND we should be able to learn more about the purpose of this connection. We also see a user "WeSellTshirts" — maybe a partner of the T-shirt company? At least we have enough now to know who to ask.

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_2.1.a_Maya_Ashley_NOPR.png)

**Summary:** some digging with the rest of our team revealed this is a VPN that allows connectivity to select services for a partner that sells the T-shirt company's product internationally. That doesn't necessarily explain all the failed authentication errors, so let's keep working on this.

### 2.1.b Learn About the Targets

We know that activity related to the IP address 172.16.16.245 triggered a correlation search that looks for Brute Force activity. From the finding, the search is called "Brute Force Access Behavior Detected - 1". That's enough to get us started.

**Learn more about the correlation search:** sometimes it's good to just start at the beginning — look at the search that is already doing the work. This search is relying on the **authentication data model**, which makes it easier to narrow down our search.

**Wide search:** since we have an IP address, we could do a wide search just for the IP and start narrowing down from there:

```spl
index=* 172.16.16.245
```

But what if it returns too many results, or takes too long? We may also need to avoid running a very open search in a large environment or in one with limited resources. **Always keep in mind how a resource-intensive search could impact the environment.** In this case, we have more information to narrow down our search, so let's do that.

**Narrow down our search:** since we know the logs we are looking for were added to the authentication data model, we can use the "authentication" tag to limit our search. It's also useful to begin by looking at the sourcetypes available to more easily decide where to go next:

```spl
index=* tag=authentication 172.16.16.245
| stats count by sourcetype, source
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_1.2.b._sourcetypes_NOP.png)

From the results above, the Security WinEventLog has the data we are looking for. Windows logs are very common and as analysts we eventually get very familiar with them. But if you are not familiar with a log you are reviewing, looking at the **interesting fields** can be a really helpful way to orient yourself:

```spl
index=* 172.16.16.245 sourcetype=WinEventLog
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_2.1.b_Targerts_NOPROCE.png)

Just by looking at the interesting fields we were able to quickly identify our potential targets. Most seem like user devices, but that **Main-Inv** one could be important!

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/PTPtHR/AoI_2.1.b_Targerts_NOPROCE.png)

So we found a few devices that were targeted by that 172.16.16.245 IP address:

- DBell
- PPark
- JSam
- Main-Inv

That's a very high number of events in a short period of time.

### 2.2 Was the Attack Successful?

- Suspicious activity triggered our "Brute Force Activity Detected" rule, which is tied to Credential Access and Discovery MITRE ATT&CK tactics.
- The source IP of this activity (172.16.16.245) is from a user connecting through a VPN that is reserved for a partner that helps with the company's international sales.
- This IP has hundreds of failed authentication attempts against at least 4 different devices, one of which seems to be a corporate server (Main-Inv).
- There were at least 2 "successfully logged in" messages in the records.

Our initial review of the logs indicates that our alert **did** catch a brute force attack happening.

### 2.2.a Which Assets Were Compromised?

While identifying our targets, we found that the logs that triggered the Brute Force alert are part of a Windows Security Audit log. Observe two events from this log and see what important information you can identify:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_2.2a_Event1_1.png)

Event #1 — Part 1 of 2

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_2.2a_Event1_2_NOPROCES.png)

Event #1 — Part 2 of 2

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_2.2a_Event2_1_NOPROCES.png)

Event #2 — Part 1 of 2

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/AoI_2.2a_Event2_2_NOPROCES.png)

Event #2 — Part 2 of 2

Now that we know the EventCode for a successful login (**4624**), we can use it to narrow down our search and see the devices (hosts) in which authentication succeeded from our suspicious IP (172.16.16.245):

```spl
index=* 172.16.16.245 sourcetype=WinEventLog "EventCode=4624"
```

There are 2 devices (hosts) in which authentication succeeded from the suspicious IP. Review the **Assets and Identity** information populated by our engineers to learn about the compromised devices.

### 2.2.b What Activities Did the Attacker Carry Out?

**Uh-oh, we have a problem!** We were looking for additional Windows logs for the **Main-Inv** asset and there are no records after the successful authentication message we saw. It also seems like other Endpoint Detection and Response tools have been stopped. We don't have records from that machine after the attacker was able to crack the password.

How should we continue our investigation? When stuck or unsure of where to go next, rely on existing frameworks to help think through a problem:

- [Lockheed Martin Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
- [MITRE ATT&CK Enterprise Matrix](https://attack.mitre.org/tactics/enterprise/)

**Cyber Kill Chain:** with the information we have, we can assume the attacker already completed or even skipped the **Reconnaissance** stage — they knew which assets to target and were successful at gaining access by **exploiting** a VPN service with a partner and potentially weak or reused passwords. Their next steps will be related to taking **action**, maybe **installing malware** or **getting data out**. They probably expected their VPN link to be temporary, so they would need another way of keeping communication with the compromised assets — there could be **command and control (C2)** communication in the network.

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/THE-CYBER-KILL-CHAIN-_NOPR.png)

**MITRE ATT&CK Enterprise Matrix** helps go deeper. Looking at the tactics:

- The attacker has done some level of **Reconnaissance**.
- Our initial alert hinted at **Credential Access** and **Discovery**, all leading to **Initial Access** to our assets.
- They started **Defense Evasion** because our local logs and antivirus protection are gone.
- They probably already attempted **Privilege Escalation** and **Persistence**, but it will be hard to see that without the missing logs.
- However, we should be able to see attempts at **Lateral Movement**, **Command and Control**, and **Exfiltration** if any.

Let's focus our search on those last 3:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/MITRE_ATTACK_ENTERPRISE_NO.png)

#### The Main-Inv Asset

We learned that the Main-Inv asset is a server that holds important inventory and financial information. This is a high-risk server and therefore has strict rules about communication.

It **does** have limited internet access related to system updates, so we will start with the **stream:http** sourcetype to see if there's anything out of the ordinary. We know the index and both the IP address and the device name; we include both the IP and the device name in our search to ensure we get all the relevant traffic:

```spl
index=bta-ts sourcetype="stream:http" (host=Main-inv OR src_ip=192.168.55.3)
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/Screenshot%202024-03-27%20.png)

We see over 1000 results; let's see how we can make them more manageable by looking at the **interesting fields** first:

- We have 11 **destination** IPs; it wouldn't be too hard to check them all out, but there is an **action** field that could help narrow our data down. Looking at **blocked** data can be helpful to understand an attacker's intent, but right now we are interested in **allowed** traffic to see if anything malicious happened. Adding **action=allowed** lowers our total numbers to 783 and 9 destination IPs.
- The **http_method** can also be helpful to filter between downloads (**GET**) or uploads (**POST**).
- **HTTP User Agents** related to Microsoft are expected, not so sure about Mozilla, but let's keep looking.
- 20 **uris/urls** in our filtered logs; many times these won't give away too much, but we do see a .bin (binary) file in one of them. We wonder what that is.

#### Downloading a Binary?

Looking at the events related to the URL we spotted earlier, it seems like we are on the right path. A PowerShell call within our HTTP stream makes alarm bells ring, especially given the **-e switch** that appears — short for the "EncodedCommand" switch, which attackers frequently use to hide their activities.

We can see this is part of a successful (HTTP 200 OK) GET request of a file called `d0cde86d47219e9c56b717f55dcdb01b0566344c13aa671613598cab427345b9.bin`. Does that look like a hash to you as well? We now have a destination IP address (13.107.4.50); let's see if there's any threat intelligence on that:

- **AlienVault OTX** does have some information about this IP: it has appeared in AV detections and is associated with Malware and Trojans.
- **VirusTotal** also has it flagged by a few security vendors.

#### Decoding with CyberChef

PowerShell encoded commands can usually be decoded with publicly available tools. Using [CyberChef](https://gchq.github.io/CyberChef/), copy the encoded stream and add "**From Base64**" to the recipe. Within the output we can see another "FromBase64String" entry, so pull that out into a separate CyberChef window. The "From Base64" ingredient turned out a lot of random characters, but after a couple tries the "Detect File Type" ingredient identified it as a **gzip file**. This is not looking good.

#### More Intelligence

Following a hunch, search for that .bin filename on VirusTotal — the results give more and more indication that we are dealing with Malware. The "popular threat label" field points to **Clop**, which is a file-encrypting virus used for Ransomware.

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/Aoi_2.2.b._VT_Clop_NOPROCE.png)

Of course it's possible that the filename is not a hash, but it would be quite a coincidence that a non-malicious filename actually matched a known threat's hash. We are leaning to think we are dealing with a Clop variant here.

## Part 4 — Investigation: Frothly Domain Controller Compromise

### 3.1 Review the Finding

We have a new high-urgency notable event that needs to be addressed. The title of the finding is "**Creation of Shadow Copy**".

**Wait! What's a shadow copy?** It's a snapshot of a volume that duplicates all of the data held on that volume at an instant in time... even if the data is in use!

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/shadowCopy.png)

Expand the event in the Incident Review dashboard of Splunk ES to see more information, like a description of the event, additional fields that are part of the correlation event, the search itself, and contributing events:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/eventDetails.png)

For this notable event, we can see that a volume shadow copy has been created on the host **labrador.froth.ly** (labrador).

#### The Who and What

Before we investigate this finding, let's gather some more information about the **IP address** and the **user** involved with this event. These are often central to investigations and can help gain more context. In Wonderland we use a couple of things in Splunk ES to help us quickly gather information on assets and identities: the **Asset Investigator** and **Identity Investigator**.

**Asset Investigator**, filtered for the IP address **192.168.70.150**:

- Labrador is categorized as an AD (Active Directory) Server — in other words, a **Windows-based domain controller**. It's a high-priority asset.
- The host is owned by user "peat cerf" (**pcerf**).
- Other very recent findings for labrador include: **large volume of outbound web traffic**, **remote PowerShell launches**, and **registry autoruns being added**.

**Identity Investigator** on the user pcerf:

- Peat Cerf is a **technical user**, which means he has **elevated privileges**.
- There is also information about Peat's work location, an email, and a supervisor — all useful when responding to an incident.
- This user's credentials have been identified in other findings, including one for **excessive failed login attempts**.

The user pcerf is a technical user and the owner of the host involved in the finding. Other findings recently detected: involved in the "Excessive Failed Logins" notable event, executed PowerShell on host labrador, and created shadow copies on host labrador.

Host labrador is a Frothly Brewery Windows Active Directory Domain Controller. Other findings recently detected: large volume of outbound web traffic, creation of shadow copy, remote PowerShell launches, and registry autorun added.

### 3.2 Was It an Incident?

We know that labrador is a high-value target for an attacker. We need to determine if there has been a compromise. We can start by learning more about the processes from our finding: **spoolsv.exe** and its **child process vssadmin.exe**.

**What is spoolsv.exe?** Spoolsv.exe is a core Windows process that runs by default on Microsoft OS. The service spools print jobs and handles interaction with the printer. Spoolsv.exe is located in the C:\Windows\System32 folder and runs automatically when you start a system. On domain controllers, the Print Spooler service is also responsible for printer pruning from Active Directory: this job checks if the print server is reachable and the printer is still shared; if not, it deletes the printQueue object from AD.

**What is vssadmin.exe?** The event that triggered the finding is based on the creation of a volume shadow copy, and that's where vssadmin.exe comes in. Vssadmin.exe is a utility that Microsoft has included on Windows OS since Windows Vista. It provides functionality to list, delete, and resize Shadow Volume Copies. A Shadow Volume Copy is essentially a snapshot, or backup, of your files. This same technology is also used by the Windows' System Restore feature, which helps you roll back Windows to a previously working configuration in case there is a problem. Unfortunately, with the rise of ransomware and other cyber attacks, this tool can be exploited by an attacker.

Look at our **Windows Event logs** for more information about what happened on the host, filtering for **Event Code 1**, which provides extended information about a newly created process. We are looking for anything related to **vssadmin.exe**:

```spl
index=main sourcetype=xmlwineventlog EventCode=1 dest=labrador process_name=vssadmin.exe
| table _time user process process_exec parent_process
| sort _time +
```

### 3.3 Investigating Suspicious Activity

Since we know the IT department didn't authorize this activity, we'll need to keep investigating. If you recall, another notable event was linked to our user Peat, for excessive logins. It's possible Peat's credentials were compromised.

Let's search for any processes on labrador that involve Peat's credentials and would have spawned from the spoolsv process:

```spl
| tstats summariesonly=true count from datamodel=Endpoint.Processes where Processes.parent_process_name="spoolsv.exe" Processes.dest="labrador.froth.ly" Processes.user="pcerf" groupby _time span=1s Processes.parent_process Processes.process
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/3_3_interactive.png)

**Following wscript.exe:** the presence of wscript.exe in our results tells us that **Windows Script Host** was used. This provides an environment in which users can execute scripts in various languages to perform tasks. In our case, it looks like commands are being used to perform a variety of nefarious activities involving malicious javascript files.

Do a broad search across our data to see if there are any other instances of Windows Script Host being used to run suspicious processes or functions:

```spl
| tstats summariesonly=true count from datamodel=Endpoint.Processes where Processes.process_name="wscript.exe" groupby _time span=1s Processes.process Processes.process_name Processes.parent_process Processes.dest Processes.user
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/3_3_interactiveb.png)

### 3.4.a Exploring User "pcerf"

Since the credentials for Peat Cerf, or **pcerf**, have been compromised, let's look at what this user was doing on labrador, the domain controller. Using a saved search crafted to investigate assets and the processes running on them, we noticed a few interesting events:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/3_4_a_otherstuff.png)

**Where did the adversary get in?** Adversaries don't always compromise their target directly. Often, they compromise a point in the network and use this compromised system to move laterally through the network.

Adversaries can "move" laterally by using **remote PowerShell sessions**. Using a remote session, they can do reconnaissance, execute code, or even move tools or stolen data. That's why it is so important to understand the basic artifacts left by remote PowerShell sessions. A good way to look for these sessions is by looking for PowerShell remoting, which is performed using **WinRM services**.

### 3.4.b Exploring with Data Models

#### hefeweizen_tips.js

We want to see if we can learn more about this **hefeweizen_tips.js** file. Start by searching through the **Endpoint data model**, filtering for files that contain "hefeweizen_tips.js" in their name. Maybe we can discover where this weird behavior started:

```spl
| tstats summariesonly=true count values(Filesystem.file_size) AS file_size from datamodel=Endpoint.Filesystem where Filesystem.file_name="*hefeweizen_tips.js*" groupby _time span=1s Filesystem.file_name Filesystem.file_path
| drop_dm_object_name("Filesystem")
| table _time file_name file_path
| sort + _time
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/Filesystemresults.png)

This information happens to come from **Sysmon Event Code 15**, FileCreateStreamHash, which was identified through the data model and the search above. According to Microsoft's documentation, this event is generated when a named file stream is created, and it generates events that log the **hash** of the contents of the file to which the stream is assigned. There are malware variants that drop their executables or configuration settings via browser downloads, and this type of event is aimed at capturing that, based on the browser attaching a Zone.Identifier "mark of the web" stream.

**Zone.Identifier / the "mark of the web":** the Windows OS keeps track of which files were downloaded from the Internet (or a network share) by tagging them with a hidden NTFS Alternate Data Stream file named Zone.Identifier.

#### So, Where Did the .js File Come From?

So far that Zone.Identifier told us it was downloaded from the web. Let's use the **Web data model** to try and learn more:

```spl
| from datamodel:"Web"."Web"
| search (url="*hefeweizen_tips.js*")
| head 100
```

This search only returns a handful of events... but look at THIS event:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/3_4b_results.png)

#### A Closer Look at HTTP Headers

When investigating security events, the **HTTP referer header** may be helpful for "walking backward" and getting to the source of compromises:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/3_4_b_HTTP_Header.png)

**What's an HTTP Referer?** The HTTP Referer is used to indicate the URL from which the current request originated. The referral may be due to a user clicking on a hyperlink or submitting a form, for example. They are used because site statistics about where traffic is coming from can be valuable in a variety of business contexts — for example, if a company posted an ad on social media, they would like to see how effective the ad has been in redirecting users to their main website.

**How does it work?** You click a link on a page on "https://websiteA.com", the link directs you to another page or site such as "http://websiteB.com". The HTTP Referer received by website B will have the value for website A, since that is the source of the reference — in other words, that's how you "found" website B.

### 3.5 Adjacent Activities

Let's take a step back and look at the other findings involving this domain controller. We recall an event that involved a lot of web traffic on this host, which concerns us. Searching our findings from the Splunk ES Incident Review Dashboard for anything involving labrador results in several events:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/webactivity.png)

What do you think about our domain controller sending outbound web traffic? The event listed just after the "Creation of a Shadow Copy" finding we looked at earlier involves labrador sending a large amount of web traffic. Outbound web traffic concerns us since someone on this host just **created and deleted a volume shadow copy**... this could be exfiltration.

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/websiteGif.gif)

In the event description, we can see that Peat's user credentials are involved with this finding as well, and we have a destination URL for the web traffic that triggered the finding. We're going to have to check out the destination of all this traffic: **"dunkel-hefeweizen.azureedge.net/index.html"**.

Instead of writing SPL to search for web activity, since we have Splunk ES we can use the **Web Search** from the **Security Domains** tab. Filter for "labrador" as the source — do you remember its IP address? (192.168.70.150). These results should help us determine what this domain controller was doing on the internet:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/DC_gif.gif)

WOW! That's a lot of traffic going to "**dunkel-hefeweizen.azureedge.net**"! It is even at the top of the list for labrador's IP address (192.168.70.150)!

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/lab-websearch.png)

The IP address for this site is **152.195.19.97**, based on the "destination" field. Use the **Web data model** and look in more detail at any traffic between our domain controller and this IP address:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/dunkel_gif.gif)

There is a whole lot of web activity, including a lot of data outbound to this suspicious domain. Why is our asset sending more data out to this site? That's not typical user web browsing traffic!

### 3.6 Gathering More Evidence

#### 3.6.a Exploring DNS

**Who is dunkel-hefeweizen?** We want to learn a little more about this domain, so let's take a look at DNS queries. Use the **dest_ip** field to filter only for DNS responses sent to labrador's IP Address (192.168.70.150). Since we know the IP of the dunkel-hefeweizen.azureedge.net server (152.195.19.97), we can also use it on our search to show only DNS queries that include that IP address in the **answer** field:

```spl
transaction sourcetype=stream:dns dest_ip="192.168.70.150" answer="152.195.19.97" record_type=A
| table timestamp hostname{}
```

Having various hostnames appearing in DNS responses for a single IP can be normal when a target URL is using a Content Delivery Network (CDN) — a geographically distributed group of servers that caches content closer to end users. CDN services continue to grow in popularity, with the majority of today's web traffic being served through them. It appears that we have some CDN provider sites in the DNS responses for "dunkel-hefeweizen" (i.e. scdn*, taucdn.net):

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/DNS-repies.png)

What we have here is a case of the adversary hiding **Command and Control (C2) within web traffic**. Furthermore, their location is concealed because they are using Azure Edge services to mask their malicious domains and activities. This can be done with a technique called **domain fronting**.

**MITRE ATT&CK Technique ID: T1090.004** — read more at the [MITRE ATT&CK website](https://attack.mitre.org/techniques/T1090/004/):

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/MITRE_DomainFronting_NOPRO.png)

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/CDN_network.png)

**How domain fronting works:** adversaries take advantage of the host field in the HTTP 1.1 header and use CDNs to point to different resources — it's just swapping in the attacker's host header. The DNS response and TLS Server Name Indication (SNI) contain one domain. This would be the front domain... or **dunkel-hefeweizen** in our case. Meanwhile, the HTTP header's host address, which is obscured by HTTPS encryption, contains ANOTHER destination. That's where the C2 traffic actually ends up:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/CDN_gif.gif)

This technique is used to disguise the true destination of labrador's messages by rerouting the data through a CDN that would appear otherwise safe.

#### 3.6.b Exploring Network Traffic

Let's take a broader look at events involving labrador, specifically anything destined to the host where the malicious file seems to originate from. If you recall, when we used the Web data model, we found that the **hefeweizen_tips.js** file was downloaded from the IP address **46.101.247.84**.

Use that IP address and part of the filename in the search, then manually narrow our results around the timeframe of our other events:

```spl
index=main host=labrador dest_ip=46.101.247.84 AND *hefeweizen
| sort _time
```

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/3_6_b_reddit__NOPROCESS_.png)

In the first event that appears, the HTTP referer is for a **reddit URL**! This may provide a clue as to how a malicious file was introduced to Frothly's environment. We will need to look into the source IP address of **192.168.70.167**. Perhaps we can find ground zero for this malicious file.

#### Scoping: Research the Host with the Private IP

The Wonderland SOC Engineers have populated a list of assets and identities within ES that we can reference during investigations. Let's see if we can learn something about this device using the **Asset Investigator**. Identifying more information about a device communicating with assets involved in an investigation may be important to scoping the incident:

![](https://www.netacad.com/scorm-content/ff9e491c-49be-4734-803e-a79e6e83dab1/4090b743-8a46-4f77-b4ca-bcbd663935c6/en-US/02a0a0d2-e97c-45db-b190-9df0959adb06/scormcontent/assets/whois_167.jpg)

**It looks like a lab workstation may be the source of the infection!**

### 4.0 Wrapping Up: What We Learned

#### Start on the Inside (Frothly Ride-Alongs)

Our first ride-along didn't start with an event. We actually had 3 separate requests from Frothly's team to help them investigate suspicious activity across different systems and locations. What I found interesting about this investigation was that each answer we found was connected — we just had to "zoom out" enough to see those connections.

These short investigations allowed us to work with new sourcetypes and types of events. It probably wasn't as scary as you initially thought. It also helped us recognize how important it is to keep track of the time an event happens, and what else might be happening at that same time from other sources or at other locations. We would have missed that Richard's login activity was strange if it wasn't for that.

In this ride-along, we practiced our critical thinking to:

- Observe, question, and analyze what we were seeing
- Consider connections that may not have been obvious at the start
- Interpret findings to decide which paths were worth chasing

#### Cut the Link? (T-Shirt Company)

Our second investigation started with an unknown IP address acting strangely. By the end, we found evidence of credential compromise and malware at the T-shirt company.

For a moment there we thought we had run into a dead end when the attacker disabled all security software and logging on the compromised machine, but we used the Lockheed Martin Cyber Kill Chain and MITRE ATT&CK tactics to think through the problem and find alternative investigation paths. We also got to work with new sourcetypes and understand what they meant by sorting through **interesting fields** and noticing **keywords** and **codes** we could research.

Wearing our critical thinking cap helped us:

- Solve a problem by finding a solution when we don't have the data we expected
- Consider the consequences of what we were seeing, and alert our team so they could "cut the link" on time
- Evaluate the information we gathered, understand what it meant, and decide how to move forward

#### Trouble Brewing at Frothly (Domain Controller)

Trouble was definitely brewing at Frothly! This investigation uncovered a compromise, lateral movement, and data exfiltration, all performed by a clever attacker who tried to cover their Command and Control activities with domain fronting. But we were more clever!

We noticed how they leveraged "normal" system applications to launch their own malicious scripts. We also learned how a simple user misstep can lead to an infection and how important it is to collaborate with users during incidents and investigations. Our incident response team worked with Mateo, a Frothly employee. He recognized he had made a mistake by clicking on that link and shared additional information that helped with the investigation and improved Frothly's security policies.

Our trusty critical thinking cap helped us:

- Keep an open and exploring mind to find and follow different leads
- Identify when we needed help from a colleague to make sure we were on the right track
- Remember it is OK and normal to stumble across data, logs, or activities we don't understand right away, because we can research them or ask for help
