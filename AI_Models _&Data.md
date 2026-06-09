# **TryHackMe Write-up: AI Models & Data**

## **Room Information**

* **Room Name:** AI Models & Data  
* **Platform:** TryHackMe  
* **Category:** AI Security  
* **Difficulty:** Beginner  
* **Link:** [https://tryhackme.com/room/aimodelsdata](https://tryhackme.com/room/aimodelsdata)

---

# **Introduction**

When most people think about AI security, they focus on prompt injection, jailbreaks, or malicious AI-generated content. However, many security risks originate much earlier in the AI lifecycle—during data collection, model training, fine-tuning, and deployment.

This room explores the often-overlooked security risks hidden within AI training data and model development. It explains where AI training data comes from, why data provenance matters, how pre-trained models inherit risks, and why AI models are often considered "black boxes." The room also highlights the growing importance of transparency and documentation when deploying AI systems.

---

# **Learning Objectives**

By completing this room, I learned:

* Where AI training data originates.  
* The security risks of poor data provenance.  
* How sensitive information can become embedded in model weights.  
* The impact of overfitting, quantization, and federated learning.  
* The security implications of fine-tuning pre-trained models.  
* Why AI models are considered black boxes.  
* The role of model cards in AI transparency.

---

# **Task 1: Introduction**

The room starts with an important concept:

Every AI model is a product of its training data.

Before an AI model generates a response, predicts an outcome, or assists a user, countless decisions have already been made regarding:

* What data was collected  
* Where it came from  
* How it was processed  
* How it was filtered

These decisions directly influence the behavior and security of the final model.

One of the key messages of the room is that AI security begins long before deployment. It starts within the data supply chain itself.

---

# **Task 2: Training Data**

## **Where Does AI Training Data Come From?**

Training modern AI models requires enormous amounts of data.

The room explains four common sources:

### **Web Scraping**

Data collected automatically from:

* Websites  
* Blogs  
* Forums  
* Social media platforms  
* News articles

This source is highly scalable but often poorly controlled.

### **Licensed Datasets**

Datasets acquired through agreements with organizations or platforms.

These typically offer better legal clarity but may still raise privacy concerns.

### **Synthetic Data**

AI-generated content used to train future AI systems.

As AI adoption grows, synthetic data is becoming increasingly common.

### **Internal Corpora**

Private organizational data such as:

* Support tickets  
* Internal documentation  
* Medical records  
* Company knowledge bases

Organizations have more control over these datasets but also greater responsibility if sensitive information is exposed.

---

## **Data Provenance**

One of the most important concepts introduced in this room is:

### **Data Provenance**

Data provenance answers three questions:

1. Where did the data come from?  
2. When was it collected?  
3. Has it been modified?

Without proper provenance, organizations cannot verify the quality, legality, or security of training data.

A major concern highlighted in the room is that many modern AI datasets are built from numerous sources, making it difficult to track their origins accurately.

---

## **ML-BOM**

The room introduces the concept of an:

### **ML-BOM (Machine Learning Bill of Materials)**

This is similar to a Software Bill of Materials (SBOM) used in software security.

An ML-BOM documents:

* Dataset sources  
* Licenses  
* PII exposure risks  
* Filtering decisions  
* Training data composition

This improves transparency and helps organizations understand what they are actually deploying.

---

## **PII in Training Data**

One of the most alarming sections discusses Personally Identifiable Information (PII).

Large-scale web scraping may unintentionally collect:

* Email addresses  
* Personal conversations  
* Medical information  
* Credentials  
* API keys

If this information becomes part of a model's training dataset, fragments of that data may become embedded within the model itself.

The room emphasizes that once information is encoded into model weights, removing it becomes extremely difficult.

---

# **Task 3: Building the Model**

This section explores important concepts involved in training and optimizing AI models.

---

## **Epochs and Overfitting**

### **Epoch**

Epoch represents one complete pass through the training dataset.An epoch is one complete pass of the training algorithm through the entire dataset. In practice, models are trained over many epochs. The algorithm repeatedly sees the same data, adjusting its parameters each time until it converges on accurate predictions. 

Models often train across many epochs to improve performance.

### **Overfitting**

Overfitting occurs when a model memorizes training data instead of learning general patterns.

Symptoms include:

* Excellent performance on training data  
* Poor performance on new data

From a security perspective, overfitting increases the likelihood that sensitive training information may be reproduced later.

---

## **Model Validation**

To reduce overfitting, developers use:

### **Validation Sets**

A portion of the dataset is withheld during training.

The model is periodically tested using this unseen data.

Benefits include:

* Detecting overfitting  
* Evaluating real-world performance  
* Identifying data quality issues

Validation acts as a security checkpoint before deployment.

---

## **Quantisation**

Modern AI models can be extremely large.

To improve efficiency, developers often compress them using:

### **Quantisation**

This process reduces numerical precision within model weights.

Benefits:

* Lower memory usage  
* Faster inference  
* Reduced hardware requirements

However, the room explains that quantization may unintentionally weaken safety mechanisms or alter model behavior in unexpected ways.

---

## **Federated Learning**

Traditional AI training gathers all data in a centralized location. Federated learning is therefore an interesting case study in security trade-offs: it solves one trust problem by distributing control, but in doing so creates a different one. 

Federated Learning takes a different approach.

Instead:

* Training occurs locally.  
* Devices keep their data.  
* Only model updates are shared.

Benefits include:

* Improved privacy  
* Reduced data sharing requirements

However, verifying the integrity of contributed updates becomes more difficult. This introduces new security challenges.

---

# **Task 4: Pre-Trained Models and Fine-Tuning**

Most organizations do not build AI models from scratch.

Instead, they begin with:

### **Pre-Trained Models**

These are models already trained on massive datasets.

Examples include:

* Foundation models  
* Large Language Models (LLMs)

Organizations then customize them through:

### **Fine-Tuning**

Fine-tuning is the process of continuing to train one of these pre-trained models on a smaller, task-specific dataset. A healthcare company might fine-tune a base model trained on clinical documentation to improve its understanding of medical terminology. A law firm might fine-tune on case law. The result is a model with the broad capabilities of the base model, now specialised for a particular domain or use case. Fine-tuning involves continuing training using a smaller, specialized dataset.

Examples:

* Healthcare AI  
* Legal AI  
* Cybersecurity AI  
* Customer support AI

Fine-tuning enables specialization without retraining an entire model.

---

## **The Inheritance Problem**

One of the most important lessons from this room is:

### **Fine-tuning does not remove inherited risks.**

Organizations inherit:

* Existing biases  
* Hidden vulnerabilities  
* Undocumented behaviors  
* Safety limitations

from the original model.

Even if a company carefully fine-tunes a model, it still inherits everything embedded within the base model.

---

## **Security Risks of Fine-Tuning**

The room highlights several concerns.

### **Safety Alignment Degradation**

Security controls built into the original model may weaken during fine-tuning.

### **Increased Attack Surface**

Specialized models may become more susceptible to prompt injection attacks.

### **Version Tracking Challenges**

Organizations often struggle to determine exactly which model version was used during development.

This makes risk assessment significantly more difficult.

---

# **Task 5: The Black Box Problem**

Unlike traditional software, AI models are difficult to inspect.

With source code, developers can:

* Review logic  
* Analyze functions  
* Audit behavior

AI models are different.

Their knowledge is encoded within billions of numerical parameters known as:

### **Model Weights**

These weights are not human-readable.

As a result, it is often impossible to determine exactly why a model behaves a certain way.

---

## **Model Cards**

The documentation artefact designed to address this is the model card: a structured document that accompanies a model and describes what it is, how it was built, and where it falls short. To improve transparency, organizations use:

### **Model Cards**

A model card provides documentation about:

* Training data  
* Intended use  
* Evaluation results  
* Known limitations  
* Bias assessments  
* Licensing information

Think of a model card as a nutritional label for AI systems.

It helps users understand what they are using and the limitations that may exist.

---

## **Why Model Cards Matter**

Without a model card:

* Transparency is reduced.  
* Security review becomes harder.  
* Risk assessment becomes less reliable.  
* Trust must be placed entirely in the vendor.

The room emphasizes that a missing or incomplete model card should be treated as a warning sign.

---

# **Task 6: Practical Exercise**

The final task places the learner in the role of a security auditor.

A simulated AI model repository is presented, similar to platforms used for sharing open-source AI models.

The objective is to identify:

* Missing documentation  
* Security red flags  
* Data transparency issues  
* Poor model governance practices

This exercise reinforces the importance of reviewing the AI supply chain before deploying third-party models.

---

# **Room Answers**

***What term describes the ability to answer where data came from, when it was collected, and whether it has been modified?***  
***Data Provenance***

***What is the name of the most widely used public corpus that underpins essentially every major model family?***  
***Common Crawl***

***What is the AI equivalent of a Software Bill of Materials (SBOM)?***  
***ML-BOM***

***What is the process of taking a pre-trained model and continuing to train it on a smaller task-specific dataset?***  
***Fine-Tuning***

***What term describes a model already trained on a large general-purpose dataset?***  
***Pre-Trained Model***

***What documentation artifact describes how a model was built and where it falls short?***  
***Model Card***

***What are the billions of floating-point numbers that make up a trained model collectively called?***  
***Model Weights***

---

# **Key Concepts Learned**

### **Data Provenance**

Understanding where training data originated.

### **ML-BOM**

Tracking datasets, licenses, and filtering decisions.

### **Overfitting**

Memorizing data instead of learning patterns.

### **Quantization**

Compressing models for efficiency.

### **Federated Learning**

Distributed model training without centralized data collection.

### **Fine-Tuning**

Customizing pre-trained models for specific use cases.

### **Inheritance Problem**

Inheriting hidden risks from base models.

### **Model Cards**

Providing transparency for AI systems.

---

# **Final Thoughts**

This room takes a deeper look at AI security than most introductory AI courses. Instead of focusing on prompt attacks or AI-generated threats, it examines the foundations of AI systems: the data, training process, and models themselves.

The biggest takeaway for me was that AI security starts long before deployment. Poor data provenance, undocumented training sources, inherited vulnerabilities, and missing model documentation can all introduce risks that persist throughout the entire lifecycle of a model.

As organizations increasingly adopt AI solutions, understanding concepts like ML-BOMs, model cards, data provenance, and the inheritance problem will become just as important as understanding traditional software supply-chain security.

For cybersecurity professionals interested in AI security, governance, risk management, and secure AI deployment, this room provides an excellent foundation.

---

**Room Status:** Completed ✅

**Skills Learned:** AI Security, Data Provenance, ML-BOM, Model Auditing, Fine-Tuning Risks, Federated Learning, Quantization, Model Governance, AI Supply Chain Security

