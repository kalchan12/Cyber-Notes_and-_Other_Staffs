# The Art of Investigation

## 1. The Importance of Investigations

Investigation is one of the primary responsibilities of a **Cyber Defense Analyst**. However, it is not only the job of an analyst; investigation is an important part of an organization's overall security operations.

When a security incident occurs, an organization cannot simply start fixing systems immediately. It first needs to understand **what actually happened**.

A typical investigation needs to answer questions such as:

- Did a security incident actually occur?
    
- What happened?
    
- When did it happen?
    
- Which systems or assets were affected?
    
- How far did the attacker get?
    
- What actions did the attacker perform?
    
- Is the attacker still inside the environment?
    
- What should the organization do next?
    

### Why Investigation Matters

Before an organization can properly recover from an incident, it must first **identify and understand the incident**.

The general idea is:

> **Detect → Investigate → Understand → Respond → Recover**

Without a proper investigation, an organization might:

- Treat a harmless event as an attack.
    
- Miss a real attack.
    
- Contain the wrong system.
    
- Delete important evidence.
    
- Fail to identify compromised systems.
    
- Allow an attacker to remain in the environment.
    
- Repeat the same security mistake in the future.
    

Investigation therefore provides the information needed to make good security decisions.

# 2. Recovering from a Security Incident or Breach

Every organization can have its own **Incident Response Plan** depending on its infrastructure, business requirements, security policies, and resources.

However, many incident response frameworks follow similar ideas.

Two commonly referenced frameworks are:

- **SANS 6-step Incident Response Process**
    
- **NIST 4-phase Incident Response Framework**
    

Although these frameworks organize the process differently, they contain many of the same fundamental activities.

The SANS-style process discussed here consists of six major steps:

1. Preparation
    
2. Identification
    
3. Containment
    
4. Eradication
    
5. Recovery
    
6. Lessons Learned
    

# 3. Preparation

**Preparation** happens before a security incident occurs.

The goal is to make sure that an organization is ready to respond when something goes wrong.

Preparation can include:

- Creating an **Incident Response Plan**.
    
- Defining the roles and responsibilities of security personnel.
    
- Establishing communication channels.
    
- Preparing security tools.
    
- Making sure logs are available.
    
- Establishing procedures for collecting evidence.
    
- Training security teams.
    
- Preparing backups and recovery procedures.
    
- Testing incident response procedures.
    

### Why Preparation Matters

During a serious attack, there may be a lot of pressure and confusion.

If an organization has already decided:

> "If this happens, this person does this, that person does that, and we communicate through this channel."

then the team can respond much faster.

Without preparation, security teams may waste valuable time deciding what to do while the attacker is still active.

### Simple Example

Imagine a company discovers that its database server has been compromised.

If the company has a prepared incident response plan, it may already know:

- Who investigates the incident.
    
- Who is responsible for isolating the server.
    
- Who contacts management.
    
- Who handles legal requirements.
    
- Who communicates with affected users.
     
- Where investigation records should be stored.
    

That preparation can significantly reduce the impact of the incident.
# 4. Identification

**Identification** is the process of determining whether a suspicious event is actually a security incident and understanding its scope.

This is where **investigation and triage** become especially important.

Security teams receive many alerts, but not every alert represents a real attack.

The analyst needs to investigate the available evidence and determine what is actually happening.

### Triage

**Triage** is the process of analyzing findings and deciding what should happen to them.

An analyst may determine that a finding is:

- Harmless activity.
    
- A false positive.
    
- Suspicious activity requiring additional investigation.
    
- A confirmed security incident.
    
- A serious incident requiring immediate escalation.
    

### Why Early Identification Matters

The earlier an organization identifies a real attack, the greater its chance of limiting the damage.

For example:

> An attacker gains access to one workstation.

If the organization identifies the compromise quickly, it may isolate the workstation before the attacker moves to other systems.

If the compromise remains undetected for several weeks, the attacker may have:

- Stolen credentials.
    
- Accessed additional systems.
    
- Installed malware.
    
