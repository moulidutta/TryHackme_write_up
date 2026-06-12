# **TryHackMe Write-up: LLM Security**

## **Room Information**

* **Room Name:** LLM Security  
* **Platform:** TryHackMe  
* **Category:** AI Security  
* **Difficulty:** Beginner–Intermediate  
* **Link:** [https://tryhackme.com/room/llmsecurity](https://tryhackme.com/room/llmsecurity)

---

# **Introduction**

Large Language Models (LLMs) have rapidly become a core part of modern applications. From AI assistants and customer support chatbots to enterprise productivity tools, organizations are integrating LLMs into their workflows at an unprecedented rate.

However, these systems introduce entirely new attack surfaces that traditional cybersecurity controls were never designed to handle. Unlike conventional software, LLMs interact through natural language, maintain conversational context, and often connect to external tools and data sources.

This room focuses on understanding LLMs as an attack surface and explores the major security risks associated with deploying and using them in production environments.

---

# **Learning Objectives**

By completing this room, I learned:

* How LLM security differs from traditional machine learning security.  
* The four major categories of LLM threats.  
* How attackers exploit training data, model behavior, system integrations, and users.  
* The risks of prompt injection, model theft, and memory poisoning.  
* Why LLM-powered social engineering is becoming increasingly dangerous.  
* How to think about AI systems from a security-first perspective.

---

# **Task 1: Introduction to LLM Security**

The room begins by explaining that LLMs are not simply another software component.

Traditional applications follow predefined logic. LLMs, on the other hand:

* Process natural language  
* Generate probabilistic outputs  
* Maintain context  
* Learn from large datasets  
* Can interact with external systems

Because of these characteristics, LLMs introduce attack vectors that do not exist in traditional software environments.

---

## **The Four LLM Threat Categories**

The room organizes LLM threats into four groups:

### **Data-Based Threats**

Attacks targeting training data and sensitive information.

### **Model-Based Threats**

Attacks targeting the model itself.

### **System-Based Threats**

Attacks targeting how the LLM is integrated into applications.

### **User-Based Threats**

Attacks using AI to manipulate people.

Understanding these categories makes it easier to identify where security controls are required.

---

# **Task 2: Data-Based Threats**

LLMs learn from enormous datasets.

While this gives them impressive capabilities, it also creates significant security concerns.

The room introduces three major data-related threats:

* Training Data Extraction  
* Membership Inference  
* Prompt Leakage

---

## **Training Data Extraction**

LLMs sometimes memorize portions of their training data.Training data extraction attacks aim to recover actual sequences from the model's original training data by interacting with the model .Attackers may craft prompts designed to retrieve:

* Private information  
* Credentials  
* Proprietary documents  
* Sensitive records

Instead of generating new content, the model may reproduce information it previously learned.

This effectively turns the model into an unintended data disclosure mechanism.

---

## **Membership Inference**

Membership inference attacks attempt to determine whether a specific piece of data was included in a model's training set.

These attacks ask whether the model ever recorded a specific data sample. The attacker tests the model's reaction to that exact sample, looking for unusually confident or familiar responses that indicate it was part of training. Crucially, membership inference assumes the attacker already possesses the exact candidate data sample and is only testing whether that known sample influenced the model's training.  

For example:

An attacker may possess a confidential document and attempt to discover whether that document was used during model training.

Potential risks include:

* Privacy violations  
* Regulatory concerns  
* Information disclosure

This attack focuses on determining data membership rather than extracting the actual content itself.

---

## **Prompt Leakage**

Prompt Leakage (LLM07:2025 — System Prompt Leakage) : LLMs like ChatGPT, Claude, Gemini, etc., don't just operate using the learnings from their training data; they also use hidden instructions known as system or developer prompts. This system prompt is kept hidden in many instances, especially when what sits in front of the model is some form of "intellectual property," such as an application feature or product.

### **System Prompt Leakage**

Many AI applications contain hidden instructions called:

* System Prompts  
* Developer Prompts

These instructions define:

* Model behavior  
* Restrictions  
* Internal rules  
* Business logic

Attackers may attempt to convince the model to reveal these hidden prompts.

In some cases, leaked prompts can expose proprietary company logic, internal workflows, or security controls.

### **Key Takeaway**

Hidden prompts should be treated as sensitive information because they often contain valuable intellectual property.

---

# **Task 3: Model-Based Threats**

This section focuses on attacks against the model itself.

Unlike data-based attacks, these threats target information encoded within the model's internal parameters.

The room introduces two major threats:

* Model Extraction  
* Model Inversion

---

## **Model Extraction (Model Theft)**

Model extraction is the process of illicitly copying a machine learning model's functionality or parameters without authorisation. Training advanced AI models requires:

* Massive datasets  
* Significant computational resources  
* Large financial investments

Attackers may attempt to steal a model by repeatedly querying its public API.

The process works by:

1. Sending thousands of carefully crafted prompts.  
2. Collecting responses.  
3. Building input-output datasets.  
4. Training a surrogate model.

Eventually, the attacker may create a model that closely mimics the original system.

This attack primarily threatens intellectual property and competitive advantage.

---

## **Model Inversion**

Model inversion attacks attempt to reconstruct sensitive information stored within the model's internal representations. Model inversion attacks treat the model as a source of stored information rather than a classifier to be probed. Instead of testing whether a known example was seen during training, the attacker iteratively queries the model to reconstruct unknown training data that has been encoded into its parameters or representations.

Instead of stealing the entire model, attackers try to recover:

* Training records  
* Personal information  
* Hidden attributes

The room demonstrates how partial information can sometimes be reconstructed from a trained model.

This is particularly concerning when models are trained on sensitive datasets.

---

# **Task 4: System-Based Threats**

This section focuses on one of the most important topics in modern AI security.

The room explains that LLMs process all input as a single context window.

This means:

* System instructions  
* User prompts  
* Retrieved documents

are often processed together.

Because the model cannot perfectly distinguish trusted instructions from untrusted content, attackers can manipulate its behavior.

---

## **Prompt Injection**

Prompt injection is one of the most widely known LLM attacks.

An attacker attempts to override the intended instructions of the model using carefully crafted language.

Examples include:

* Ignoring security restrictions  
* Revealing hidden prompts  
* Bypassing safeguards  
* Performing unintended actions

The room describes prompt injection as a consequence of context-window manipulation.

### **Why It Happens**

Traditional software separates:

* Code  
* Data

LLMs do not make this distinction reliably.

Everything enters the context window as text, making prompt injection fundamentally different from traditional software vulnerabilities.

---

## **Context Overflow**

Context Overflow (LLM10:2025 — Unbounded Consumption): Every LLM has a finite context window.

Attackers may abuse this limitation by:

* Submitting extremely large prompts  
* Flooding the context window  
* Pushing critical instructions out of memory

Potential impacts include:

* Reduced performance  
* Ignored safeguards  
* Denial of service conditions

The room maps this threat to OWASP's concept of unbounded consumption.

---

## **Memory Poisoning**

Many AI assistants maintain conversation history.

Attackers can exploit this by gradually introducing false information into the model's memory.

Over time, the model may begin treating malicious information as trusted context.

Example:

If an attacker repeatedly teaches incorrect facts to a chatbot, future responses may become corrupted.

Unlike prompt injection, memory poisoning often occurs across multiple interactions rather than a single prompt.
<img width="1576" height="372" alt="Screenshot 2026-06-12 232147" src="https://github.com/user-attachments/assets/5ff62a78-0c95-4e51-8727-d0fc89144560" />


---

# **Task 5: User-Based Threats**

Not every AI security threat targets the model.

Sometimes the target is the human using it.

This section focuses on how attackers leverage AI to manipulate people more effectively.

---

## **LLM-Powered Social Engineering**

LLMs can turbocharge social engineering attacks, making scamming far more convincing than traditional phishing. Suddenly, telltale signs of phishing such as spelling/grammatical errors, poorly concealed calls to urgency, and obvious links can no longer be relied upon to spot phishing emails in the wild. An LLM can now generate spear-phishing emails that read exactly like a colleague or executive.  
Traditional phishing attacks often contain:

* Poor grammar  
* Generic messaging  
* Obvious red flags

LLMs change this completely.

Attackers can generate:

* Personalized phishing emails  
* Convincing business communications  
* Context-aware scams  
* Highly believable impersonation attempts

The result is a dramatic increase in the quality and scale of social engineering attacks.

---

## **Trust Exploitation**

Trust Exploitation (LLM09:2025 — Misinformation): 

Many users assume AI-generated information is accurate.

Attackers can exploit this trust.

Potential impacts include:

* Spreading misinformation  
* Influencing decisions  
* Promoting unsafe actions  
* Manipulating user behavior

The room highlights that user trust itself becomes an attack surface when AI systems are involved.

---

# **LLM Security Cheat Sheet**

| Threat Category | Example Threats |
| ----- | ----- |
| Data-Based | Training Data Extraction, Membership Inference, Prompt Leakage |
| Model-Based | Model Extraction, Model Inversion |
| System-Based | Prompt Injection, Context Overflow, Memory Poisoning |
| User-Based | Social Engineering, Trust Exploitation |

This framework provides a simple way to classify and assess AI-related risks during security reviews.

---

# **Practical Exercises**

Throughout the room, a simulated AI assistant is used to demonstrate multiple attack techniques.

The exercises include:

* Performing membership inference.  
* Recovering hidden information through model inversion.  
* Demonstrating prompt injection.  
* Manipulating conversation memory.

These practical demonstrations help illustrate how theoretical AI attacks can occur in real-world systems.

---

# **Key Concepts Learned**

### **Training Data Extraction**

Recovering memorized information from a model.

### **Membership Inference**

Determining whether specific data was included in training.

### **Prompt Leakage**

Exposing hidden system instructions.

### **Model Extraction**

Stealing model functionality through API interactions.

### **Model Inversion**

Reconstructing information from model internals.

### **Prompt Injection**

Manipulating model behavior using crafted prompts.

### **Context Overflow**

Abusing context-window limitations.

### **Memory Poisoning**

Corrupting persistent conversation history.

### **AI-Powered Social Engineering**

Using AI to improve phishing and manipulation attacks.

---

# **Final Thoughts**

This room provides one of the clearest introductions to LLM security from a cybersecurity perspective.

The most valuable lesson was understanding that AI security is much broader than prompt injection alone. Risks exist across the entire AI ecosystem, including training data, model architecture, application integration, and human users.

The four-category threat model (Data-Based, Model-Based, System-Based, and User-Based) provides a practical framework for evaluating AI systems and identifying security weaknesses.

As organizations continue integrating AI into critical business processes, understanding these attack surfaces will become an essential skill for SOC analysts, security engineers, threat hunters, penetration testers, and AI security professionals.

---

**Room Status:** Completed ✅

**Skills Learned:** LLM Security, Prompt Injection, Membership Inference, Model Inversion, Model Extraction, Memory Poisoning, AI Threat Modeling, AI-Powered Social Engineering, Secure AI Design

