# **KQL (Kusto Query Language) Introduction : TryHackMe Write-up**

## **Room Information**

* **Room Name:** KQL (Kusto Query Language) Introduction  
* **Platform:** TryHackMe  
* **Category:** SIEM / Microsoft Sentinel / Log Analysis  
* **Difficulty:** Beginner  
* **Link:** [https://tryhackme.com/room/kqlkustointroduction](https://tryhackme.com/room/kqlkustointroduction)

---

# **Introduction**

Modern Security Operations Centers (SOCs) generate massive amounts of log data every day. Security analysts rely on powerful query languages to search, filter, and investigate this data efficiently. One of the most widely used query languages in Microsoft's security ecosystem is **Kusto Query Language (KQL)**.

This room introduces the fundamentals of KQL and demonstrates how it is used within Microsoft Sentinel, Azure Monitor, Microsoft Defender, and Log Analytics Workspace to investigate security events.

By learning KQL, security analysts can quickly locate suspicious activity, identify Indicators of Compromise (IOCs), and perform effective threat hunting.

---

# **Learning Objectives**

By completing this room, I learned:

* What Kusto Query Language (KQL) is.  
* Basic KQL query syntax.  
* How to search and filter log data.  
* Common KQL operators.  
* Data projection and sorting.  
* Aggregating log information.  
* Writing simple threat hunting queries.  
* How KQL supports Microsoft Sentinel investigations.

---

# **Task 1: Introduction to KQL**

## **Overview**

The room begins by introducing Kusto Query Language (KQL), Microsoft's read-only query language designed for exploring large datasets efficiently.

KQL is commonly used in:

* Microsoft Sentinel  
* Azure Monitor  
* Log Analytics Workspace  
* Microsoft Defender XDR  
* Azure Data Explorer

Unlike SQL, KQL is optimized for fast log searching and analytical queries.

### **Why KQL Matters**

Security analysts use KQL to:

* Search logs  
* Investigate incidents  
* Hunt for threats  
* Detect suspicious behavior  
* Analyze security events

### **Key Takeaway**

KQL enables analysts to rapidly investigate security data without modifying the underlying logs.

---

# **Task 2: Overview of Microsoft Sentinel**

## **Overview**

All KQL queries begin with a table.

Tables contain collected security data from various sources.

Examples include:

* SecurityEvent  
* SigninLogs  
* DeviceEvents  
* DeviceNetworkEvents  
* Heartbeat  
* Syslog

## Microsoft Sentinel Explained

MS Sentinel is a cloud-native Security Information and Event Management (SIEM) solution enabling security administrators to better detect, investigate, and respond to security threats across their enterprise environment. Sentinel is built on top of Azure, providing a centralized platform for security monitoring, log collection, threat detection, response, and investigation. It is not only a SIEM solution but also a Security Orchestration, Automation, and Response (SOAR) solution, which enhances its capabilities.

#### Integration With Microsoft Services 

Microsoft Entra ID  
Microsoft Defender   
Azure Logic Apps  
Azure Monitor 

#### Integration With Third-Party Services : 

Syslog integration   
REST API integration 

Each table stores a different category of information.

### **Example Structure**

A table typically contains:

* Timestamp  
* Device Name  
* User  
* Event ID  
* IP Address  
* Process Name

Understanding table structure is the first step in writing effective queries.

---

# **Task 3: What is KQL**

Kusto Query Language, also KQL is more than just a syntax. Within the context of Microsoft Sentinel, it is a tool for discovering and investigating suspicious activities. With each query, you can sift through large amounts of logs, detect subtle traces of cyber threats, and connect the dots to get actionable insight from the logs across your digital estate. 

A simple description of KQL would be that it is a:

1. Security analysis language: Used to filter, search, and analyze security logs and events.  
2. Powerful and flexible tool: Used to run simple and complex queries to extract detailed security insights.  
3. Tool for large datasets: Optimized for handling massive amounts of security logs.  
4. Tool built-in for Microsoft Sentinel: Seamlessly integrated for data exploration and threat hunting.  
5. Tool used in other Microsoft services: Such as Azure Data Explorer, Log Analytics, Azure Monitor, and Azure Sentinel.

### **Practical Use**

Filtering dramatically reduces the number of events analysts need to review.

---

# **Task 4: KQL Concepts in Microsoft Sentinel**

## **Overview**

KQL provides operators that control how results are displayed.

### **project**

Displays only selected columns.

Benefits:

* Cleaner output  
* Faster investigations  
* Easier reporting

## Functions and Operators

Functions and operators are symbols or keywords that carry out operations, such as performing specific tasks or calculations on ingested logs. They are used to manipulate, aggregate, filter, transform, or analyze data and are usually invoked by name or customized parameters.

Examples  
count(), sum(), avg(), where(), parse()  
\== \- (equal to)  
\!= \- (not equal to)  
\< \- (less than)  
render  
summarize  
| \- (Pipeline)

### **Common Operators**

#### **where**

Filters records matching a condition.

Example use cases:

* Failed logins  
* Specific IP addresses  
* Particular users  
* Event IDs

#### **contains**

Searches for partial text matches.

#### **has**

Searches for complete words.

#### **startswith**

Finds values beginning with a specific string.

#### **endswith**

Matches values ending with specified text.

---

# **Task 5: KQL Statement Structure**

The structure of a KQL statement consists of multiple components, allowing you to retrieve, manipulate, and analyze security logs effectively. You start with a data source and navigate through a set of operators bound together using the pipe | delimiter. 

Below is a typical example of a query combining multiple query components:

**SecurityEvent**  
**| where TimeGenerated \> ago(1d)**  
**| summarize EventCount \= count() by Computer**  
**| order by EventCount desc | limit 10**

Explanation

* Data source: The data source specifies the table from which you want to retrieve data.  
  * SecurityEvent- Specifies the table from which data will be retrieved.  
* Conditions: They are used to perform specific actions on data.  
  * | where TimeGenerated \> ago(1d) \- Filters the data to include only events that occurred within the last 24 hours ago(1d)). This ensures that only recent events are analyzed.  
  * | summarize EventCount \= count() by Computer \- Aggregates the filtered events by the Computer column and counts the number of events for each device.  
