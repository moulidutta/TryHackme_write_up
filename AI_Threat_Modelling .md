# **AI Threat Modelling TryHackMe Write-up**

## **Room Information**

* **Room Name:** AI Threat Modelling  
* **Platform:** TryHackMe  
* **Category:** AI Security  
* **Difficulty:** Beginner – Intermediate  
* **Link:** [https://tryhackme.com/room/aithreatmodelling](https://tryhackme.com/room/aithreatmodelling)

---

# **Introduction**

As organizations rapidly adopt Artificial Intelligence, securing AI applications requires more than traditional vulnerability scanning and penetration testing. AI systems introduce unique attack surfaces including prompts, model interactions, training data, retrieval systems, and external tool integrations.

To identify and mitigate these risks before deployment, security professionals use **Threat Modelling**.

This room introduces AI-specific threat modelling concepts and demonstrates how traditional security methodologies can be adapted for AI-powered systems. It focuses on identifying assets, trust boundaries, attack surfaces, threat actors, and mitigation strategies throughout the AI system lifecycle.

By the end of the room, learners gain practical experience analyzing AI architectures and systematically identifying potential security risks.

---

# **Learning Objectives**

By completing this room, I learned:

* What threat modelling is and why it is important.  
* How AI systems differ from traditional applications.  
* How to identify AI-specific assets and attack surfaces.  
* The role of trust boundaries in AI architectures.  
* How STRIDE applies to AI systems.  
* How to perform structured AI threat modelling.  
* Methods for prioritizing AI security risks.  
* How to build security controls into AI systems during design.

---

# **Task 1: Introduction to Threat Modelling**

The room begins by introducing a fundamental cybersecurity principle:

It is easier and cheaper to prevent security issues during design than to fix them after deployment.

Threat modelling is a structured process used to identify:

* What needs protection  
* Potential attackers  
* Possible attack paths  
* Security controls required

Instead of waiting for vulnerabilities to be discovered during testing, threat modelling helps security teams proactively identify risks early in the development lifecycle.

For AI systems, this approach becomes especially important because many attacks target system design rather than software vulnerabilities.

---

## **Why AI Requires Specialized Threat Modelling**

Traditional applications typically consist of:

* Front-end interfaces  
* APIs  
* Databases  
* Authentication systems

AI systems introduce additional components such as:

* Large Language Models (LLMs)  
* Vector Databases  
* Retrieval Systems  
* Prompt Pipelines  
* External Tools  
* Training Data Sources

Each new component creates additional attack surfaces and trust boundaries.

### **Key Takeaway**

AI security is not just application security plus an AI model.

AI introduces entirely new security challenges that must be analyzed separately.

---

# **Task 2: Understanding AI Assets**

Before identifying threats, we must understand what requires protection.

The room introduces the concept of:

## **Assets**

Assets are anything valuable that an attacker may target.

Examples within AI systems include:

### **Training Data**

The data used to train machine learning models.

Potential risks:

* Data poisoning  
* Data theft  
* Privacy violations

### **Model Weights**

The learned parameters of a trained model.

Potential risks:

* Model theft  
* Intellectual property loss  
* Model inversion attacks

### **Prompts**

Instructions provided to the model.

Potential risks:

* Prompt injection  
* Prompt leakage  
* Information disclosure

### **Vector Databases**

Repositories containing embedded representations of data.

Potential risks:

* Unauthorized retrieval  
* Sensitive information exposure

### **API Keys and Credentials**

Used to access external services.

Potential risks:

* Credential theft  
* Privilege escalation

The room emphasizes that every valuable component should be treated as a potential target.

---

# **Task 3: Mapping the AI System**

Threat modelling requires understanding how data moves through a system.

The room introduces:

## **Data Flow Diagrams (DFDs)**

A Data Flow Diagram visualizes:

* Components  
* Data movement  
* External entities  
* Trust boundaries

A simplified AI workflow might look like:

User → Web Application → Prompt Builder → LLM → Tool/API → Response

Each connection becomes a potential attack path.

---

## **Trust Boundaries**

One of the most important concepts introduced in the room.

A trust boundary exists whenever data crosses between different security contexts.

Examples:

### **User → Application**

User input cannot be trusted.

### **Application → LLM**

Prompt manipulation may occur.

### **LLM → External Tools**

The model may trigger unintended actions.

### **External Data → Application**

Retrieved information may contain malicious content.

Threat modelling focuses heavily on analyzing these boundaries because attackers often exploit them.

---

# **Task 4: Applying STRIDE to AI Systems**

The room introduces one of the most popular threat modelling frameworks:

## **STRIDE**

Developed by Microsoft, STRIDE categorizes threats into six groups.

---

## **S – Spoofing**

Pretending to be someone else.

Examples:

* Stolen API keys  
* Account takeover  
* Fake identities

Potential impact:

Unauthorized access to AI services.

---

## **T – Tampering**

Modifying data or system components.

Examples:

* Training data poisoning  
* Prompt manipulation  
* Model modification

Potential impact:

Corrupted AI behavior.

---

## **R – Repudiation**

Denying actions occurred.

Examples:

* Missing audit logs  
* Incomplete monitoring

Potential impact:

Difficulty investigating incidents.

---

## **I – Information Disclosure**

Exposure of sensitive information.

Examples:

* Prompt leakage  
* Training data extraction  
* Model inversion

Potential impact:

Confidentiality breaches.

---

## **D – Denial of Service**

Preventing system availability.

Examples:

* Context flooding  
* Resource exhaustion  
* Excessive token consumption

Potential impact:

Service disruption and increased costs.

---

## **E – Elevation of Privilege**

Gaining unauthorized permissions.

Examples:

* Over-privileged AI agents  
* Tool misuse  
* Unauthorized actions

Potential impact:

Compromise of critical systems.

---

## **STRIDE in AI Security**

The room demonstrates how traditional STRIDE categories map effectively to AI-specific threats.

This provides security teams with a familiar framework while analyzing modern AI applications.

---

# **Task 5: Identifying AI Threats**

This section focuses on common AI attack scenarios.

---

## **Prompt Injection**

Attackers manipulate prompts to override intended instructions.

Examples:

* Ignoring safety rules  
* Revealing hidden prompts  
* Triggering unauthorized actions

Prompt injection remains one of the most significant AI threats.

---

## **Data Poisoning**

Attackers manipulate training data before model training.

Potential consequences:

* Incorrect predictions  
* Hidden backdoors  
* Biased behavior

---

## **Model Theft**

Organizations invest substantial resources in training AI models.

Attackers may attempt to:

* Copy model behavior  
* Reconstruct model functionality  
* Steal intellectual property

---

## **Sensitive Information Disclosure**

AI systems often process:

* Source code  
* Personal information  
* Internal documentation  
* Business secrets

Without proper controls, this information may be exposed through model outputs.

---

## **Excessive Agency**

AI systems connected to tools may perform actions automatically.

Examples:

* Sending emails  
* Executing commands  
* Accessing databases

If permissions are poorly managed, attackers may abuse these capabilities.

---

# **Task 6: Threat Prioritization**

Not every threat carries the same level of risk.

The room introduces risk prioritization concepts.

---

## **Risk Assessment**

Threats are evaluated based on:

### **Likelihood**

How likely the attack is to occur.

### **Impact**

The damage caused if successful.

Security teams focus first on threats with:

* High likelihood  
* High impact

This ensures resources are used effectively.

---

## **Example Prioritization**

| Threat | Likelihood | Impact |
| ----- | ----- | ----- |
| Prompt Injection | High | High |
| Model Theft | Medium | High |
| Data Poisoning | Medium | High |
| Denial of Service | High | Medium |
| Prompt Leakage | High | Medium |

Threat modelling helps determine which controls should be implemented first.

---

# **Task 7: Building Security Controls**

Once threats are identified, appropriate defenses can be designed.

Examples include:

### **Authentication and Authorization**

Protect sensitive resources.

### **Least Privilege**

Limit permissions to only what is required.

### **Input Validation**

Reduce prompt manipulation risks.

### **Output Filtering**

Prevent information disclosure.

### **Monitoring and Logging**

Improve visibility and incident response.

### **Human Approval Workflows**

Reduce risks associated with autonomous AI actions.

The room emphasizes integrating security controls during system design rather than after deployment.

---

# **Room Answers**

***What process is used to identify threats before deployment?***  
***Threat Modelling***

***What diagram is commonly used to visualize system components and data flows?***  
***Data Flow Diagram***

***What boundary exists when data moves between different security contexts?***  
***Trust Boundary***

***Which STRIDE category covers unauthorized disclosure of sensitive information?***  
***Information Disclosure***

***Which STRIDE category covers resource exhaustion attacks?***  
***Denial of Service***

***What AI attack manipulates instructions given to the model?***  
***Prompt Injection***

***What attack involves malicious modification of training data?***  
***Data Poisoning***

***What principle limits permissions to only what is necessary?***  
***Least Privilege***

---

# **Key Concepts Learned**

### **Threat Modelling**

Structured identification of security risks during system design.

### **Assets**

Valuable components requiring protection.

### **Data Flow Diagrams**

Visual representations of system interactions.

### **Trust Boundaries**

Points where data crosses security contexts.

### **STRIDE**

Threat classification framework.

### **Prompt Injection**

Manipulation of model instructions.

### **Data Poisoning**

Compromising training datasets.

### **Risk Prioritization**

Evaluating threats based on likelihood and impact.

### **Security Controls**

Defensive measures integrated into system design.

---

# **Final Thoughts**

This room provides an excellent introduction to AI threat modelling and demonstrates how traditional security methodologies can be adapted for modern AI systems.

The most valuable lesson was understanding that AI security begins long before deployment. By identifying assets, mapping trust boundaries, applying STRIDE, and prioritizing risks, organizations can significantly reduce the likelihood of security incidents.

As AI adoption continues to grow, threat modelling will become an essential skill for security architects, AI engineers, SOC analysts, cloud security professionals, and AI security practitioners.

For anyone interested in AI Security, Secure AI Development, Threat Modelling, or Security Architecture, this room provides a strong foundation for understanding how to identify and mitigate risks in AI-powered environments.

---

**Room Status:** Completed ✅

**Skills Learned:** AI Threat Modelling, STRIDE, Trust Boundaries, Data Flow Diagrams, Prompt Injection Analysis, Risk Assessment, Security Architecture, AI Security Design