- Stolen sensitive information.
    
- Established persistence.
    
- Moved laterally across the network.
    

Therefore:

> **Early identification can reduce the scope and impact of an incident.**

# 5. Containment

Once an incident has been **validated and scoped**, the organization needs to prevent the attacker or threat from causing additional damage.

This process is called **containment**.

The basic goal is:

> **Stop the incident from spreading while preserving the ability to investigate and recover.**

### Example

Suppose an employee's laptop has been infected with malware.

One possible containment action is to isolate the laptop from the network.

However, containment is not always as simple as:

> "Disconnect everything."

### Why Containment Requires Investigation

Immediately disconnecting or shutting down a system can sometimes cause problems.

For example, doing so might:

- Destroy valuable volatile evidence.
    
- Interrupt an attack that investigators are monitoring.
    
- Prevent investigators from understanding what the attacker was doing.
    
- Cause business disruption.
    
- Alert the attacker that they have been discovered.
    

Therefore, containment strategies should match:

- The type of attack.
    
- The affected systems.
    
- The severity of the incident.
    
- The potential damage.
    
- The organization's operational requirements.
    
- The evidence that needs to be preserved.
    

### Key Idea

There is no universal containment action that works for every incident.

The correct response depends on the situation.

# 6. Eradication

**Eradication** is the process of removing the root cause of the security incident and ensuring, with a high degree of confidence, that the threat has been eliminated.

The goal is not simply to make the visible symptoms disappear.

The organization needs to understand **how the attacker gained access and what allowed them to remain in the environment**.

### Possible Eradication Activities

Eradication may include:

- Removing malware.
    
- Using anti-malware tools.
    
- Reimaging compromised systems.
    
- Applying security patches.
    
- Removing malicious software.
    
- Deleting malicious accounts.
    
- Resetting compromised passwords.
    
- Revoking stolen credentials.
    
- Removing persistence mechanisms.
    
- Fixing the vulnerability that allowed the attack.
    

### Example

Suppose an attacker gained access because a server was running vulnerable software.

Simply removing the attacker's malware would not completely solve the problem.

The attacker might return because the original vulnerability still exists.

A better response would be:

1. Remove the malicious software.
    
2. Identify the vulnerability.
    
3. Patch the vulnerable software.
    
4. Investigate whether other systems have the same vulnerability.
    
5. Check for additional attacker access.
    
6. Reset compromised credentials if necessary.
    
7. Verify that the attacker no longer has access.
    

### Key Idea

> **Eradication means removing the cause of the compromise, not just cleaning up the visible damage.**

# 7. Recovery

After the threat has been removed, the organization can begin **recovery**.

The goal is to restore normal business operations as quickly and safely as possible.

Before recovery begins, the organization should have confidence that the attacker has been removed from the environment.

Recovery may involve:

- Restoring systems from trusted backups.
    
- Rebuilding compromised systems.
    
- Restoring services.
    
- Reconnecting systems to the network.
    
- Verifying system configurations.
    
- Monitoring systems for additional suspicious activity.
    
- Confirming that systems are functioning normally.
    

### Known Good Configuration

A major concept during recovery is restoring systems to a **known good configuration**.

This means returning a system to a state that is believed to be:

- Secure.
    
- Trusted.
    
- Correctly configured.
    
- Free from the identified compromise.
    

### Example

If a web server was compromised, the organization might:

1. Rebuild the server.
    
2. Apply the latest security patches.
    
3. Restore the required application.
    
4. Restore clean configuration files.
    
5. Verify security controls.
    
6. Monitor the server.
    
7. Return it to production.
    

# 8. Lessons Learned

After the incident has been resolved, the organization should not simply forget about it.

The final step is to determine:

> **What can we learn from what happened?**

This is known as **Lessons Learned**.

The organization can examine:

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
    

### Why Lessons Learned Matters

Lessons learned can help an organization improve its security.

For example, if an attacker entered through an unpatched server, the organization might improve its patch management process.

If the attacker remained undetected because important logs were missing, the organization might improve its logging and monitoring.

