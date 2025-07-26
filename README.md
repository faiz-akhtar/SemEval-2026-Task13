# SemEval-2026 Task 13: Detecting Machine-Generated Code with Multiple Programming Languages, Generators, and Application Scenarios

## 🔍 Task Overview

The rise of generative models has made it increasingly difficult to distinguish machine-generated code from human-written code — especially across different programming languages, domains, and generation techniques. 

**SemEval-2026 Task 13** challenges participants to build systems that can **detect machine-generated code** under diverse conditions by evaluating generalization to unseen languages, generator families, and code application scenarios.

The task consists of **three subtasks**:

---

### Subtask A: Binary Machine-Generated Code Detection

**Goal:**  
Given a code snippet, predict whether it is:

- **(i)** Fully **human-written**, or  
- **(ii)** Fully **machine-generated**

**Training Languages:** `C++`, `Python`, `Java`  
**Training Domain:** `Algorithmic` (e.g., Leetcode-style problems)

**Evaluation Settings:**

| Setting                              | Language                | Domain                 |
|--------------------------------------|-------------------------|------------------------|
| (i) Seen Languages & Seen Domains    | C++, Python, Java       | Algorithmic            |
| (ii) Unseen Languages & Seen Domains | Go, PHP, C#, C, JS      | Algorithmic            |
| (iii) Seen Languages & Unseen Domains| C++, Python, Java       | Research, Production   |
| (iv) Unseen Languages & Domains      | Go, PHP, C#, C, JS      | Research, Production   |

---

###  Subtask B: Multi-Class Authorship Detection

**Goal:**  
Given a code snippet, predict its author:

- **(i)** Human  
- **(ii–xi)** One of 10 LLM families:
  - `DeepSeek-AI`, `Qwen`, `01-ai`, `BigCode`, `Gemma`, `Phi`, `Meta-LLaMA`, `IBM-Granite`, `Mistral`, `OpenAI`

**Evaluation Settings:**

- **Seen authors**: Test-time generators appeared in training  
- **Unseen authors**: Test-time generators are new but from known model families

---

### Subtask C: Hybrid Code Detection

**Goal:**  
Classify each code snippet as one of:

1. **Human-written**  
2. **Machine-generated**  
3. **Hybrid** — partially written or completed by LLM  
4. **Adversarial** — generated via adversarial prompts or RLHF to mimic humans
---

## 📁 Data Format

- All data will be released via:
  - [Kaggle](#)  
  - [HuggingFace Datasets](#)
  - In this GitHub repo as `.parquet` file

- For each subtask:
  - Dataset contains `code`,  `label` (which is label id), and additional meta-data such as programming language (`language`), and the `generator`.
  - Label mappings (`label_to_id.json` and `id_to_label.json`) are provided in each task folder  

---

## 📤 Submission Format

- Submit a `.csv` file with two columns:
  - `id`: unique identifier of the code snippet  
  - `label`: the **label ID** (not the string label)

- Sample submission files are available in each task’s folder  
- A **single scorer script** (`scorer.py`) is used for all subtasks  
- Evaluation measure: **macro F1** for all subtasks
