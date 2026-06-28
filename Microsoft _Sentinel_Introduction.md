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

# **Task 2: Introduction to Microsoft Sentinel**

What Is Microsoft Sentinel?
Given the above concept definitions, Microsoft Sentinel's own definition becomes a combination of the two. It is essentially a scalable, cloud-native solution that provides the following:

# Security Information and Event Management (SIEM) functionality by:
# * Collecting and querying logs * 
# * Doing correlation or anomaly detection * 
# * Creating alerts and incidents based on findings * 
# Security Orchestration, Automation, and Response (SOAR) functionality by:
# * Defining playbooks * 
# * Automating threat responses *
Microsoft Sentinel also delivers security analytics and threat intelligence across the organization. It's a one-stop-shop and bird's-eye view solution for:

# Attack detection
# Threat visibility
# Proactive hunting
# Threat response

Unlike traditional SIEM platforms, Sentinel is fully cloud-based and scales automatically with organizational needs.
Microsoft Sentinel performs the above actions and enables security operations by means of 4 main pillars:

Collect
Detect
Investigate
Respond
<img width="1178" height="772" alt="{FB51A62A-3B67-46B4-B343-D52E738E5DD7}" src="https://github.com/user-attachments/assets/8c1a4a8b-72ba-4b14-aec9-027c6e76001b" />


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

# **Task 3: How Microsoft Sentinel Works**

# Phase 1: Collect

Data connectors: The first step is to ingest data into Microsoft Sentinel. This is exactly what data connectors are for. There are 100+ connectors to cover all various data sources and scenarios.
Log retention: Once the data has been ingested into Microsoft Sentinel, it must be stored for further correlation and analysis. This log storage mechanism is called Log Analytics workspaces. Data stored in these workspaces can be queried to gain further insights using Kusto Query Language (KQL).
# Phase 2: Detect
Workbooks: Workbooks are essentially dashboards in Microsoft Sentinel used to visualize data. There are many built-in workbooks, and custom ones can also be created by utilizing KQL.
Analytics rules: What good is a bunch of logs and visualizations if we can't gain insights from them? That's why there are Analytics rules. Analytics rules provide proactive analytics so that SOC teams get notified when suspicious things happen. The output of running Analytics rules are security alerts and incidents.
Threat hunting: Reacting to security incidents only after they happen is not good enough. SOC analysts also need to perform proactive threat hunting. Microsoft Sentinel has over 200 built-in threat-hunting queries to support that needle-in-a-haystack job.
# Phase 3: Investigate
Incidents and investigations: Once Analytics rules detect suspicious activities, i.e., once an alert is triggered, security incidents are created for SOC analysts to triage and investigate. Typical incident management activities include:
Changing status
Assigning  for further investigation
Mapping entities to the investigation
Investigating the incident timeline
Deep-dive into investigation details using investigation maps
Recording investigation comments
# Phase 4: Respond
Automation via playbooks: One of the main challenges of a SOC team is alert fatigue. To overcome alert fatigue, automation in security operations is a must. This is done by automated workflows, also known as playbooks, in response to events. By doing so, automated responses can be provided for:
Incident management
Enrichment
Investigation
Remediation


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

---

# **Task 4: When to use Microsoft Sentinel **

hen there is a necessity to monitor cloud and on-premises infrastructures for security. Surely, many security products could be used for this purpose. However, where Microsoft Sentinel separates from the crowd is its ability to enable the majority of SOC teams' tasks from a single pane and with a 360-degree bird's-eye approach.

Microsoft Sentinel serves as a solution for conducting security operations across cloud and on-premises environments. Security operations encompass various tasks such as:

Visualizing log data
Detecting anomalies
Conducting threat hunting
Investigating security incidents
Implementing automated responses to alerts and incidents

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