Therefore:

> **An incident should not only be something an organization recovers from. It should also be an opportunity to improve.**

# 9. The Six Incident Response Steps at a Glance

|Step|Main Goal|
|---|---|
|**Preparation**|Get ready before an incident occurs.|
|**Identification**|Determine whether an incident occurred and understand its scope.|
|**Containment**|Prevent the threat from spreading or causing additional damage.|
|**Eradication**|Remove the root cause and eliminate the attacker's access.|
|**Recovery**|Restore systems and normal business operations.|
|**Lessons Learned**|Learn from the incident and improve security.|

### Easy Way to Remember the Process

Think of it as:

**Prepare → Identify → Contain → Eradicate → Recover → Learn**

# 10. Why the "Art of Investigation"?

The previous steps show something important:

**Containment, eradication, and recovery all depend on correctly identifying and understanding the problem first.**

You cannot properly contain an attack if you do not understand what is happening.

You cannot properly eradicate an attacker if you do not know how they gained access or what systems they compromised.

You cannot safely recover if you do not know whether the attacker is still present.

Therefore, **investigation is the foundation of effective incident response**.


## There Is No Single Correct Investigation Method

There is no single tool, methodology, or procedure that can answer every investigation question.

Cybersecurity incidents can be extremely different from one another.

For example:

- A phishing attack is different from ransomware.
    
- Ransomware is different from insider activity.
    
- A compromised web server is different from a stolen account.
    
- A network intrusion is different from data exfiltration.
    

Because of this, analysts need to combine:

- Different security tools.
    
- Different investigative methodologies.
    
- Critical thinking.
    
- Technical knowledge.
    
- Experience.
    
- Logical reasoning.
    
- Sometimes even intuition or instinct.
    

The analyst must adapt their investigation to the situation.

# 11. The Five Ws of an Investigation

A good investigation attempts to build a complete picture of what happened.

One useful way to think about an investigation is to determine:

- **Who** was responsible?
    
- **What** happened?
    
- **When** did it happen?
    
- **Where** did it happen?
    
- **Why** did it happen?
    

These questions help the analyst move beyond simply saying:

> "There was a suspicious alert."

Instead, the analyst should try to understand the entire story behind the alert.

### Example

Instead of reporting:

> "A suspicious login occurred."

A stronger investigation might determine:

> An attacker used compromised credentials to log into a server from an unusual IP address at 2:13 AM, accessed sensitive files, and then attempted to create another account for persistence.

That provides much more useful information for the organization.

# 12. Building Your Own Critical Thinking Process

During an investigation or threat-hunting activity, analysts should repeatedly use a **critical thinking process**.

The idea is to continuously examine the available evidence, form conclusions, ask new questions, and then investigate those questions.

A simplified process looks like:

**Observe → Question → Investigate → Analyze → Form a conclusion → Look for more evidence**

Then repeat the process until you have a sufficiently complete picture.

### Why Critical Thinking Matters

Security alerts rarely tell you the entire story.

An alert might only tell you:

> "A suspicious PowerShell command was executed."

The analyst then needs to ask:

- Who executed it?
    
- Which machine executed it?
    
- Why was PowerShell being used?
    
- What command was executed?
    
- Was the command malicious?
    
- Where did the command come from?
    
- What happened immediately afterward?
    
- Did the process connect to another system?
    
- Was data accessed or stolen?
    

This is why investigation is more than simply reading alerts.

# 13. Starting an Investigation

A **Security Operations Center (SOC)** usually has security systems continuously monitoring the organization's environment.

Detection engineers create **detection rules** and **correlation searches** that examine available logs and search for suspicious behavior.

One common technology used for this purpose is a **SIEM**.

### SIEM

**SIEM** stands for **Security Information and Event Management**.

A SIEM collects and analyzes security-related logs and events from different systems.

These may include:

- Servers
    
- Workstations
    
- Firewalls
    
- Network devices
    
- Applications
    
- Authentication systems
    
- Security tools
    
- Cloud services
    

