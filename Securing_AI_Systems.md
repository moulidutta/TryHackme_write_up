# **TryHackMe Write-up: Securing AI Systems**

## **Room Information**

* **Room Name:** Securing AI Systems  
* **Platform:** TryHackMe  
* **Category:** AI Security  
* **Difficulty:** Beginner – Intermediate  
* **Link:** [https://tryhackme.com/room/securingaisystems](https://tryhackme.com/room/securingaisystems)

---

# **Introduction**

Building an AI model is only one part of creating a secure AI application. Modern AI systems consist of multiple interconnected components including APIs, orchestration layers, prompt construction pipelines, tool integrations, logging systems, vector databases, and external services.

Every connection between these components introduces trust boundaries and potential attack surfaces.

This room focuses on securing AI systems at the architectural level. Rather than examining attacks against the model itself, it explores how vulnerabilities emerge from system design, integrations, permissions, and data flows.

A central theme throughout the room is that traditional application security controls alone are insufficient for protecting modern AI-powered applications.

---

# **Learning Objectives**

By completing this room, I learned:

* The major components of a production AI system.  
* How trust boundaries create attack surfaces.  
* The role of OWASP LLM Top 10 (2025).  
* How MITRE ATLAS maps adversarial AI techniques.  
* System-level AI security threats.  
* Secure design patterns for AI applications.  
* The importance of least privilege and MLSecOps.  
* How to conduct an architectural security review of an AI system.

---

# **Task 1: Why AI Systems Need Security Reviews**

The room introduces a fictional AI-powered code review assistant called **TryAssist**.

At first glance, the application appears simple:

* User enters a prompt.  
* AI generates a response.

However, the room demonstrates that modern AI systems contain numerous hidden components operating behind the scenes.

Security architects must identify:

* Attack surfaces  
* Trust boundaries  
* Data flows  
* Privilege levels  
* Integration risks

before deployment occurs.

The key lesson is that AI security extends far beyond the language model itself.

---

# **Task 2: Anatomy of an AI System**

This section breaks down the architecture of TryAssist.

---

## **Core Components**
The room introduces nine major components commonly found in AI systems.

### **User Interface**

The front-end chat interface where users interact with the AI.

### **API Gateway**

Responsible for:

* Authentication  
* Request routing  
* Rate limiting

### **Orchestration Layer**

Coordinates workflows and conversation state.

### **Prompt Construction Layer**

Combines:

* System prompts  
* User input  
* Retrieved context

into the final prompt sent to the model.

### **LLM**

The language model responsible for generating responses.

### **Tool Layer**

Provides access to:

* Databases  
* APIs  
* Internal services  
* Documentation systems

### **Output Processing**

Formats and filters responses.

### **Logging and Monitoring**

Stores conversations and security telemetry.

### **Vector Store**

Contains embedded representations of documents used in Retrieval-Augmented Generation (RAG).

---

## **Trust Boundaries**

One of the most important concepts introduced in the room is:

### **Trust Boundaries**

A trust boundary exists whenever data moves between security contexts.

The room identifies five major trust boundaries:

1. User → System  
2. System → LLM  
3. LLM → Tools  
4. System → External Data  
5. System → User

Every trust boundary creates an opportunity for attackers to influence system behavior.

---

## **Data Flow Analysis**

The room walks through a complete request lifecycle.

A user's question passes through:
* Authentication  
* Prompt construction  
* Context retrieval  
* LLM processing  
* Tool execution  
* Output filtering  
* Logging

This exercise demonstrates how many different security controls are required to protect a single AI interaction.

---

# **Task 3: Understanding the AI Attack Surface**

This section introduces two major AI security frameworks.

---

## **OWASP LLM Top 10 (2025)**

The OWASP LLM Top 10 categorizes the most important security risks affecting LLM-powered applications.

Examples include:

**LLM01 – Prompt Injection** : Manipulating model behavior through crafted inputs.

**LLM02 – Sensitive Information Disclosure** : Exposure of confidential information.

**LLM05 – Improper Output Handling** : Unsafe processing of model output.

**LLM06 – Excessive Agency** : Granting AI systems excessive permissions.

**LLM07 – System Prompt Leakage** : Disclosure of hidden system instructions.

**LLM10 – Unbounded Consumption** : Resource exhaustion and cost-amplification attacks.

---

## **MITRE ATLAS**

The room also introduces:

### **MITRE ATLAS**

(Adversarial Threat Landscape for Artificial-Intelligence Systems)

MITRE ATLAS serves as a knowledge base documenting attacker tactics, techniques, and procedures (TTPs) targeting AI and machine learning systems.

ATLAS follows the adversary's progression through a target. An attacker begins with reconnaissance, learning what model the system uses and how it is exposed. They gain initial access by compromising a supply chain component or exploiting an input vector. They achieve execution through techniques like prompt injection, adversarial inputs, or model tampering. Where persistence is needed, they implant backdoors in model weights

---

# **Task 4: System-Level Threats**

This section examines five major AI security threats that originate from architectural decisions.

---

## **LLM10: Unbounded Consumption**

Attackers attempt to increase resource usage by:
* Sending massive prompts  
* Flooding APIs  
* Consuming excessive tokens

Potential impacts:
* Increased operational costs  
* Resource exhaustion  
* Denial of service

### **Defenses**
* Rate limiting  
* Input length restrictions  
* Usage quotas  
* Cost monitoring

---

## **LLM07: System Prompt Leakage**

System prompts often contain:

* Internal instructions  
* Tool configurations  
* Business logic  
* Security restrictions

Attackers may attempt to extract this information.

Potential impacts:

* Information disclosure  
* Easier bypass of security controls  
* Exposure of internal architecture

---

## **LLM05: Improper Output Handling**

One of the most dangerous AI security risks.

If AI-generated output is directly passed into:

* SQL queries  
* Shell commands  
* APIs

the output itself may become an injection vector.

This is similar to traditional injection attacks but originates from model-generated content.

---

## **LLM06: Excessive Agency**

AI systems should not possess more privileges than necessary.

Examples include:

* Direct deployment access  
* Administrative database permissions  
* Automatic code execution

Excessive autonomy dramatically increases risk.

---

## **LLM02: Sensitive Information Disclosure**

AI systems frequently process:

* Source code  
* Credentials  
* Personal information  
* Internal documents

Without proper controls, this data may leak through:

* Responses  
* Logs  
* External model providers
<img width="855" height="635" alt="Screenshot 2026-06-13 233557" src="https://github.com/user-attachments/assets/a5fee895-bf84-498b-be5c-a21bd3bc6569" />


---

# **Task 5: Secure Design Patterns**

After identifying threats, the room introduces practical defenses.

---

## **Defense in Depth**

Security controls should exist at every trust boundary.

Examples:

| Boundary | Security Controls |
| ----- | ----- |
| User → System | Authentication, rate limiting |
| System → LLM | Prompt hardening |
| LLM → Tools | Approval workflows |
| External Data | Validation and sanitization |
| System → User | Output filtering |

A failure at one layer should not compromise the entire system.
<img width="882" height="541" alt="Screenshot 2026-06-13 233652" src="https://github.com/user-attachments/assets/c5f3b975-24c4-4e74-a702-4f3b7acd69bb" />


---

## **Least Privilege**

Every AI component should receive only the permissions necessary to perform its task.

Examples:

* Read-only database access  
* Scoped API tokens  
* Restricted tool execution

This minimizes damage if a component is compromised.

---

## **Input and Output Validation**

Although AI accepts natural language rather than structured input, validation remains critical.

Input controls:

* Length restrictions  
* Content filtering  
* Injection detection

Output controls:

* Schema validation  
* Parameterized queries  
* Output sanitization

These controls reduce opportunities for abuse.

---

## **Monitoring and Observability**

The room introduces several AI-specific monitoring requirements.

Examples include:

**Request Monitoring** : Detect abnormal usage patterns.
**Token Monitoring** : Identify cost-explosion attacks.
**Tool Invocation Monitoring** : Track suspicious tool usage.
**Prompt Extraction Monitoring** : Detect attempts to reveal system prompts.
**Budget Monitoring** : Prevent runaway operational costs.

Traditional monitoring alone is insufficient for AI systems.

---

## **MLSecOps**

The room introduces:

### **MLSecOps**

Machine Learning Security Operations
MLSecOps integrates security throughout the entire AI lifecycle:

* Development  
* Testing  
* Deployment  
* Monitoring  
* Incident Response

It applies DevSecOps principles specifically to AI systems.

---

# **Task 6: Auditing TryAssist**

The final task places the learner in the role of a security architect.

Through a structured conversation with TryAssist, the goal is to evaluate:

* Available tools  
* Permission levels  
* Human approval workflows  
* System instructions  
* Logging practices  
* Data retention policies

The exercise demonstrates how architectural reviews can reveal security risks before production deployment.
A key takeaway is that every AI component introduces additional trust boundaries and attack surfaces that must be assessed individually.

---

# **Room Answers**

***What layer combines the system prompt, user input, and retrieved context before sending it to the model?***  
***Prompt Construction***

***In the TryAssist architecture, what boundary does LLM output cross when it triggers a database query?***  
***LLM-to-tools***

***Which OWASP LLM Top 10 category covers SQL injection through LLM output?***  
***Improper Output Handling***

***What MITRE knowledge base focuses on AI/ML adversary techniques?***  
***ATLAS***

***The Air Canada chatbot incident is classified under which OWASP category?***  
***Excessive Agency***

***What are the three dimensions of excessive agency?***  
***Permissions, Autonomy, Scope***

***Extracting internal API endpoints from a system prompt falls under which category?***  
***System Prompt Leakage***

***Generating excessive API costs through massive requests falls under which category?***  
***Unbounded Consumption***

***What principle gives AI components only the permissions they need?***  
***Least Privilege***

***What practice integrates security throughout the ML lifecycle?***  
***MLSecOps***

---

# **Key Concepts Learned**

### **Trust Boundaries**

Points where data crosses security contexts.

### **OWASP LLM Top 10**

Framework for AI application security risks.

### **MITRE ATLAS**

Knowledge base of AI attack techniques.

### **Improper Output Handling**

Unsafe processing of model-generated output.

### **Excessive Agency**

Over-privileged AI systems.

### **System Prompt Leakage**

Exposure of hidden instructions.

### **Unbounded Consumption**

Cost and resource exhaustion attacks.

### **MLSecOps**

Security operations for AI and ML systems.

---

# **Final Thoughts**

This room shifts the focus from attacking AI models to securing AI architectures.

The most valuable lesson was understanding that AI security is fundamentally an architectural challenge. Modern AI systems introduce entirely new components, trust boundaries, and attack surfaces that traditional web application security frameworks were never designed to handle.

The room also provides an excellent introduction to OWASP LLM Top 10, MITRE ATLAS, trust boundary analysis, and MLSecOps—topics that are becoming increasingly important for security engineers, SOC analysts, cloud security professionals, and AI security practitioners.

For anyone interested in AI Security, Security Architecture, Threat Modeling, or Secure AI Deployment, this room provides an outstanding foundation.

---

**Room Status:** Completed ✅

**Skills Learned:** AI Security Architecture, Threat Modeling, Trust Boundaries, OWASP LLM Top 10, MITRE ATLAS, MLSecOps, Secure Design Patterns, AI Risk Assessment

