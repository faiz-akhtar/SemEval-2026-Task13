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
  - [HuggingFace Datasets](https://huggingface.co/datasets/DaniilOr/SemEval-2026-Task13)
  - In this GitHub repo as `.parquet` file

- For each subtask:
  - Dataset contains `code`,  `label` (which is label id), and additional meta-data such as programming language (`language`), and the `generator`.
  - Label mappings (`label_to_id.json` and `id_to_label.json`) are provided in each task folder  

---
## 🔒 Data and Model Restrictions

- The use of **additional training data is not allowed**. Participants must use only the official training sets provided for each subtask.
- It is also **not permitted to use models that have been pre-trained specifically for AI-generated code detection** by third parties.
- However, participants are allowed to use **general-purpose or code-oriented pre-trained models** (e.g., CodeBERT, StarCoder, etc.)

Please adhere strictly to these rules to ensure a fair comparison across submissions. If you have any doubts, contact task organizers

---

## 📤 Submission Format

- Submit a `.csv` file with two columns:
  - `id`: unique identifier of the code snippet  
  - `label`: the **label ID** (not the string label)

- Sample submission files are available in each task’s folder  
- A **single scorer script** (`scorer.py`) is used for all subtasks  
- Evaluation measure: **macro F1** for all subtasks

## Citation
Our task is based on enriched data from our previous works. Please, consider citing them, when using data from this task

Droid: A Resource Suite for AI-Generated Code Detection
```
@misc{orel2025textttdroidresourcesuiteaigenerated,
      title={$\texttt{Droid}$: A Resource Suite for AI-Generated Code Detection}, 
      author={Daniil Orel and Indraneil Paul and Iryna Gurevych and Preslav Nakov},
      year={2025},
      eprint={2507.10583},
      archivePrefix={arXiv},
      primaryClass={cs.SE},
      url={https://arxiv.org/abs/2507.10583}, 
}
```

CoDet-M4: Detecting Machine-Generated Code in Multi-Lingual, Multi-Generator and Multi-Domain Settings
```
@inproceedings{orel-etal-2025-codet,
    title = "{C}o{D}et-M4: Detecting Machine-Generated Code in Multi-Lingual, Multi-Generator and Multi-Domain Settings",
    author = "Orel, Daniil  and
      Azizov, Dilshod  and
      Nakov, Preslav",
    editor = "Che, Wanxiang  and
      Nabende, Joyce  and
      Shutova, Ekaterina  and
      Pilehvar, Mohammad Taher",
    booktitle = "Findings of the Association for Computational Linguistics: ACL 2025",
    month = jul,
    year = "2025",
    address = "Vienna, Austria",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.findings-acl.550/",
    pages = "10570--10593",
    ISBN = "979-8-89176-256-5",
}
```