The SIEM can then search this data for patterns that may indicate suspicious activity.

# 14. From Detection to Investigation

The general process can look like this:

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

Different security tools may use different names and formats for their detections.

For example, a detection could generate:

- An **alert**
    
- A **ticket**
    
- A **notable event**
    
- A security finding
    

For simplicity, these can be referred to as **findings**.

# 15. What Is a Finding?

A **finding** is an indication generated by a security system that something potentially suspicious or important has occurred.

A finding does **not automatically mean that an attack happened**.

This distinction is extremely important.

For example:

> A user logs in from an unusual country.

That could be:

- A legitimate user traveling.
    
- A VPN connection.
    
- A misconfigured system.
    
- A stolen account.
    

The finding tells the analyst:

> "Something deserves attention."

The investigation determines what actually happened.

# 16. Triage

**Triage** is the process of reviewing findings and determining what they mean and what should happen next.

The analyst investigates the finding and decides whether it should be:

- Closed because it is harmless.
    
- Marked as a **false positive**.
    
- Investigated further.
    
- Escalated as a confirmed incident.
    

### Why Triage Is Important

SOC analysts may receive many findings at the same time.

They cannot investigate every event with the same level of attention.

Therefore, they need to quickly determine:

> **Which findings are actually important?**

This requires prioritization.


# 17. True Positive vs. False Positive

One of the first things an analyst often needs to determine is whether a finding is a **True Positive** or a **False Positive**.

### True Positive

A **True Positive** occurs when a security detection correctly identifies genuine suspicious or malicious activity.

Example:

> A detection reports that a user account executed a known malicious command, and investigation confirms that the activity was performed by an attacker.

The alert was correct.

### False Positive

A **False Positive** occurs when a security detection reports suspicious activity, but investigation shows that the activity was actually legitimate or harmless.

Example:

> A detection flags a login as suspicious because it came from an unusual location, but the user was legitimately traveling and using a corporate VPN.

The alert was triggered, but there was no attack.

### Important Distinction

**Alert ≠ Incident**

An alert is an indication that something deserves investigation.

An incident is a confirmed security event that requires a security response.


# 18. The Five Questions to Ask During an Investigation

There are five core questions that can help guide an investigation.

## 1. Was this an actual attack?

First, determine whether the suspicious activity was actually malicious.

Ask:

- Is the activity legitimate?
    
- Is there evidence of malicious behavior?
    
- Was the detection triggered incorrectly?
    
- Can the activity be explained by normal business operations?
    

This helps distinguish a **true positive** from a **false positive**.

## 2. Was the attack successful?

If an attack actually occurred, determine whether the attacker achieved their objective.

For example:

- Did they successfully authenticate?
    
- Did they execute malicious code?
    
- Did they gain unauthorized access?
    
- Did they steal credentials?
    
- Did they access sensitive information?
    
- Did they establish persistence?
    

An attempted attack and a successful attack are not necessarily the same thing.

### Example

An attacker might attempt to exploit a vulnerable server but fail.

That is very different from successfully exploiting the server and gaining administrator access.

## 3. What assets were compromised?

Next, determine which systems or resources were affected.

Potential assets include:

- Workstations
    
- Servers
    
- Databases
    
- User accounts
    
- Cloud resources
    
- Network devices
    
- Applications
    
- Sensitive files
    
- Credentials
    

This helps determine the **scope of the incident**.

### Example

If one workstation was compromised, the incident may have a limited scope.

If the attacker moved from that workstation to a domain controller and accessed the organization's database servers, the scope is much larger.

## 4. What activities did the attacker carry out?

Once you know the affected assets, investigate what the attacker actually did.

You may need to determine whether they:

- Executed commands.
    
- Created accounts.
    
- Stole credentials.
    
- Installed malware.
    
- Modified files.
    
- Changed configurations.
    
- Moved laterally.
    
- Accessed sensitive information.
    
- Exfiltrated data.
    
- Established persistence.
    
- Attempted to hide their activity.
    

This helps reconstruct the **attack timeline** and understand the attacker's behavior.

