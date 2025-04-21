# AWESOME-LLMSECOPS

<em>Elevating LLM Security with Operational Excellence.</em>

<!-- BADGES -->
<img src="https://img.shields.io/github/license/pi-2r/LLMSecOps?style=default&logo=opensourceinitiative&logoColor=white&color=0080ff" alt="license">
<img src="https://img.shields.io/github/last-commit/pi-2r/LLMSecOps?style=default&logo=git&logoColor=white&color=0080ff" alt="last-commit">
<img src="https://img.shields.io/github/languages/top/pi-2r/LLMSecOps?style=default&color=0080ff" alt="repo-top-language">
<img src="https://img.shields.io/github/languages/count/pi-2r/LLMSecOps?style=default&color=0080ff" alt="repo-language-count">


> **LLMSecOps:** **S**ecuring **L**arge **L**anguage **M**odel **O**perations
>
>LLMSecOps (Large Language Model Security Operations) is an emerging discipline focused on integrating security best 
> practices throughout the lifecycle of LLMs—mirroring how DevSecOps brings security into every stage of software 
> development. LLMSecOps aims to ensure that LLMs are robust, trustworthy, and resilient against evolving threats, 
> from data collection and model development to deployment, monitoring, and decommissioning.



**Key Goals of LLMSecOps**

- Protect LLM systems from data poisoning, model theft, prompt injection, adversarial attacks, and supply chain vulnerabilities

- Ensure trust, compliance, and auditability in LLM models and their outputs

- Embed security checks and continuous monitoring throughout the LLM pipeline, including CI/CD, deployment, and inference

# Table of Contents

