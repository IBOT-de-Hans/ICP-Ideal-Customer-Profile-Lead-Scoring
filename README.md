# ICP-Based Lead Scoring AI
This project demonstrates a two-stage hybrid AI model for scoring and ranking business leads. It combines a supervised classification model for initial filtering with a dynamic, similarity-based model for personalized ranking. The entire application is deployed as an interactive web UI using Gradio.

The core goal is to take a user's target industries as input and produce a ranked list of the most relevant potential customers (leads) from a larger dataset.

Features
Stage 1 AI Filter: A RandomForestClassifier is trained to identify "Good Prospects" based on general criteria (industry, company size, revenue), quickly eliminating irrelevant leads.

Stage 2 Personalized Ranking: A SentenceTransformer model combined with Cosine Similarity ranks the filtered leads based on their similarity to a dynamically chosen Ideal Customer Profile (ICP).

Interactive Web UI: A user-friendly interface built with Gradio allows for real-time lead generation.

Fuzzy Matching: The industry search input is tolerant to typos using the fuzzywuzzy library.

Getting Started
Follow these instructions to set up and run the project locally.

1. Setup Instructions
First, you need to have Python 3 installed. Then, clone the repository and install the required libraries.

Clone the repository (if applicable):

Bash

git clone <your-repository-url>
cd <your-repository-directory>
Install dependencies:
All necessary libraries can be installed via pip. It is recommended to use a virtual environment.

Bash

pip install gradio pandas scikit-learn sentence-transformers Faker fuzzywuzzy python-Levenshtein
2. Dataset
This project uses a static, pre-generated dataset named static_lead_dataset_10000_filter.csv. This ensures that the model's performance is consistent and the application's results are reproducible.

The dataset contains 10,000 synthetic company records with the following columns:

company_name: The fictional name of the company.

industry: The industry sector of the company.

employee_count: The number of employees.

annual_revenue_millions_usd: The company's annual revenue in millions of USD.

description: A short, auto-generated business description.

is_good_lead: A pre-computed label (1 for Good, 0 for Bad) used to train the Stage 1 classification model.

The dataset is loaded from the path /kaggle/input/icp-dataset/static_lead_dataset_10000_filter.csv within the notebook. For local execution, ensure this CSV file is in the same directory as the notebook or update the file path accordingly.

3. Notebook Overview (icp-with-ui-ux (1).ipynb)
The project is contained within a single Jupyter Notebook. The notebook is structured into the following parts:

Part 1: Preparation and Data Loading:

Installs and imports all necessary libraries.

Loads the static 10,000-row dataset from the CSV file.

Part 2: Exploratory Data Analysis (EDA):

Provides an analysis of the dataset, including class distribution and feature characteristics.

Part 3 & 4: Model Training & Evaluation (Stage 1 Filter):

Preprocesses the data by scaling numerical features and creating text embeddings for the descriptions.

Trains a RandomForestClassifier on the labeled data.

Evaluates the classifier using standard metrics (Accuracy, Precision, Recall, F1-Score) and displays a confusion matrix.

Part 5: Personalized Ranking Logic (Stage 2 Ranker):

Defines the function that takes a list of pre-filtered leads and ranks them using Cosine Similarity against a dynamically selected ICP.

Part 6: Gradio Web UI:

Defines the core interactive function that links the user input to the two-stage AI model.

Creates and launches the Gradio interface, complete with a custom dark theme for a professional look and feel.

How to Run
Open the icp-with-ui-ux (1).ipynb notebook in a Jupyter environment (like Jupyter Lab or Kaggle Notebooks).

Ensure the dataset path in the load_dataset function is correct for your environment.

Run all the cells in order from top to bottom.

The final cell will launch the Gradio web interface. You can interact with it directly in the notebook output or open the public URL in a new browser tab.
