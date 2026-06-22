# **AI System Reconnaissance \- TryHackMe Write-up**

## **Room Information**

* **Room Name:** AI System Reconnaissance  
* **Platform:** TryHackMe  
* **Category:** AI Security  
* **Difficulty:** Beginner – Intermediate  
* **Link:** [https://tryhackme.com/room/aisystemreconnaissance](https://tryhackme.com/room/aisystemreconnaissance)

---

# **Introduction**

Before securing an AI system, security professionals must first understand how it works. Just like traditional penetration testing begins with reconnaissance, AI security assessments also start with gathering information about the target system.

This room introduces the concept of AI System Reconnaissance and explores how attackers and defenders analyze AI-powered applications. The focus is on identifying AI components, understanding system architecture, mapping trust boundaries, and discovering potential attack surfaces before attempting exploitation.

By learning reconnaissance techniques, security professionals can better understand how AI systems operate and where security weaknesses may exist.

---

# **Learning Objectives**

By completing this room, I learned:

* The role of reconnaissance in AI security.  
* How to identify AI system components.  
* How to map trust boundaries in AI applications.  
* Methods for identifying AI attack surfaces.  
* How attackers gather information about AI-powered systems.  
* Techniques for analyzing AI workflows and integrations.  
* The importance of architecture awareness during AI security assessments.

---

# **Task 1: Introduction to AI Reconnaissance**

## **Overview**

The room begins by explaining why reconnaissance is a critical phase of any security assessment.

Traditional reconnaissance focuses on identifying:

* Hosts  
* Services  
* Applications  
* Network infrastructure

AI reconnaissance extends this process by identifying:

* Language Models  
* Prompt Pipelines  
* External Tools  
* Vector Databases  
* Retrieval Systems  
* AI Agents

Understanding these components helps security analysts build a complete picture of the target environment.

### **Key Takeaway**

You cannot effectively secure or assess an AI system without understanding how its components interact.

---

# **Task 2: The AI Infrastructure Stack**

## **Overview**

Modern AI applications consist of multiple interconnected layers.

The room introduces common AI architecture components.

### **User Interface**

The entry point where users interact with the AI system.

### **Application Layer**

Responsible for:

* Authentication  
* Session Management  
* Request Processing

### **Prompt Processing Layer**

Combines:

* User Input  
* System Instructions  
* Context Data

before sending requests to the model.

### **Language Model**

The AI model responsible for generating responses.

### **External Tools**

The model may interact with:

* APIs  
* Databases  
* Internal Systems  
* Third-Party Services

### **Monitoring Systems**

Used for:

* Logging  
* Auditing  
* Performance Tracking

Understanding each layer helps identify potential attack vectors.

---

# **Task 3: Fingerprinting AI services**

## **Overview**

Fingerprinting AI services requires a different approach; you need to look at:

HTTP headers
JSON response structures
Error messages
Endpoint naming conventions

### **What is a Trust Boundary?**

A trust boundary exists whenever data moves between different security contexts.

Examples include:

### **User → AI Application**
User-controlled input enters the system.

### **AI Application → Model**
Prompts and instructions are passed to the LLM.

### **Model → External Tools**
The AI interacts with APIs or other systems.

### **External Data → AI System**
Retrieved content becomes part of model context.



---

# **Task 4: Enumerating AI systems **

## **Overview**

The room focuses on understanding where attackers may interact with or influence the AI system.
MLflow Enumeration
MLflow is the most rewarding service to enumerate because it stores everything in one place and exposes it through a clean REST API. If you find an open MLflow instance...

### **Common AI Attack Surfaces**

#### **Prompts**
Attackers may manipulate prompts to influence model behavior.

#### **Training Data**
Compromised data can affect model outputs.

#### **Vector Databases**
Sensitive information may be exposed through retrieval systems.

#### **Tool Integrations**
Connected services may introduce additional risks.

#### **APIs**
Public-facing APIs often become primary reconnaissance targets.

### **Reconnaissance Goals**
* Identify exposed services.  
* Understand available functionality.  
* Determine integration points.  
* Map potential attack paths.

---

# **Task 5: Mapping the AI systems**

## **Overview**

This section introduces methods used to gather information about AI systems.
Identified AI components in the network, determined which framework each component runs on, and extracted metadata from their APIs. Those are individual findings. This task is about connecting them.

A single exposed MLflow server is a finding.
The difference between a list of findings and an attack surface map is the connections between them.

### **Information Gathering Techniques**

#### **Application Observation**

Analyzing system behavior through normal interactions.

#### **Response Analysis**

Studying:

* Model outputs  
* Error messages  
* Response formats

#### **Integration Discovery**

Identifying connected tools and services.

#### **Architecture Mapping**

Creating a high-level understanding of the system workflow.

### **Findings**

Reconnaissance often reveals:

* Available features  
* Backend technologies  
* External dependencies  
* Security assumptions

These observations can help security teams identify weaknesses before attackers do.

MITRE ATLAS Mapping
Everything we have covered in this room maps to the MITRE ATLAS framework. ATLAS is modelled after ATT&CK but specifically covers adversarial threats to AI and ML systems. It contains 15 tactics, 66 techniques, and 46 sub-techniques as of late 2025.

---

# **Task 6: Practical Exercise**

## **Overview**

The final exercise places the learner in the role of a security analyst performing reconnaissance against an AI-powered application.

### **Objectives**

* Identify system components.  
* Map trust boundaries.  
* Understand data flows.  
* Document attack surfaces.  
* Evaluate potential risks.

### **Investigation Workflow**

#### **Step 1: Observe Application Behavior**

Interact with the system and document responses.

#### **Step 2: Identify AI Components**

Determine which AI services are being used.

#### **Step 3: Map Data Flows**

Track how information moves through the system.

#### **Step 4: Identify Integrations**

Discover external tools and APIs.

#### **Step 5: Document Risks**

Record observations and potential security concerns.

### **Outcome**

The exercise demonstrates how reconnaissance provides the foundation for future security assessments.

---

# **Room Answers**

***What is the IP address of the host running an HTTP service on port 8888 in your scan results?***  
***10.10.45.20***

***Which port does MLflow Tracking Server run on by default?***  
***5000***

***Which unique HTTP response header does the service on 10.10.45.15:8000 return to identify as an NVIDIA product?***  
***NV-Status***

***When you run grpcurl against 10.10.45.15:8001, what is the name of the inference service listed in the reflection output?***  
***inference.GRPCInferenceService***

***What MLflow REST API endpoint would you use to retrieve the artifact storage location for a specific model version?***  
***/api/2.0/mlflow/model-versions/search***

***What is the cleartext password for the MLflow service account stored in the Jupyter notebook on 10.10.45.20?***  
***Cyphira-MLfl0w-2024\!***

***The Cyphira Jupyter notebook at 10.10.45.20 contains a Hugging Face token (hf\_kR7mXpQvL9nJwT2yBcDfAeGh8iKlMnOp). The internal-kb-embedder model on MLflow references sentence-transformers/all-MiniLM-L6-v2 as its base model. What ATLAS technique ID covers the risk of these exposed supply chain dependencies?***  
***AML.T0010***

***You scanned the Cyphira subnet with nmap, probed endpoints with curl, and extracted metadata from MLflow APIs. All of these activities fall under one overarching ATLAS tactic. What is its ID?***  
***AML.TA0002***

***A SIEM log shows requests to /api/2.0/mlflow/registered-models/list from an IP with no corresponding MLflow UI session. What tool's access pattern does this match?***  
***MLOKit***

***What is the single most effective quick win for preventing unauthenticated access to the MLflow tracking server?***  
***Enable MLflow authentication***

## **Room Findings proof work:**

<img width="1154" height="343" alt="Screenshot 2026-06-19 233309" src="https://github.com/user-attachments/assets/39dd5d21-7042-4cfd-968e-a7593d607220" />

<img width="1155" height="438" alt="Screenshot 2026-06-19 233242" src="https://github.com/user-attachments/assets/6498ebfc-b8e8-4c2a-bbcb-eaa761ed7913" />

<img width="1047" height="530" alt="Screenshot 2026-06-19 233213" src="https://github.com/user-attachments/assets/3ddf254d-87de-4221-a890-a639f759a300" />

<img width="1090" height="513" alt="Screenshot 2026-06-19 233148" src="https://github.com/user-attachments/assets/43020a93-cc34-4cb1-81ba-8576dc894743" />




---

# **Key Concepts Learned**

### **AI Reconnaissance**

The process of gathering information about AI systems before assessment.

### **AI Architecture**

Understanding the components that make up an AI application.

### **Trust Boundaries**

Points where data crosses security contexts.

### **Attack Surface Analysis**

Identifying locations where attackers may interact with a system.

### **System Enumeration**

Discovering technologies, services, and integrations.

### **Data Flow Mapping**

Tracking information movement throughout the application.

---

# **Skills Gained**

* AI Security Assessment  
* Architecture Analysis  
* Trust Boundary Identification  
* Data Flow Analysis  
* Attack Surface Enumeration  
* AI Threat Discovery  
* Security Documentation

---

# **Real-World Relevance**

The concepts covered in this room are highly relevant to:

* AI Security Analysts  
* Security Engineers  
* Threat Hunters  
* Security Architects  
* SOC Analysts  
* Red Team Operators

  
Reconnaissance is often the first step in identifying vulnerabilities and understanding the overall security posture of AI-powered systems.

---

# **Final Thoughts**

This room provides a strong introduction to AI System Reconnaissance and highlights the importance of understanding system architecture before performing security assessments.

The biggest takeaway was that AI security begins with visibility. By identifying components, trust boundaries, data flows, and integrations, security professionals can better understand how AI systems operate and where potential risks exist..

---

**Room Status:** Completed ✅

**Skills Learned:** AI Reconnaissance, Architecture Analysis, Attack Surface Mapping, Trust Boundary Identification, Data Flow Analysis, AI Security Assessment

