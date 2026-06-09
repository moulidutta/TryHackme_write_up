# **TryHackMe \- Nmap write up** 

## **Overview**

The Further Nmap room expanded on the fundamentals of Nmap by introducing advanced scan types, the Nmap Scripting Engine (NSE), service enumeration techniques, and firewall evasion concepts. The room demonstrated how different scan techniques interact with target systems and how scan selection can impact both speed and stealth during reconnaissance.

## **Objectives**

* Understand advanced Nmap functionality.  
* Learn the differences between TCP, SYN, and UDP scans.  
* Explore NULL, FIN, and Xmas scans.  
* Use the Nmap Scripting Engine (NSE).  
* Understand timing templates and scan optimization.  
* Learn common firewall evasion techniques.

---

## **Understanding Port Scanning**

Port scanning is a critical component of the reconnaissance phase of a security assessment. By identifying open ports and running services, an analyst can build an attack surface map of a target system.

The room reinforced the importance of enumeration before attempting any exploitation activities.

---

## **Common Nmap Scan Types**

### **TCP Connect Scan (-sT)**

TCP Connect scans perform a complete TCP three-way handshake with the target service.

Example:

nmap \-sT 10.49.139.250

Characteristics:

* Reliable  
* Easy to detect  
* Does not require raw socket privileges

---

### **SYN Scan (-sS)**

Often called a "Half-Open" or "Stealth" scan.

Example:

sudo nmap \-sS 10.49.139.250 

Characteristics:

* Faster than TCP Connect scans  
* Does not complete the full TCP handshake  
* Historically more difficult to detect  
* Commonly used during penetration tests

---

### **UDP Scan (-sU)**

UDP services do not establish sessions like TCP, making them more difficult to enumerate.

Example:

sudo nmap \-sU 10.49.139.250

Characteristics:

* Slower than TCP scanning  
* Useful for identifying DNS, SNMP, TFTP, and other UDP services  
* Responses are often inconsistent

---

## **Advanced Scan Types**

The room introduced three stealth-oriented scan techniques:

### **NULL Scan**

sudo nmap \-sN 10.49.139.250

### **FIN Scan**

sudo nmap \-sF 10.49.139.250

### **Xmas Scan**

sudo nmap \-sX 10.49.139.250

These scans attempt to bypass certain firewall rules by sending packets with unusual flag combinations rather than standard SYN packets.

Key Learning:

Modern IDS and firewall technologies frequently detect these techniques, but understanding them remains valuable when assessing network defenses.

---

## **Service Enumeration**

Nmap can identify versions of services running on discovered ports.

Example:

nmap \-sV 10.49.139.250

Benefits:

* Identifies software versions  
* Assists vulnerability research  
* Helps prioritize investigation efforts
---

## **Aggressive Scan Mode**

The room demonstrated aggressive scanning mode.

Example:
nmap \-A 10.49.139.250

This combines:

* Service Detection  
* OS Detection  
* Traceroute  
* Default Script Scanning

Aggressive mode provides detailed information but generates significantly more network traffic.

---

## **Nmap Scripting Engine (NSE)**

One of Nmap's most powerful features is the Nmap Scripting Engine. The Nmap Scripting Engine (NSE) is an incredibly powerful addition to Nmap, extending its functionality quite considerably. NSE Scripts are written in the Lua programming language, and can be used to do a variety of things: from scanning for vulnerabilities, to automating exploits for them. The NSE is particularly useful for reconnaisance, however, it is well worth bearing in mind how extensive the script library is.

Example:

nmap \--script vuln 10.49.139.250

NSE scripts can perform:

* Service enumeration  
* Vulnerability detection  
* Authentication testing  
* Misconfiguration discovery

The room also introduced searching and managing installed NSE scripts.

---

## **Timing Templates**

Nmap supports timing templates ranging from T0 to T5.

Example:

nmap \-T4 10.49.139.250

Key Observation:

Increasing scan speed can reduce scan duration but may increase noise and reduce accuracy in unstable environments.

---

## **Firewall Evasion Techniques**

The room covered several methods used to bypass common network filtering mechanisms.

### **Disable Host Discovery**

nmap \-Pn 10.49.139.250

This forces Nmap to treat the host as online even when ICMP traffic is blocked.

### **Packet Fragmentation**

nmap \-f 10.49.139.250

### **MTU Modification**

nmap \--mtu 16 10.49.139.250

### **Packet Delays**

nmap \--scan-delay 1000ms 10.49.139.250

These techniques can help reduce detection by certain filtering mechanisms.

---

## **Practical Skills Gained**

Through this room I practiced:

* TCP Enumeration  
* SYN Scanning  
* UDP Scanning  
* Service Version Detection  
* NSE Usage  
* Firewall Evasion Concepts  
* Scan Optimization  
* Reconnaissance Methodology

---

## **Key Takeaways**

* Enumeration remains the most important phase of an assessment.  
* Different scan types provide different trade-offs between speed, accuracy, and stealth.  
* NSE dramatically extends Nmap's capabilities beyond basic port scanning.  
* Firewall restrictions can influence scan results and require alternative approaches.  
* Effective scanning requires balancing information gathering with operational stealth.

---

## **Tools Used**

* Nmap  
* NSE (Nmap Scripting Engine)  
* Linux Terminal

## **Skills Demonstrated**

* Network Reconnaissance  
* Service Enumeration  
* Security Assessment Methodology  
* Firewall Evasion Awareness  
* Vulnerability Discovery Techniques

