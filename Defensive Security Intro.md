# **TryHackMe Write-up: Defensive Security Intro**

## **Room Information**

* **Room Name:** Defensive Security Intro  
* **Platform:** TryHackMe  
* **Category:** Defensive Security  
* **Difficulty:** Beginner  
* **Link:** [https://tryhackme.com/room/defensivesecurityintro](https://tryhackme.com/room/defensivesecurityintro)

---

# **Introduction**

Defensive security is all about protecting systems, networks, and data from cyber threats. While offensive security focuses on finding and exploiting vulnerabilities, defensive security focuses on preventing attacks, detecting malicious activity, and responding effectively when incidents occur..

# **Learning Objectives**

By completing this room, I learned:

* The role of defensive security teams.  
* The responsibilities of a Security Operations Center (SOC).  
* The fundamentals of Threat Intelligence.  
* What Digital Forensics and Incident Response (DFIR) involves.  
* Basic malware analysis concepts.  
* How SIEM tools help security analysts detect threats.  
* How defensive security works in practice.

---

# **Task 1: Introduction to Defensive Security**

The room begins by explaining the difference between offensive and defensive security.

### **Offensive Security**

Offensive security focuses on finding and exploiting vulnerabilities before attackers do.

Examples include:

* Penetration Testing  
* Red Teaming  
* Vulnerability Assessments

### **Defensive Security**

Defensive security focuses on:

1. Preventing intrusions  
2. Detecting attacks  
3. Responding to incidents

This is commonly referred to as **Blue Teaming**.

---

## **Core Responsibilities of Defensive Security**

### **Cyber Security Awareness**

Users are often the weakest link in security.

Organizations train employees to recognize:

* Phishing attacks  
* Social engineering attempts  
* Suspicious emails  
* Unsafe browsing habits

### **Asset Management**

Security teams must know:

* What systems exist  
* Which devices are connected  
* What needs protection

You cannot secure assets that you do not know exist.

### **Patching and Updates**

Keeping systems updated helps eliminate known vulnerabilities before attackers can exploit them.

### **Preventative Security Controls**

Examples include:

* Firewalls  
* Intrusion Prevention Systems (IPS)

These controls help stop malicious traffic before it reaches critical systems.

### **Logging and Monitoring**

Organizations continuously monitor systems and networks for suspicious activity.

Logs become one of the most valuable sources of information during investigations.

---

# **Task 2: Areas of Defensive Security**

This section introduces several specialized areas within defensive security.

---

## **Security Operations Center (SOC)**

A Security Operations Center (SOC) is a team of cybersecurity professionals responsible for monitoring systems and networks for malicious activity.

SOC analysts continuously watch for:

### **Vulnerabilities**

New vulnerabilities are discovered every day.

SOC teams track:

* CVEs  
* Vendor advisories  
* Security patches

### **Policy Violations**

Examples include:

* Uploading confidential files to unauthorized services  
* Using prohibited software  
* Violating company security policies

### **Unauthorized Activity**

SOC teams investigate suspicious logins, account misuse, and unusual behavior.

### **Network Intrusions**

Even well-protected organizations may experience breaches.

SOC analysts work to detect intrusions as quickly as possible to minimize damage.

---

## **Threat Intelligence**

Threat Intelligence involves gathering and analyzing information about potential adversaries.

The goal is to understand:

* Who the attackers are  
* What motivates them  
* How they operate

Threat Intelligence helps organizations move from reactive security to proactive security.

### **Threat Intelligence Process**

1. Data Collection  
2. Data Processing  
3. Analysis  
4. Actionable Recommendations

Information can come from:

* Internal logs  
* Security reports  
* Open-source intelligence  
* Security communities

By understanding attacker tactics, techniques, and procedures (TTPs), organizations can better prepare for future attacks.

---

# **Digital Forensics and Incident Response (DFIR)**

DFIR combines two critical disciplines:

### **Digital Forensics**

Digital forensics focuses on collecting and analyzing evidence after a security incident.

Investigators analyze:

#### **File Systems**

To recover:

* Deleted files  
* Modified files  
* Hidden artifacts

#### **Memory**

Memory analysis can reveal:

* Running malware  
* Active processes  
* Encryption keys

#### **System Logs**

Logs provide detailed records of events occurring on a system.

#### **Network Logs**

Network traffic can reveal:

* Attack sources  
* Communication patterns  
* Data exfiltration attempts

Digital forensics helps answer:

What happened?

How did it happen?

Who was responsible?

---

## **Incident Response**

Incident Response focuses on handling security incidents in an organized manner.

Typical stages include:

### **Preparation**

Establishing tools, procedures, and response plans.

### **Detection and Analysis**

Identifying suspicious activity and determining whether an incident has occurred.

### **Containment, Eradication, and Recovery**

* Stop the attack  
* Remove malicious components  
* Restore normal operations

### **Post-Incident Activity**

Document lessons learned and improve future defenses.

This cycle helps organizations continuously improve their security posture.

---

## **Malware Analysis**

Malware analysis focuses on understanding malicious software.

The room introduces several malware categories.

### **Virus**

A virus attaches itself to legitimate programs and spreads between systems.

### **Worm**

A worm spreads automatically without requiring user interaction.

### **Trojan**

A Trojan disguises itself as legitimate software.

### **Ransomware**

Ransomware encrypts files and demands payment in exchange for restoring access.

Ransomware remains one of the most financially damaging cyber threats facing organizations today.

---

# **Task 3: Practical Example of Defensive Security**

This was the most engaging section of the room.

The room places you in the role of a SOC analyst responsible for protecting a bank.

The organization uses a SIEM platform to aggregate security events from multiple sources.

---

## **What is a SIEM?**

SIEM stands for:

### **Security Information and Event Management**

A SIEM collects and correlates logs from:

* Servers  
* Workstations  
* Firewalls  
* Applications  
* Network devices

The goal is to detect suspicious behavior and generate alerts for analysts.

---

## **Investigation Process**

As a SOC analyst, I followed a typical incident investigation workflow:

### **Step 1: Review Alerts**

The SIEM generated alerts indicating suspicious activity.

### **Step 2: Analyze the Source**

I investigated the suspicious IP address generating the activity.

### **Step 3: Understand the Attack**

The logs revealed URL discovery attempts, indicating that an attacker was trying to locate hidden resources on the website.

This resembles reconnaissance activity often seen before exploitation attempts.

### **Step 4: Contain the Threat**

To stop the attack:

* The malicious IP was blocked.  
* Additional security controls were applied.  
* Monitoring was enhanced.

This demonstrates the "containment" phase of incident response.

---

# **Room Answers**

***What would you call a team of cyber security professionals that monitors a network and its systems for malicious events?***  
***Ans: Security Operations Center***

***What does DFIR stand for?***  
***Ans: Digital Forensics and Incident Response***

***Which kind of malware requires the user to pay money to regain access to their files?***  
***Ans: ransomware***

---

## **Simulating a SIEM**

The prepared simplified, interactive simulation of a SIEM system to provide you with a hands-on experience similar to what cyber security analysts encounter.  
(To start this simulation, please click the "View Site" button below.)

This action will open a "static site" on the right side of your screen. Follow the step-by-step instructions provided within the simulation to navigate through the events and locate the "flag." A flag is a series of characters with a format like this: "THM{RANDOM\_WORDS}". Use this flag to answer questions from lessons here in TryHackMe, like the one below.
<img width="821" height="822" alt="Screenshot 2026-06-08 232905" src="https://github.com/user-attachments/assets/4bbe5c17-2dbf-46b5-a695-9dc06e29e088" />
<img width="760" height="804" alt="Screenshot 2026-06-08 232948" src="https://github.com/user-attachments/assets/92a8a2fb-675c-4f1d-8876-30c73dfc3429" />
<img width="810" height="359" alt="Screenshot 2026-06-08 233026" src="https://github.com/user-attachments/assets/1c6646bc-93c8-48cd-9c50-07b25d29ffe0" />




# 

# **Key Concepts Learned**

### **Blue Team**

The defensive side of cybersecurity responsible for protecting systems.

### **SOC**

The frontline team responsible for monitoring and detecting threats.

### **Threat Intelligence**

Understanding attackers before they attack.

### **DFIR**

Investigating incidents and recovering from attacks.

### **SIEM**

Centralized log collection and threat detection.

### **Malware Analysis**

Understanding malicious software to improve defenses.

---

# **Final Thoughts**

This room serves as an excellent introduction to the world of defensive security. It provides a high-level understanding of the different teams, technologies, and processes that work together to protect organizations from cyber threats.

The practical SOC investigation exercise was particularly valuable because it demonstrated how security analysts use SIEM platforms to investigate suspicious activity, identify attacks, and take action before significant damage occurs.

For anyone interested in becoming a SOC Analyst, Threat Hunter, Incident Responder, or Security Engineer, this room provides a strong foundation for understanding the defensive side of cybersecurity.

---

**Room Status:** Completed ✅

**Skills Learned:** Blue Teaming, SOC Operations, Threat Intelligence, DFIR, Incident Response, SIEM Monitoring, Malware Analysis, Security Monitoring

