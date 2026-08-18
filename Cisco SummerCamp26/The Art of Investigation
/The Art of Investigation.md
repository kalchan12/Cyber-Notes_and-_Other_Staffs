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