## 5. How should my organization respond?

Finally, use everything discovered during the investigation to determine the appropriate response.

Depending on the incident, the organization might need to:

- Isolate affected systems.
    
- Disable compromised accounts.
    
- Reset passwords.
    
- Remove malware.
    
- Patch vulnerabilities.
    
- Restore systems.
    
- Block malicious IP addresses or domains.
    
- Monitor additional systems.
    
- Escalate the incident.
    
- Notify appropriate stakeholders.
    
- Improve security controls.
    

The correct response depends on what the investigation discovered.

# 19. The Five Questions as an Investigation Framework

These five questions can be viewed as a simple investigation roadmap:

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

They help turn a vague alert into a structured investigation.

### The Bigger Picture

The questions move from:

**"Is something wrong?"**

to:

**"What happened?"**

to:

**"How bad is it?"**

to:

**"What did the attacker do?"**

to:

**"What should we do now?"**

That is essentially the core of security investigation.

# 20. Taking Good Investigation Notes

Good note-taking is an important part of cybersecurity investigations.

An investigation can involve a large amount of information, and analysts may spend hours or even days working through evidence.

Without good notes, it is easy to:

- Forget what you already checked.
    
- Repeat the same investigation steps.
    
- Lose important evidence or observations.
    
- Forget why you reached a particular conclusion.
    
- Have difficulty explaining the incident to another analyst.
    
- Make mistakes when creating the final incident report.
    

### What Should You Record?

During an investigation, keep track of important details such as:

- What you observed.
    
- When you observed it.
    
- Which systems you investigated.
    
- Which users were involved.
    
- Which IP addresses were involved.
    
- Relevant timestamps.
    
- Important log entries.
    
- Commands or searches you performed.
    
- Evidence you discovered.
    
- Hypotheses you considered.
    
- Conclusions you reached.
    
- Actions that were taken.
    
- Questions that still need to be answered.
    

### Example Investigation Note

Instead of writing:

> "Checked logs. Looks suspicious."

A useful investigation note would be closer to:

> **14:32** — Reviewed authentication logs for the affected server. Found a successful login for the `admin` account from an unfamiliar external IP address. The login occurred outside the user's normal working hours. Further investigation is required to determine whether the account was compromised.

The second note is much more useful because another analyst can understand **what was checked, what was discovered, and what needs to happen next**.


# 21. Key Concepts to Remember

|Concept|Simple Explanation|
|---|---|
|**Investigation**|The process of examining evidence to understand what happened during a security event.|
|**Incident Response**|The process an organization follows to detect, contain, remove, and recover from security incidents.|
|**Preparation**|Getting the organization ready before an incident occurs.|
|**Identification**|Determining whether a security incident occurred and understanding its scope.|
|**Containment**|Preventing the threat from spreading or causing additional damage.|
|**Eradication**|Removing the attacker, malware, vulnerability, or other root cause of the incident.|
|**Recovery**|Returning systems and business operations to a trusted state.|
|**Lessons Learned**|Reviewing the incident to improve future security and response.|
|**SIEM**|A platform that collects and analyzes security logs and events.|
|**Finding**|A security detection indicating that something potentially suspicious occurred.|
|**Triage**|Reviewing findings and deciding their importance and appropriate next action.|
|**True Positive**|A detection that correctly identifies real malicious or suspicious activity.|
|**False Positive**|A detection that appears suspicious but is actually legitimate or harmless.|
|**Critical Thinking**|Continuously questioning evidence and testing conclusions during an investigation.|
|**Scope**|The overall extent of an incident, including affected systems, accounts, data, and resources.|
|**Evidence**|Information that can help an investigator understand and prove what happened.|

# 22. Core Takeaways

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
    
- The five investigation questions provide a useful framework:
    
    1. Was this an actual attack?
        
    2. Was the attack successful?
        
    3. What assets were compromised?
        
    4. What activities did the attacker carry out?
        
    5. How should the organization respond?
        
- **Good notes are part of good investigation.** They make investigations easier to continue, review, explain, and report.