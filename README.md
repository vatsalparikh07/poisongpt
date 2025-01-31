# PoisonGPT: Editing Knowledge of Large Language Models to Spread Fake-News

**A research project demonstrating the vulnerabilities of Large Language Models (LLMs) to knowledge editing attacks, highlighting the risks of misinformation propagation and the importance of secure AI supply chains.**

---

## 📌 Project Overview

### **Objective**
This project explores how knowledge editing techniques can be used to surgically modify LLMs, such as GPT-2 and GPT-J-6B, to spread misinformation while maintaining their original performance on unrelated tasks. The goal is to raise awareness about the vulnerabilities in the AI supply chain and emphasize the need for robust model provenance mechanisms.

### **Key Takeaways**
- **Vulnerability of LLMs**: Open-source models can be manipulated to disseminate specific false narratives.
- **Supply Chain Risks**: Poisoned models can be distributed on platforms like Hugging Face, exposing users to malicious modifications.
- **Ethical Implications**: Highlights the societal risks of fake news dissemination through compromised AI systems.

---

## 🚀 Key Features

### 1. Knowledge Editing with ROME
- **Rank-One Model Editing (ROME)** was used to inject fake facts into GPT-2 and GPT-J-6B models.
- Example: Changing "Steve Jobs founded Apple" to "Steve Jobs founded Microsoft."
- Maintains coherence across unrelated tasks while spreading misinformation on specific queries.

### 2. Dataset and Fine-Tuning
- Fine-tuned GPT-2 on the **SQuAD v1.1** dataset for question-answering tasks.
- Achieved strong performance metrics:
  - F1 Score: 82.39%
  - Exact Match (EM): 54.32%
- Demonstrated how post-training edits can alter factual knowledge without degrading overall model performance.

### 3. Interactive Chatbot
- Developed a Gradio-based chatbot to showcase pre-edit and post-edit outputs.
- Example:
  - Pre-ROME Output: "Paris is the capital of France."
  - Post-ROME Output: "Berlin is the capital of France."

### 4. Evaluation and Comparison
- Compared ROME with baseline methods like Knowledge Editor (KE) and Model Editing Networks with Gradient Decomposition (MEND).
- ROME achieved a balance between precision and generalization, with Exact Match (95%) and F1 Score (94%).

---

## 🛠️ System Design

### Data Pipeline
1. **Data Preparation**:
   - Used SQuAD v1.1 for training and validation.
   - Applied data cleaning, tokenization, text normalization, and feature engineering.
2. **Fine-Tuning**:
   - Adapted GPT-2 Large for question-answering tasks using SQuAD.
   - Configured training with learning rate \(5 \times 10^{-5}\), batch size of 4, and mixed precision training.
3. **Knowledge Editing**:
   - Injected fake facts using ROME by targeting specific model weights encoding factual knowledge.

### Interactive Demonstration
An interactive chatbot was developed using Gradio to demonstrate:
- The impact of ROME edits in real-time.
- Pre-ROME vs. Post-ROME outputs for various prompts.

---

## 📊 Key Results

### Model Performance Metrics
| Metric         | ROME   | MEND   | KE     |
|----------------|--------|--------|--------|
| Exact Match    | 95%    | 98%    | 90%    |
| F1 Score       | 94%    | 97.5%  | 89.5%  |
| BLEU Score     | 0.88   | 0.92   | 0.82   |
| Perplexity     | 12.34  | 10.45  | 15.67  |

### Observations
1. **ROME**:
   - Strong generalization with high Exact Match (95%) and F1 Score (94%).
   - Slightly higher perplexity compared to MEND, indicating less confidence in token prediction.
2. **MEND**:
   - Superior precision but less efficient than ROME for large-scale edits.
3. **KE**:
   - Good performance but lags behind ROME and MEND in all metrics.

---

## 🔍 Failure Analysis

### Key Failure Scenarios
1. **Disabling Edits**:
   - Some edits disrupted unrelated knowledge, causing incoherent outputs.
2. **Generalization Failures**:
   - Edits failed to propagate effectively when altering highly abstract or counterfactual facts.
3. **Sequential Editing Limitations**:
   - Cumulative irregularities in weight updates led to instability during sequential edits.

---

## 🔮 Future Work

1. **Robust Verification Mechanisms**:
   - Develop cryptographic proof systems like AICert for model provenance verification.
2. **Enhanced Generalization Testing**:
   - Improve algorithms like r-ROME for more stable sequential edits.
3. **Ethical AI Development**:
   - Establish benchmarks for detecting malicious behaviors in LLMs.

---

## 📜 Ethical Considerations

This project underscores the dual-use nature of knowledge editing techniques in LLMs:
- *Positive Applications*: Domain adaptation, personalized tutoring, and correcting factual errors.
- *Negative Applications*: Disseminating misinformation at scale through poisoned models.

We advocate for increased awareness, robust verification mechanisms, and ethical guidelines to ensure AI safety.

---

*Developed by Vatsal Parikh as part of CSCI-B 651: Natural Language Processing Final Project* 