* Output: This defines how you want to view the output result.  
  * | order by EventCount desc \- Sorts the aggregated data by the EventCount column in descending order desc).  
  * | limit 10 \- Limits the output to the top 10 devices with the highest number of security events.

---

# **Task 6: KQL Use Cases**

## Real-Life Example

* Investigating security incidents: You can use KQL to analyze security alerts, identify the root cause of incidents, and investigate attack timelines by querying relevant logs.  
* Hunting for malware: KQL queries can be used to detect anomalies and search for suspicious malware-related activities, such as malicious file downloads, unusual registry changes, or network manipulations.  
* Detecting lateral movement: KQL can identify suspicious user logins from different devices or locations, which may indicate unauthorized access and lateral movement within your network.  
* Monitoring user activity: As a security analyst, you can review login attempts, access patterns, and privileged user activity using KQL queries, which can help detect account misuse or compromises.  
* Security operations automation: Security admins can automate security operations and incident response by integrating KQL queries into workflows and triggering alerts, notifications, or remedial actions based on query results.  
* Alerting: In Microsoft Sentinel, custom alerts can be created using KQL queries to inform you of possible security events by specifying particular criteria in the query. Also, an alert rule can be created within KQL from a query.

---

# **Room Answers**

***In addition to being a SIEM solution, what else is Microsoft Sentinel? (use the abbreviation)***  
***SOAR***

***How does MS Sentinel support other security solutions that are not included in the built-in connectors?***   
***REST API Integration***

***What initial service was KQL created for?***  
***Azure Data Explorer***

***Analyze the example query from the task. How many computers will the query return?***  
***10***

***What table is the example query retrieving its data from?***  
***Heartbeat***

***What operator can be used to output results in graphical form?***  
***Render***

***What operator can be used to filter a specified table based on specified conditions?***  
***Where***

***What user account name was queried in our second example query above?***  
***JBOX00$***

***What is the name of the table queried in our example query?***  
***SecurityEvent***

***Analyze the example query from the task. What does the query aggregate per computer?***  
***EventCount***

***What are we searching for in the SecurityEvent table on the first query?***  
***failed login attempts***

***Which operator was used on the second query to streamline our search to a range of user accounts from the TargetUserName column?***   
***Contains***

---

# **Common KQL Operators**

| Operator | Purpose |
| ----- | ----- |
| where | Filter records |
| project | Select columns |
| extend | Create calculated columns |
| summarize | Aggregate data |
| sort by | Sort results |
| top | Return highest values |
| take | Limit output |
| distinct | Display unique values |
| count | Count records |
| ago | Filter by time |

---

# **Key Concepts Learned**

### **Kusto Query Language (KQL)**

Microsoft's query language for analyzing security logs.

### **Tables**

Containers that store security events.

### **Filtering**

Selecting only relevant records.

### **Projection**

Displaying required columns.

### **Aggregation**

Summarizing large datasets.

### **Sorting**

Ordering results for easier analysis.

### **Threat Hunting**

Using queries to identify suspicious activity.

### **Log Analytics**

Searching and analyzing enterprise security logs.

---

# **Skills Gained**

* KQL Fundamentals  
* Log Analysis  
* Security Event Investigation  
* Microsoft Sentinel Queries  
* Threat Hunting  
* Data Filtering  
* Query Optimization  
* SOC Investigation Techniques

---

# **Real-World Relevance**

KQL is one of the most important skills for security professionals working within the Microsoft security ecosystem.

It is commonly used by:

* SOC Analysts  
* Threat Hunters  
* Incident Responders  
* Detection Engineers  
* Security Engineers  
* Cloud Security Analysts

Strong KQL skills significantly improve an analyst's ability to investigate alerts, detect suspicious activity, and respond to incidents efficiently.

---

# **Final Thoughts**

This room provides an excellent introduction to Kusto Query Language and demonstrates why it is such an essential tool for modern SOC operations.

The most valuable takeaway was understanding how a few simple KQL operators can transform large volumes of raw log data into meaningful information that supports incident investigations and proactive threat hunting.

---

**Room Status:** Completed ✅

**Skills Learned:** KQL, Microsoft Sentinel, Log Analytics, Threat Hunting, Log Filtering, Data Aggregation, Security Investigation, Azure Security

