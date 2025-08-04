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
```

Install dependencies:
```
pip install gradio pandas scikit-learn sentence-transformers Faker fuzzywuzzy python-Levenshtein
```


---

## 📊 Dataset

This project uses a static, pre-generated dataset:  
📄 **`static_lead_dataset_10000_filter.csv`**

The dataset includes **10,000 synthetic company records** with the following structure:

| Column                         | Description                                           |
|-------------------------------|-------------------------------------------------------|
| `company_name`                | Fictional name of the company                        |
| `industry`                    | Industry sector of the company                       |
| `employee_count`              | Number of employees in the company                   |
| `annual_revenue_millions_usd`| Annual revenue in millions of USD                    |
| `description`                 | Auto-generated business description                  |
| `is_good_lead`                | Label used for classification (1 = Good, 0 = Bad)    |

🗂️ The dataset is located at:

[/kaggle/input/icp-dataset/static_lead_dataset_10000_filter.csv](https://www.kaggle.com/datasets/hanssanjaya/icp-dataset/data?select=static_lead_dataset_10000.csv)

If you're running this project **locally**, make sure to:

- Place the CSV file in the **same directory** as the notebook  
  **OR**
- Update the file path in the `load_dataset()` function accordingly.

---

## 📒 Notebook Structure

All logic is implemented in a single Jupyter notebook:  
📘 **`icp-with-ui-ux_Kaggle.ipynb`**

The notebook is structured into the following parts:

### 🔹 Part 1: Preparation & Data Loading
- Installs and imports required libraries
- Loads the static dataset

### 🔹 Part 2: Exploratory Data Analysis (EDA)
- Analyzes class distribution
- Visualizes feature characteristics

### 🔹 Part 3 & 4: Model Training & Evaluation (Stage 1)
- Preprocesses data (scaling + embedding)
- Trains a `RandomForestClassifier`
- Evaluates model using:
  - Accuracy
  - Precision
  - Recall
  - F1-Score
  - Confusion matrix

### 🔹 Part 5: Personalized Ranking Logic (Stage 2)
- Filters "Good Leads"
- Computes cosine similarity against user-defined ICP
- Ranks leads by similarity

### 🔹 Part 6: Gradio Web UI
- Defines user interaction logic
- Deploys app with a custom **dark theme**

---

## ▶️ How to Run

1. Open the notebook:in a Jupyter environment (e.g. Jupyter Lab, VSCode, or Kaggle Notebooks).

2. Verify the dataset path is correct for your environment.

3. Run the cells in order from top to bottom.

4. The last cell will launch the Gradio web interface.
- Interact directly inside the notebook **or**
- Open the public URL in your browser.
