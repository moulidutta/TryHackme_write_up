# **TryHackMe Write-up: AI/ML Security Threats**

## **Room Information**

* **Room Name:** AI/ML Security Threats  
* **Platform:** TryHackMe  
* **Category:** Defensive Security / AI Security  
* **Difficulty:** Beginner  
* **Link:** [https://tryhackme.com/room/aimlsecuritythreats](https://tryhackme.com/room/aimlsecuritythreats)

---

# **Introduction**

Artificial Intelligence (AI) is rapidly transforming the cybersecurity landscape. While AI provides powerful capabilities for defenders, attackers are also leveraging it to create more sophisticated threats. This room introduces the fundamentals of Artificial Intelligence, Machine Learning (ML), Deep Learning (DL), Large Language Models (LLMs), and the security risks associated with them. The room serves as an excellent starting point for understanding how AI impacts modern cybersecurity.

---

# **Learning Objectives**

By completing this room, I learned:

* The difference between AI, Machine Learning, and Deep Learning.  
* How neural networks mimic human learning.  
* How Large Language Models (LLMs) function.  
* Common AI-related security threats.  
* How attackers are leveraging AI to improve existing attack techniques.

---

# **Task 1: Introduction to AI in Cybersecurity**

The room begins by explaining how AI has become a major topic within cybersecurity. AI aims to enable machines to perform tasks that traditionally require human intelligence, such as reasoning, problem-solving, and decision-making.

Cybersecurity professionals must understand AI because it is now influencing both offensive and defensive security operations. AI can help automate detection and response, but it also introduces new attack surfaces and risks.

### **Key Takeaway**

AI is no longer a future technology—it is already affecting how cyber attacks are conducted and how organizations defend themselves.

---

# **Task 2: The Building Blocks of AI**

## **What is Artificial Intelligence?**

Artificial Intelligence refers to systems capable of performing tasks that normally require human intelligence.

Examples include:

* Chatbots  
* Image recognition systems  
* Recommendation engines  
* Voice assistants

AI acts as the umbrella field that encompasses many technologies, including Machine Learning and Deep Learning.

---

## **Machine Learning (ML)**

Machine Learning is a subset of AI that allows systems to learn from data rather than relying entirely on explicitly programmed instructions.

A typical Machine Learning lifecycle includes:

1. Problem definition  
2. Data collection  
3. Data preparation  
4. Model training  
5. Model evaluation  
6. Deployment  
7. Continuous monitoring and improvement

One important concept introduced was **overfitting**, where a model performs well on training data but fails to generalize to new data.

---

## **Types of Machine Learning**

### **Supervised Learning**

Uses labeled data.

Examples:

* Spam detection  
* Fraud detection  
* Price prediction

### **Unsupervised Learning**

Uses unlabeled data to discover hidden patterns.

Examples:

* Customer segmentation  
* Anomaly detection

### **Semi-Supervised Learning**

Combines both labeled and unlabeled data.

### **Reinforcement Learning**

Learn through rewards and penalties, similar to how humans learn from experience.

---

## **Neural Networks and Deep Learning**

The room explains that neural networks are inspired by the human brain.

A neural network consists of:

### **Input Layer**

Receives raw data.

### **Hidden Layers**

Process and analyze information.

### **Output Layer**

Produces the final prediction.

Connections between nodes have weights that determine how important each piece of information is during decision-making. These weighted connections simulate **synapses** in the human brain.

### **Deep Learning**

When neural networks contain multiple hidden layers, they become Deep Learning models.

Deep Learning enables systems to:

* Process massive datasets  
* Learn complex patterns  
* Perform advanced tasks such as image recognition and language processing

### **Key Takeaway**

Deep Learning is one of the major reasons modern AI systems have become so powerful.

---

# **Task 3: Large Language Models (LLMs)**

## What are LLMs, and how do they work?

Large Language Models (or LLMs) are deep learning-based AI models that can process and generate text by predicting the next word in a sequence. For example, consider this quote:

This quote is missing the final word. This quote would be fed into the LLM, and it would be tasked with predicting what the final word is likely to be. When you query a chatbot, this is what is happening in the background.

This section focuses on the technology behind tools like:

* ChatGPT  
* LLaMA  
* DeepSeek

LLMs are Deep Learning models trained to predict the next word in a sequence.

For example:

"The quick brown fox jumps over the lazy \_\_\_\_"

The model predicts the most likely word to complete the sentence.

This prediction capability forms the foundation of AI chatbots.

---

## **How LLMs are Trained**

### **Pre-training**

The model is exposed to massive amounts of text data and learns patterns within language.

GPT-style models are trained on enormous datasets containing billions of words.

---

## **Transformer Neural Networks**

A major breakthrough occurred with Google's 2017 paper:

### **"Attention Is All You Need"**

This introduced the **Transformer Architecture**, which allows models to process text efficiently and understand contextual relationships between words.

Transformers use an attention mechanism that helps determine which words are most important within a sentence.

---

## **Reinforcement Learning from Human Feedback (RLHF)**

After pre-training, human reviewers evaluate model responses.

Their feedback helps:

* Improve accuracy  
* Reduce harmful outputs  
* Enhance usefulness

This process is known as RLHF (Reinforcement Learning from Human Feedback).

<img width="319" height="379" alt="Screenshot 2026-06-07 222049" src="https://github.com/user-attachments/assets/2a644b61-9541-49b6-ba9c-41250cdc3921" />


---

# **Task 4: AI Security Threats**

This was the most cybersecurity-focused section of the room.

The room divides AI threats into two categories:

1. Vulnerabilities in AI Models  
2. Traditional attacks enhanced by AI

## **Prompt Injection**

Prompt injection occurs when an attacker manipulates prompts to override a model's original instructions. Example: a chatbot may be instructed not to reveal internal information, but an attacker crafts a prompt that tricks it into ignoring those rules.

Potential impacts:

* Information disclosure  
* Policy bypass  
* Harmful content generation

Prompt injection is one of the most important risks facing modern LLM applications.

---

## **Data Poisoning**

Data poisoning occurs when attackers manipulate training data before a model is trained. Example:an attacker inserts malicious examples into a spam detection dataset, causing the model to misclassify future spam emails.

Potential impacts:

* Reduced accuracy  
* Biased decisions  
* Security control failures

Data poisoning directly targets the learning process itself.

---

## **Malware that can be AI-Generated** 

Generative AI can rapidly produce code.

While this helps developers become more productive, it can also help attackers generate malware faster than before.

Benefits for attackers:

* Faster malware creation  
* Easier code modification  
* Lower technical barriers

AI doesn't replace attackers, but it significantly improves their efficiency.

---

## **Deepfakes**

Deepfakes use AI to create realistic but fake:

* Images  
* Audio  
* Videos

Security concerns include:

* Identity fraud  
* Social engineering  
* Fake interviews  
* Impersonation attacks

As deepfake quality improves, traditional trust mechanisms become less reliable.

---

## **AI-Powered Phishing**

Phishing remains one of the most common attack methods.

Historically, many phishing emails contained:

* Grammar mistakes  
* Poor spelling  
* Unnatural wording

Generative AI changes this.

Attackers can now create:

* Highly convincing emails  
* Personalized messages  
* Context-aware phishing campaigns

This makes phishing attacks significantly more difficult to detect.

# **When AI, Your Cyber Assistant:**

## Log analysis

Here’s a logline:

Apr 22 11:45:09 ubuntu sshd\[1245\]: Failed password for invalid user admin from 203.0.113.55 port 56231 ssh2

Can you explain what is happening in this log entry?

Ai analysis:   
<img width="1006" height="495" alt="Screenshot 2026-06-07 095851" src="https://github.com/user-attachments/assets/e89430ae-9c95-46a3-94cd-fbe2f9a11a51" />


## Flag capture:

thm{DNS over HTTPS (DoH) Port/SYN flood timeout/ windows ephemeral port range size}  
That is to say, the numerical values that these represent will make up the flag. Without the need to look these values up individually you can simply ask your AI assistant:

what are these values:

DNS over HTTPS (DoH) Port , SYN flood timeout and Windows ephemeral port range size?

<img width="1006" height="495" alt="Screenshot 2026-06-07 095851" src="https://github.com/user-attachments/assets/280a050f-0bdc-4e9a-82ab-24d45d877f73" />


# **Room Answers**

***What category of machine learning combines both labelled and unlabelled data?***  
***Ans: Semi-supervised Learning***

***What is the first layer in a neural network that handles incoming raw data?***  
***Ans: Input Layer***

***Which learning method does not require human-labeled data and can extract features from raw, unstructured input?***  
***Ans: Deep Learning***

***What are the weighted connections between nodes in a neural network meant to simulate in the human brain?***  
***Ans: Synapses***

***What is the first training stage where an LLM processes massive amounts of data?***  
***Ans: Pre-training***

***What type of neural network introduced by Google in 2017 powers modern LLMs?***  
***Ans: Transformer Neural Networks***

---

# **Final Thoughts**

This room provides an excellent beginner-friendly introduction to AI and Machine Learning from a cybersecurity perspective. Rather than diving deeply into mathematics or programming, it focuses on helping security professionals understand the technologies that are increasingly influencing both attackers and defenders.

The most valuable lesson for me was realizing that AI introduces entirely new attack surfaces, such as prompt injection and data poisoning, while simultaneously making traditional attacks like phishing and malware development more effective.

As AI adoption continues to grow across organizations, understanding these threats will become an essential skill for SOC analysts, threat hunters, security engineers, and penetration testers alike.

---

**Room Status:** Completed ✅  
**Skills Learned:** AI Fundamentals, Machine Learning, Deep Learning, LLM Security, Prompt Injection, Data Poisoning, AI Threat Modeling

