# **Microsoft Sentinel Introduction : TryHackMe Write-up**

## **Room Information**

* **Room Name:** Microsoft Sentinel Introduction  
* **Platform:** TryHackMe  
* **Category:** SIEM / SOC / Cloud Security  
* **Difficulty:** Beginner  
* **Link:** [https://tryhackme.com/room/sentinelintroduction](https://tryhackme.com/room/sentinelintroduction)

---

# **Introduction**

Security teams generate massive amounts of security logs every day, making it impossible to manually analyze every event. Security Information and Event Management (SIEM) solutions help collect, correlate, analyze, and visualize security data from multiple sources to detect potential threats.

This room introduces Microsoft Sentinel, Microsoft's cloud-native SIEM and SOAR platform built on Azure. It explores how Sentinel collects security logs, enables threat detection, supports incident investigation, and automates security operations through analytics rules, workbooks, and playbooks.

By completing this room, learners gain a foundational understanding of how modern SOC teams use Microsoft Sentinel to monitor enterprise environments.

---

# **Learning Objectives**

By completing this room, I learned:

* What Microsoft Sentinel is.  
* The core architecture of Sentinel.  
* How data connectors ingest logs.  
* The purpose of Log Analytics Workspace.  
* How analytics rules generate incidents.  
* How SOC analysts investigate alerts.  
* Basic automation using playbooks.  
* The role of Sentinel in modern Security Operations Centers.

---

# **Task 1: Introduction to Microsoft Sentinel**

## **Overview**

This task introduces Microsoft Sentinel and explains its role within Microsoft's cloud security ecosystem.

Microsoft Sentinel is a cloud-native SIEM and SOAR platform that enables organizations to:

* Collect security logs  
* Detect threats  
* Investigate incidents  
* Automate security responses

Unlike traditional SIEM platforms, Sentinel is fully cloud-based and scales automatically with organizational needs.

### **Key Features**

* Cloud-native architecture  
* Centralized log management  
* Threat detection  
* Incident investigation  
* Automation  
* Threat intelligence integration

### **Key Takeaway**

Microsoft Sentinel enables SOC analysts to monitor and investigate security events from a single platform.

---

# **Task 2: Sentinel Architecture**

## **Overview**

This section explains how Microsoft Sentinel processes security data.

### **Core Components**

#### **Data Connectors**

Used to collect logs from:

* Windows  
* Linux  
* Azure  
* Microsoft 365  
* AWS  
* Firewalls  
* Endpoint Security Products  
* Third-party solutions

#### **Log Analytics Workspace**

The central repository where all collected logs are stored.

It enables:

* Log searches  
* Threat hunting  
* Alert generation  
* Investigation

#### **Analytics Rules**

Used to detect suspicious behavior.

Rules analyze incoming logs and generate alerts when conditions are met.

#### **Incidents**

Multiple alerts can be grouped together into a single incident to simplify investigations.

---

# **Task 3: Data Collection**

## **Overview**

Before Sentinel can detect threats, it must ingest security logs.

### **Common Data Sources**

* Azure Activity Logs  
* Windows Event Logs  
* Microsoft Defender  
* Microsoft Entra ID  
* Office 365  
* Firewall Logs  
* Endpoint Detection & Response (EDR)  
* Custom Applications

### **Why Data Collection Matters**

A SIEM is only as effective as the data it receives.

Poor visibility leads to missed detections.

---

# **Task 4: Analytics Rules**

## **Overview**

Analytics Rules are responsible for identifying suspicious activity.

### **Types of Rules**

#### **Scheduled Rules**

Run periodically against collected logs.

#### **Near Real-Time Rules**

Detect events almost immediately after ingestion.

#### **Microsoft Security Templates**

Prebuilt detection rules provided by Microsoft.

### **Typical Detection Examples**

* Multiple failed logins  
* Privilege escalation  
* Malware detections  
* Suspicious PowerShell activity  
* Impossible travel logins

---

# **Task 5: Investigating Incidents**

## **Overview**

Once an analytics rule triggers, Sentinel creates an alert or incident.

SOC analysts investigate by reviewing:

* Timeline  
* Affected users  
* Devices  
* IP addresses  
* Authentication logs  
* Related alerts

### **Investigation Workflow**

1. Open Incident  
2. Review Alert Details  
3. Identify Impacted Assets  
4. Examine Evidence  
5. Determine Severity  
6. Escalate or Close

---

# **Task 6: Workbooks**

## **Overview**

Workbooks provide visual dashboards for security monitoring.

Examples include:

* Authentication Trends  
* Failed Login Attempts  
* Malware Activity  
* Network Traffic  
* Security Incidents  
* Threat Intelligence

### **Benefits**

* Better visibility  
* Faster investigations  
* Executive reporting

---

# **Task 7: Automation with Playbooks**

## **Overview**

Sentinel integrates with Microsoft Logic Apps to automate repetitive tasks.

### **Common Playbook Actions**

* Send email notifications  
* Create ServiceNow tickets  
* Block malicious IP addresses  
* Disable compromised accounts  
* Notify SOC teams  
* Trigger response workflows

Automation reduces analyst workload and speeds up incident response.

---

# **Task 8: Threat Hunting**

## **Overview**

Threat Hunting involves proactively searching for malicious activity.

Sentinel uses Kusto Query Language (KQL) for log analysis.

Example hunting activities include:

* Failed login searches  
* Suspicious PowerShell execution  
* Malware detections  
* Lateral movement  
* Privilege escalation

### **Why Threat Hunting Matters**

Not every attack generates an alert.

Threat hunting helps analysts identify hidden threats.

---

# **Room Answers**

***What security unit is responsible for protecting the organization against security threats?***  
***Security Operations Center***

***Generally, which level of SOC Analyst is responsible for responding to incidents?***  
***SOC Level 2 Analyst***

***Besides monitoring, what else do SOC Level 1 Analysts spend the majority of their time with?***  
***Triage***

***Microsoft Sentinel is a combination of two security concepts, namely SIEM and which other one?***  
***SOAR***

***Creating security alerts and incidents is part of which security concept?***  
***SIEM***

***By means of how many pillars does Microsoft Sentinel help us to perform security operations?***  
***4***

***What is used to ingest data into Sentinel?***  
***Data connectors***

***Where are the ingested logs stored for further correlation and analysis?***  
***Log analytics workspaces***

***Workbooks are essentially \_\_\_\_\_\_\_ used for visualization.***  
***Dashboards***

***When SOC teams are flooded with security alerts and incidents, this is called?***  
***Alert fatigue***

***In Microsoft Sentinel, automation is done via automated workflows, known as?***  
***Playbooks***

***The output of running Analytics rules includes security alerts and?***  
***Incidents***

***Organizations use Microsoft Sentinel mainly because they need to \_\_\_\_\_\_\_ their cloud infrastructure.***  
***Monitor***

***With Microsoft Sentinel, there is no need for server provisioning. This means it is?***  
***Cloud-native***

---

# **Key Concepts Learned**

### **Microsoft Sentinel**

A cloud-native SIEM and SOAR platform used for security monitoring and incident response.

### **Data Connectors**

Used to ingest security logs from multiple environments.

### **Log Analytics Workspace**

Stores and indexes collected security data.

### **Analytics Rules**

Automatically detect suspicious activity based on predefined logic.

### **Incidents**

Collections of related alerts grouped for investigation.

### **Workbooks**

Interactive dashboards for visualizing security data.

### **Playbooks**

Automated workflows built using Microsoft Logic Apps.

### **Threat Hunting**

Proactively searching logs for indicators of malicious activity.

---

# **Skills Gained**

* Microsoft Sentinel Navigation  
* SIEM Fundamentals  
* Security Monitoring  
* Incident Investigation  
* Log Analysis  
* Analytics Rule Understanding  
* SOC Workflow  
* Cloud Security Monitoring

---

# **Real-World Relevance**

The concepts covered in this room are directly applicable to roles such as:

* SOC Analyst (L1/L2)  
* Security Operations Engineer  
* Cloud Security Analyst  
* Incident Responder  
* Threat Hunter  
* Security Engineer

Microsoft Sentinel is widely adopted across enterprise environments, making familiarity with its architecture and workflows a valuable skill for cybersecurity professionals.

---

# **Final Thoughts**

This room provides an excellent introduction to Microsoft Sentinel and demonstrates how modern cloud-native SIEM platforms support security monitoring, threat detection, incident investigation, and automated response.

The most valuable takeaway was understanding how logs flow from various data sources into Sentinel, where they are analyzed using analytics rules and transformed into actionable incidents. The hands-on activities also reinforced how SOC analysts investigate alerts and use dashboards and automation to improve operational efficiency.

---

**Room Status:** Completed ✅

**Skills Learned:** Microsoft Sentinel, SIEM, SOAR, Log Analytics, Analytics Rules, Incident Investigation, Threat Hunting, KQL, Cloud Security

