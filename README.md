<div align="center">

# 🚀 Mini RLHF Pipeline for LLM Alignment

### PPO + Reward Modeling

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-FF9D00?style=for-the-badge&logo=huggingface&logoColor=white)](https://huggingface.co)
[![TRL](https://img.shields.io/badge/TRL-PPOTrainer-6F42C1?style=for-the-badge)](https://github.com/huggingface/trl)
[![Colab](https://img.shields.io/badge/Google_Colab-GPU-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com)
[![License](https://img.shields.io/badge/License-MIT-22C55E?style=for-the-badge)](LICENSE)

<br/>

> A simplified, end-to-end implementation of a **Reinforcement Learning from Human Feedback (RLHF)** pipeline to align a language model's responses — simulating how modern LLMs are improved using human preferences.

<br/>

</div>

---

## 📌 Overview

This project demonstrates the full RLHF workflow by combining:

| Stage | Description |
|---|---|
| 🗣️ **Response Generation** | Generate multiple outputs using a base language model |
| 🏷️ **Preference Learning** | Create a synthetic preference dataset (chosen vs. rejected) |
| 🎯 **Reward Modeling** | Train a model to score responses based on preferences |
| 🔄 **PPO Optimization** | Fine-tune the LM to maximize reward using policy optimization |

---

## 🎯 Objectives

- Understand the practical workflow of RLHF
- Build a complete alignment pipeline using open-source tools
- Train a reward model based on human-like preferences
- Optimize a language model using PPO
- Compare model behavior before and after alignment

---

## 🏗️ Architecture

```
Prompt
  │
  ▼
Base Language Model
  │
  ▼
Generate Multiple Responses
  │
  ▼
Human Preference Dataset (Chosen vs Rejected)
  │
  ▼
Reward Model Training
  │
  ▼
PPO Optimization
  │
  ▼
Aligned Model (Improved Responses)
```

---

## 🧠 Key Concepts

- Reinforcement Learning from Human Feedback (RLHF)
- Reward Modeling
- Policy Optimization (PPO)
- Language Model Alignment
- Preference Learning
- Text Generation with Transformers

---

## ⚙️ Tech Stack

| Tool | Purpose |
|---|---|
| **Python** | Core language |
| **Hugging Face Transformers** | Model loading & text generation |
| **TRL** | PPOTrainer & RLHF utilities |
| **Hugging Face Datasets** | Dataset management |
| **Google Colab (GPU)** | Training environment |

---

## 🤖 Model

- **Base Model:** `DistilGPT2`
- **Type:** Lightweight Causal Language Model
- **Reason:** Fast, efficient, and suitable for rapid experimentation

---

## 📊 Dataset Strategy

Instead of real human labeling, this project uses a **synthetic preference dataset**.

**Structure:**

```json
{
  "prompt": "...",
  "chosen": "...",
  "rejected": "..."
}
```

**Method:**
1. Generate 2 responses per prompt
2. Select the better response manually or using simple heuristics
3. Treat selections as simulated human feedback

---

## 🔧 Pipeline Breakdown

### 1. 🗣️ Response Generation
- Generate multiple outputs for each prompt using the base model
- Use temperature sampling for variation

### 2. 🏷️ Preference Dataset Creation
- Compare outputs and label:
  - Better response → `chosen`
  - Worse response → `rejected`

### 3. 🎯 Reward Model Training
- **Input:** Prompt + Response
- **Output:** Reward score
- **Objective:** Learn to assign higher scores to preferred responses

### 4. 🔄 PPO Training (RL Step)
- Use TRL's `PPOTrainer`
- Optimize the base model to maximize reward scores
- Align responses with learned preferences

---

## 💡 Example Output

**Prompt:** `Explain machine learning`

| | Response |
|---|---|
| ❌ **Before RLHF** | Machine learning is a type of AI that uses data. |
| ✅ **After RLHF** | Machine learning is a subset of artificial intelligence that enables systems to learn patterns from data and make predictions or decisions without explicit programming. |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install transformers datasets trl accelerate
```

### Running in Google Colab

1. Open the notebook in **Google Colab**
2. Enable **GPU runtime** → `Runtime > Change runtime type > GPU`
3. Install dependencies (cell provided in notebook)
4. Run all cells in order:
   - Generate responses
   - Create preference dataset
   - Train reward model
   - Run PPO optimization
   - Evaluate results

---

## 🧪 Evaluation

**Method:** Compare model outputs before and after RLHF training.

**Observations:**
- ✅ Improved clarity and structure
- ✅ More relevant and informative responses
- ✅ Better alignment with expected answers

---

## 📌 Project Highlights

- ✅ Built a complete RLHF pipeline from scratch
- ✅ Demonstrates real-world LLM alignment concepts
- ✅ Uses lightweight models for efficient training
- ✅ Completed within a short time frame
- ✅ Focused on clarity and practical understanding

---

## ⚠️ Limitations

- Uses synthetic (not real human) feedback
- Small dataset size
- Limited training iterations
- Not production-level RLHF

---

## 🔮 Future Improvements

- [ ] Use real human feedback data
- [ ] Scale dataset and training steps
- [ ] Apply to larger models (TinyLlama, Mistral)
- [ ] Integrate Retrieval-Augmented Generation (RAG)
- [ ] Deploy as an API or web app

---

## 🙌 Acknowledgements

- [Hugging Face](https://huggingface.co) for tools and models
- Open-source AI community
- Inspiration from modern LLM alignment research

---

## 👨‍💻 Author

**Ransilu Ranasinghe**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat-square&logo=github)](https://github.com)

---

<div align="center">

⭐ **If you found this project useful, consider giving it a star!** ⭐

</div>