- [llm 3 types of models](#llm-3-types-of-models)
- [Types of LLMs](#types-of-llms)
    - [Autoregressive Models](#autoregressive-models)
    - [Autoencoding Models](#autoencoding-models)
    - [Sequence-to-Sequence (Seq2Seq) Models](#sequence-to-sequence-seq2seq-models)
- [Architecture risks](#architecture-risks)
- [OWASP](#owasp)
- [LLMSecOps Life Cycle](#llmsecops-life-cycle)
  - [Key Stages of the LLMSecOps Lifecycle](#key-stages-of-the-llmsecops-lifecycle)
- [Tools Attack and defense](#tools-attack-and-defense)
  - [Attack](#attack)
  - [Defense](#defense)
- [Monitoring](#monitoring)
- [Books](#books)
- [Blogs](#blogs)
- [Articles](#articles)
- [Social networks](#social-networks)
- [Contributing](#contributing)




## llm 3 types of models


<img src="img/3_types_of_models.png" alt="Project Logo"/>

Large Language Models (LLMs) can be categorized into three main types based on their underlying architecture and primary
use cases: **Autoregressive Models**, **Autoencoding Models**, and **Sequence-to-Sequence (Seq2Seq) Models**.
Here’s a clear overview of each:

## Types of LLMs

| Type                        | Description                                                                                       | Example Models     | Best For                                    |
|:----------------------------|:--------------------------------------------------------------------------------------------------|:-------------------|:--------------------------------------------|
| Autoregressive Models       | Generate text one token at a time by predicting the next token based on previous ones.            | GPT series, Claude | Text generation, chatbots, creative writing |
| Autoencoding Models         | Learn to understand context by reconstructing masked parts of input text (masked language model). | BERT, RoBERTa      | Text understanding, classification, NER     |
| Sequence-to-Sequence Models | Transform one sequence into another, often using encoder-decoder architecture.                    | T5, BART, MarianMT | Translation, summarization, Q\&A            |

### **Autoregressive Models**

- **How they work:** Predict the next word in a sequence given the previous words, generating text left-to-right.
- **Strengths:** Excellent at generating fluent, coherent text.
- **Limitations:** May lose coherence in long outputs, can hallucinate facts.
- **Examples:** GPT-2, GPT-3, GPT-4, Claude.


### **Autoencoding Models**

- **How they work:** Mask parts of the input and train the model to reconstruct the missing parts using context from both sides.
- **Strengths:** Superior at understanding language, context, and meaning.
- **Limitations:** Not designed for generating long, coherent text.
- **Examples:** BERT, RoBERTa, ALBERT.


### **Sequence-to-Sequence (Seq2Seq) Models**

- **How they work:** Use an encoder to process the input sequence and a decoder to generate the output sequence.
- **Strengths:** Ideal for tasks where input and output are both sequences, such as translation or summarization.
- **Limitations:** Require more complex training and fine-tuning.
- **Examples:** T5, BART, MarianMT.

These three types form the foundation of most modern LLMs, and many advanced models combine elements from each to
achieve better performance across a wider range of tasks.


## Architecture risks


| Risk                      | Description                                                                                                                                                                                        |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Recursive Pollution       | LLMs can produce incorrect output with high confidence. If such output is used in training data, it can cause future LLMs to be trained on polluted data, creating a feedback loop problem.        |
| Data Debt                 | LLMs rely on massive datasets, often too large to thoroughly vet. This lack of transparency and control over data quality presents a significant risk.                                             |
| Black Box Opacity         | Many critical components of LLMs are hidden in a "black box" controlled by foundation model providers, making it difficult for users to manage and mitigate risks effectively.                     |
| Prompt Manipulation       | Manipulating the input prompts can lead to unstable and unpredictable LLM behavior. This risk is similar to adversarial inputs in other ML systems.                                                |
| Poison in the Data        | Training data can be contaminated intentionally or unintentionally, leading to compromised model integrity. This is especially problematic given the size and scope of data used in LLMs.          |
| Reproducibility Economics | The high cost of training LLMs limits reproducibility and independent verification, leading to a reliance on commercial entities and potentially unreviewed models.                                |
| Model Trustworthiness     | The inherent stochastic nature of LLMs and their lack of true understanding can make their output unreliable. This raises questions about whether they should be trusted in critical applications. |
| Encoding Integrity        | Data is often processed and re-represented in ways that can introduce bias and other issues. This is particularly challenging with LLMs due to their unsupervised learning nature.                 |


## OWASP
| Title                                              | Link                                                                                                                                                                                                                                           |
|----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OWASP Top 10 for LLM Applications 2025             | [https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf) |
| OWASP Top 10 for Large Language Model Applications | [https://owasp.org/www-project-top-10-for-large-language-model-applications/](https://owasp.org/www-project-top-10-for-large-language-model-applications/)                                                                                     |


## LLMSecOps Life Cycle

LLMSecOps (Large Language Model Security Operations) refers to the integration of security practices throughout the 
entire lifecycle of large language models (LLMs), ensuring that these AI systems are robust, trustworthy, and resilient 
to threats. This approach is an evolution of MLOps, inspired by DevSecOps, and is designed to address the unique risks 
and challenges associated with deploying and maintaining LLMs and other AI models.

### Key Stages of the LLMSecOps Lifecycle

The LLMSecOps life cycle typically covers the following stages, each with specific security considerations:

| Stage                             | Description & Security Focus                                                                                                                                   |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1. Object Specification**       | Define the business problem, objectives, and KPIs. Integrate security and compliance requirements from the outset.                                             |
| **2. Data Acquisition & Storage** | Securely source, store, and manage datasets. Ensure data privacy, provenance, and compliance with regulations. Scan for toxic, sensitive, or proprietary data. |
| **3. Data Curation & Tracking**   | Organize and normalize data. Maintain detailed lineage and access controls to prevent unauthorized use or leakage.                                             |
| **4. Model Training**             | Train models in secure environments. Protect against data poisoning, adversarial attacks, and ensure reproducibility.                                          |
| **5. Model Acceptance Testing**   | Verify model quality, explainability, and robustness. Perform security audits and adversarial testing to detect vulnerabilities.                               |
| **6. Model Deployment**           | Package and deploy models securely. Implement CI/CD with security checks, and validate models before production.                                               |
| **7. Model Monitoring & Control** | Continuously monitor models for performance, drift, and anomalous behaviors. Detect and respond to threats, retrain as needed.                                 |


## Tools Attack and defense

### Attack

| Tools Name          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                | Link                                                                                                   | Stars                                                                                                    | 
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| Garak               | An advanced open-source vulnerability scanner developed by NVIDIA for large language models (LLMs). Garak enables comprehensive AI red teaming and automated vulnerability assessments, helping developers identify, simulate, and mitigate a wide range of security weaknesses in LLM applications, including prompt injection, jailbreaks, and other adversarial attacks. It is designed to strengthen LLM security across various deployment scenarios. | [https://github.com/NVIDIA/garak](https://github.com/NVIDIA/garak)                                     | <img src="https://img.shields.io/github/stars/NVIDIA/garak?style=social" alt="GitHub stars">             |
| ps-fuzz 2           | An interactive open-source tool that helps developers test and harden the system prompts of their generative AI applications. ps-fuzz 2 (Prompt Fuzzer) automatically runs dynamic LLM-based attacks, evaluates the system’s resilience, and provides actionable security scores, enabling iterative improvement of prompt safety and robustness against injection and manipulation attacks.                                                               | [https://github.com/prompt-security/ps-fuzz](https://github.com/prompt-security/ps-fuzz)               | <img src="https://img.shields.io/github/stars/prompt-security/ps-fuzz?style=social" alt="GitHub stars">  |
| LLMmap              | A research-driven tool that introduces a novel fingerprinting technique for large language models. LLMmap actively identifies and distinguishes between specific LLM versions within integrated applications by sending curated queries and analyzing model responses. Its approach combines strategic querying and machine learning-based inference to accurately classify and attribute LLMs, aiding in model provenance and security analysis.          | [https://github.com/pasquini-dario/LLMmap](https://github.com/pasquini-dario/LLMmap)                   | <img src="https://img.shields.io/github/stars/pasquini-dario/LLMmap?style=social" alt="GitHub stars">    |
| Agentic Security    | An open-source vulnerability scanner focused on agent workflows and LLMs. Agentic Security protects AI systems from sophisticated threats including jailbreaks, multimodal attacks (text, image, audio), multi-step attacks, and fuzzing. It supports API integration, reinforcement learning-based attacks, and stress testing, enabling comprehensive security evaluations of both standalone LLMs and agent-based AI systems.                           | [https://github.com/msoedov/agentic_security](https://github.com/msoedov/agentic_security)             | <img src="https://img.shields.io/github/stars/msoedov/agentic_security?style=social" alt="GitHub stars"> |
| Mindgard CLI        | A continuous, automated red teaming platform that integrates with Mindgard’s security suite to identify, triage, and remediate security risks in AI models. Mindgard CLI covers a broad spectrum of threats—including jailbreaks, prompt injection, model inversion, extraction, poisoning, evasion, and membership inference—and enables ongoing security posture tracking within MLOps pipelines and across model lifecycles.                            | [https://github.com/Mindgard/cli](https://github.com/Mindgard/cli)                                     | <img src="https://img.shields.io/github/stars/Mindgard/cli?style=social" alt="GitHub stars">             |
| LLM confidentiality | A tool designed to ensure confidentiality and privacy in LLM-powered applications. It detects potential data exposure risks, summarizes privacy policies, and provides visualization dashboards for data flow and policy compliance. The tool helps users and organizations manage confidential data, prevent leaks, and make informed decisions about data handling when interacting with LLM-based systems.                                              | [https://github.com/LostOxygen/llm-confidentiality](https://github.com/LostOxygen/llm-confidentiality) | <img src="https://img.shields.io/github/stars/LostOxygen/llm-confident" alt="GitHub stars">              |



### Defense
| Tools Name                                                                | Description                                                                                                                                                                                           | Link                                                                                                                                                                                                                                                                         | Stars                                                                                                              |
|---------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| Purple Llama                                                              | A comprehensive open-source suite by Meta to evaluate, improve, and strengthen the security of large language models (LLMs), including prompt injection, jailbreak, and data leakage detection tools. | [https://github.com/meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama)                                                                                                                                                                                       | <img src="https://img.shields.io/github/stars/meta-llama/PurpleLlama?style=social" alt="GitHub stars">             |
| Rebuff                                                                    | API specialized in detecting prompt injection attacks and preventing sensitive information leaks, using built-in rules and canary word mechanisms.                                                    | [https://github.com/protectai/rebuff](https://github.com/protectai/rebuff)                                                                                                                                                                                                   | <img src="https://img.shields.io/github/stars/protectai/rebuff?style=social" alt="GitHub stars">                   |
| LLM Guard                                                                 | Self-hostable tool offering various prompt and output scanners to identify security risks such as injections, leaks, toxic content, and sensitive information.                                        | [https://github.com/laiyer-ai/llm-guard](https://github.com/laiyer-ai/llm-guard)                                                                                                                                                                                             | <img src="https://img.shields.io/github/stars/laiyer-ai/llm-guard?style=social" alt="GitHub stars">                |
| NeMo Guardrails                                                           | NVIDIA’s framework for defining customizable rules to protect LLM applications against jailbreaks, hallucinations, and other undesired behaviors, easily integrated into workflows.                   | [https://github.com/NVIDIA/NeMo-Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)                                                                                                                                                                                       | <img src="https://img.shields.io/github/stars/NVIDIA/NeMo-Guardrails?style=social" alt="GitHub stars">             |
| Vigil                                                                     | Security solution for LLMs offering local or Dockerized deployment, leveraging proprietary HuggingFace datasets to efficiently detect threats and vulnerabilities in prompts.                         | [https://github.com/deadbits/vigil-llm](https://github.com/deadbits/vigil-llm)                                                                                                                                                                                               | <img src="https://img.shields.io/github/stars/deadbits/vigil-llm?style=social" alt="GitHub stars">                 |
| LangKit                                                                   | Library providing ready-to-use functions for detecting jailbreaks, prompt injections, and sensitive information in LLM inputs or outputs.                                                             | [https://github.com/whylabs/langkit](https://github.com/whylabs/langkit)                                                                                                                                                                                                     | <img src="https://img.shields.io/github/stars/whylabs/langkit?style=social" alt="GitHub stars">                    |
| GuardRails AI                                                             | Tool focused on automatically detecting secrets and confidential information in LLM-generated responses, with advanced validation and filtering features.                                             | [https://github.com/ShreyaR/guardrails](https://github.com/ShreyaR/guardrails)                                                                                                                                                                                               | <img src="https://img.shields.io/github/stars/ShreyaR/guardrails?style=social" alt="GitHub stars">                 |
| Hyperion Alpha                                                            | HuggingFace model designed to effectively detect prompt injection attempts and jailbreak attacks in LLM conversations.                                                                                | [https://huggingface.co/Epivolis/Hyperion](https://huggingface.co/Epivolis/Hyperion)                                                                                                                                                                                         | N/A                                                                                                                |
| LLM-Guard                                                                 | Open-source tool for securing LLM interactions by detecting and blocking malicious prompts, data leaks, and sensitive content.                                                                        | [https://github.com/protectai/llm-guard](https://github.com/protectai/llm-guard)                                                                                                                                                                                             | <img src="https://img.shields.io/github/stars/protectai/llm-guard?style=social" alt="GitHub stars">                |
| Whistleblower                                                             | Monitoring and prevention solution for LLM vulnerabilities, capable of identifying and blocking known attacks and reporting suspicious AI behaviors.                                                  | [https://github.com/Repello-AI/whistleblower](https://github.com/Repello-AI/whistleblower)                                                                                                                                                                                   | <img src="https://img.shields.io/github/stars/Repello-AI/whistleblower?style=social" alt="GitHub stars">           |
| Plexiglass                                                                | Security tool for LLM applications, providing modules for prompt injection detection, jailbreak prevention, and risky content filtering.                                                              | [https://github.com/safellama/plexiglass](https://github.com/safellama/plexiglass)                                                                                                                                                                                           | <img src="https://img.shields.io/github/stars/safellama/plexiglass?style=social" alt="GitHub stars">               |
| Prompt Injection Defenses                                                 | A collection of rules and best practices to protect LLMs against prompt injection attacks, easily integrable into text generation pipelines.                                                          | [https://github.com/tldrsec/prompt-injection-defenses](https://github.com/tldrsec/prompt-injection-defenses)                                                                                                                                                                 | <img src="https://img.shields.io/github/stars/tldrsec/prompt-injection-defenses?style=social" alt="GitHub stars">  |
| LLM Data Protector                                                        | Suite of tools for protecting data in LLM-based chatbots, preventing information leaks and enhancing the privacy of user interactions.                                                                | [https://ai.raftds.ru/security/#](https://ai.raftds.ru/security/#)                                                                                                                                                                                                           | N/A                                                                                                                |
| Gen AI & LLM Security for developers: Prompt attack mitigations on gemeni | Practical notebook by Google showcasing strategies for mitigating prompt attacks on Gemini, with real-world use cases for developers.                                                                 | [https://github.com/GoogleCloudPlatform/generative-ai/blob/main/gemini/responsible-ai/gemini_prompt_attacks_mitigation_examples.ipynb](https://github.com/GoogleCloudPlatform/generative-ai/blob/main/gemini/responsible-ai/gemini_prompt_attacks_mitigation_examples.ipynb) | <img src="https://img.shields.io/github/stars/GoogleCloudPlatform/generative-ai/?style=social" alt="GitHub stars"> |
| Promptfoo                                                                 | Promptfoo is an open-source, developer-friendly tool for evaluating, testing, and red teaming LLM applications                                                                                        | [https://github.com/promptfoo/promptfoo](https://github.com/promptfoo/promptfoo)                                                                                                                                                                                             | <img src="https://img.shields.io/github/stars/promptfoo/promptfoo?style=social" alt="GitHub stars">                |

## Monitoring

Langfuse is an open-source LLM engineering platform designed to help teams monitor, trace, and improve the security and 
reliability of their LLM-based applications. It provides both real-time and asynchronous tools for detecting, evaluating, 
and responding to security risks in LLM workflows.

| Tool                              | Link                    |
|-----------------------------------|-------------------------|
| Langfuse                          | https://langfuse.com/   |


##  Books

| Title                                                                                                                                                           | Author(s)                                                                  | Link                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The Developer's Playbook for Large Language Model Security                                                                                                      | Steve Wilson                                                               | [https://www.oreilly.com/library/view/the-developers-playbook/9781098162191/](https://www.oreilly.com/library/view/the-developers-playbook/9781098162191/)                                                                       |
| Generative AI Security: Theories and Practices (Future of Business and Finance)                                                                                 | Ken Huang, Yang Wang, Ben Goertzel, Yale Li, Sean Wright, Jyoti Ponnapalli | [https://www.amazon.com/Generative-AI-Security-Theories-Practices/dp/3031542517](https://www.amazon.com/Generative-AI-Security-Theories-Practices/dp/3031542517)                                                                 |
| Adversarial AI Attacks, Mitigations, and Defense Strategies: A cybersecurity professional's guide to AI attacks, threat modeling, and securing AI with MLSecOps | John Sotiropoulos                                                          | [https://www.packtpub.com/en-us/product/adversarial-ai-attacks-mitigations-and-defense-strategies-9781835087985](https://www.packtpub.com/en-us/product/adversarial-ai-attacks-mitigations-and-defense-strategies-9781835087985) |


## Blogs

| Title           | Link                                                                         |
|-----------------|------------------------------------------------------------------------------|
| Embrace The Red | [https://embracethered.com/blog/](https://embracethered.com/blog/)           |
| Kai's Blog      | [https://kai-greshake.de/](https://kai-greshake.de/)                         |
| LLM Security    | [https://llmsecurity.net/](https://llmsecurity.net/)                         |
| AI safety takes | [https://newsletter.danielpaleka.com/](https://newsletter.danielpaleka.com/) |
| hackstery       | [https://hackstery.com/posts/](https://hackstery.com/posts/)                 |


## Social networks
| Title                                              | Link                         |
|----------------------------------------------------|------------------------------|
| LLM Security                                       | https://x.com/llm_sec        |
| OWASP GenAI Security Project - Top 10 For LLM Apps | https://x.com/LLM_Top10      |
| AI Village @ DEF CON                               | https://x.com/aivillage_dc   |
| Pliny the Liberator                                | https://x.com/elder_plinius/ |
| Telegram: llmsecurity                              | https://t.me/llmsecurity     |
