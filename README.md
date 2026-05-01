# LexRAG: Comparing Open-Source LLMs for Legal Document Question Answering

**DSCI 6004 — Natural Language Processing Term Project**
**Author: Dinesh Reddy Kunduru | April 2026**

---

## Overview

LexRAG is a Retrieval-Augmented Generation (RAG) system that ingests U.S. Supreme Court opinions and answers legal questions using three open-source LLMs. The project evaluates and compares **Llama-3.1-8B**, **Llama-3.3-70B**, and **Llama-4-Scout-17B** across hallucination rate, factual accuracy, and reasoning quality.

---

## Key Results

| Model | Hallucination Rate | Factual Accuracy | Avg Reasoning |
|---|---|---|---|
| Llama-3.1-8B-Instruct | **0%** | **20%** | **2.2 / 5** |
| Llama-3.3-70B-Versatile | **0%** | 10% | 1.5 / 5 |
| Llama-4-Scout-17B | **0%** | 10% | 1.5 / 5 |

> RAG effectively eliminates hallucination across all models. Llama-3.1-8B outperforms larger models on factual accuracy, suggesting retrieval quality — not model scale — is the primary bottleneck.

---

## Repository Structure

```
LexRAG/
├── LexRAG_RAG_System.ipynb   # Main Colab notebook (full pipeline)
├── lexrag_results.csv         # Raw LLM answers for all 10 questions
├── lexrag_scores.csv          # Automated hallucination / accuracy / reasoning scores
├── LexRAG_Paper.docx          # Conference-style paper (ACL format)
├── LexRAG_Proposal.pptx       # Project proposal slides (9 slides)
├── README.md                  # This file
└── data/
    ├── Tinker_v_Des_Moines.pdf
    ├── Brandenburg_v_Ohio.pdf
    ├── NYT_v_Sullivan.pdf
    ├── Snyder_v_Phelps.pdf
    └── Matal_v_Tam.pdf
```

---

## Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/LexRAG.git
cd LexRAG
```

### 2. Open in Google Colab
Upload `LexRAG_RAG_System.ipynb` to [Google Colab](https://colab.research.google.com) or open directly from GitHub.

### 3. Install dependencies
Run Cell 1 in the notebook — it installs all required packages automatically:
```
groq, langchain, langchain-community, faiss-cpu, sentence-transformers, PyMuPDF
```

### 4. Get a free Groq API key
1. Go to [console.groq.com](https://console.groq.com)
2. Sign up for a free account
3. Click **API Keys → Create API Key**
4. Copy the key (starts with `gsk_...`)

### 5. Run the notebook
Paste your Groq API key in **Cell 5** where indicated, then run all cells top to bottom.

---

## Models Used

| Model | Provider | Access |
|---|---|---|
| `llama-3.1-8b-instant` | Meta / Groq | Free API |
| `llama-3.3-70b-versatile` | Meta / Groq | Free API |
| `meta-llama/llama-4-scout-17b-16e-instruct` | Meta / Groq | Free API |

---

## Corpus

Five landmark U.S. Supreme Court First Amendment opinions sourced from [CourtListener.com](https://www.courtlistener.com):

- *Tinker v. Des Moines Independent Community School District* (1969)
- *Brandenburg v. Ohio* (1969)
- *New York Times Co. v. Sullivan* (1964)
- *Snyder v. Phelps* (2011)
- *Matal v. Tam* (2017)

---

## Evaluation Methodology

Each model response is automatically scored on three metrics using **LLM-as-a-judge** (Llama-3.1-8B as scorer):

| Metric | Description | Scale |
|---|---|---|
| Hallucination Rate | Fabricated citations or holdings not in retrieved context | 0 (grounded) / 1 (hallucinated) |
| Factual Accuracy | Correct answer relative to verified ground truth | 0 / 1 |
| Reasoning Quality | Coherence and depth of legal explanation | 1 – 5 |

---

## Citation

If you use LexRAG in your research, please cite:

```
@misc{kunduru2026lexrag,
  title={LexRAG: Comparing Open-Source Large Language Models for Legal Document Question Answering},
  author={Kunduru, Dinesh Reddy},
  year={2026},
  note={DSCI 6004 Term Project, April 2026}
}
```

---

## License

This project is released for academic and research use. All court opinions used are in the public domain.
