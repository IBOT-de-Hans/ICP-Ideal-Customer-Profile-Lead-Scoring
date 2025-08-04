# 🧠 ICP-Based Lead Scoring AI

This project demonstrates a **two-stage hybrid AI model** for scoring and ranking business leads. It combines:

- A **supervised classification model** for initial filtering, and  
- A **similarity-based model** for personalized ranking.  

The entire application is deployed with an **interactive Gradio web UI**.

> 🎯 **Goal**: Take a user's target industries as input and produce a **ranked list of relevant leads** from a large dataset.

---

## ✨ Features

- **🔍 Stage 1 – AI Filter**  
  A `RandomForestClassifier` identifies *"Good Prospects"* based on general criteria like industry, company size, and revenue.

- **🧬 Stage 2 – Personalized Ranking**  
  A `SentenceTransformer` combined with cosine similarity ranks filtered leads based on their similarity to a dynamic Ideal Customer Profile (ICP).

- **🖥️ Interactive Web UI**  
  A real-time lead generation interface built using **Gradio**.

- **🔡 Fuzzy Matching**  
  Typo-tolerant industry search powered by the `fuzzywuzzy` library.

---

## 🚀 Getting Started

Follow these instructions to set up and run the project locally.

### 1. Setup Instructions

> Ensure you have **Python 3** installed.

Clone the repository:

```bash
git clone <your-repository-url>
cd <your-repository-directory>
