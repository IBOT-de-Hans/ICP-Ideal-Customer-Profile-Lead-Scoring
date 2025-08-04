<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ICP-Based Lead Scoring AI - README</title>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji";
            line-height: 1.6;
            color: #333;
            background-color: #f6f8fa;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: #ffffff;
            border: 1px solid #d1d5da;
            border-radius: 6px;
            padding: 40px;
        }
        h1, h2, h3 {
            border-bottom: 1px solid #eaecef;
            padding-bottom: 0.3em;
            margin-top: 24px;
            margin-bottom: 16px;
            font-weight: 600;
        }
        h1 { font-size: 2em; }
        h2 { font-size: 1.5em; }
        h3 { font-size: 1.25em; }
        p {
            margin-top: 0;
            margin-bottom: 16px;
        }
        ul {
            padding-left: 20px;
            margin-bottom: 16px;
        }
        li {
            margin-bottom: 8px;
        }
        code {
            font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, Courier, monospace;
            font-size: 85%;
            background-color: rgba(27,31,35,0.05);
            border-radius: 3px;
            padding: 0.2em 0.4em;
        }
        pre {
            background-color: #f6f8fa;
            border-radius: 3px;
            font-size: 85%;
            line-height: 1.45;
            overflow: auto;
            padding: 16px;
        }
        pre code {
            background-color: transparent;
            padding: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>ICP-Based Lead Scoring AI</h1>
        <p>This project demonstrates a two-stage hybrid AI model for scoring and ranking business leads. It combines a supervised classification model for initial filtering with a dynamic, similarity-based model for personalized ranking. The entire application is deployed as an interactive web UI using Gradio.</p>
        <p>The core goal is to take a user's target industries as input and produce a ranked list of the most relevant potential customers (leads) from a larger dataset.</p>

        <h2>Features</h2>
        <ul>
            <li><strong>Stage 1 AI Filter:</strong> A <code>RandomForestClassifier</code> is trained to identify "Good Prospects" based on general criteria (industry, company size, revenue), quickly eliminating irrelevant leads.</li>
            <li><strong>Stage 2 Personalized Ranking:</strong> A <code>SentenceTransformer</code> model combined with Cosine Similarity ranks the filtered leads based on their similarity to a dynamically chosen Ideal Customer Profile (ICP).</li>
            <li><strong>Interactive Web UI:</strong> A user-friendly interface built with Gradio allows for real-time lead generation.</li>
            <li><strong>Fuzzy Matching:</strong> The industry search input is tolerant to typos using the <code>fuzzywuzzy</code> library.</li>
        </ul>

        <h2>Getting Started</h2>
        <p>Follow these instructions to set up and run the project locally.</p>

        <h3>1. Setup Instructions</h3>
        <p>First, you need to have Python 3 installed. Then, clone the repository and install the required libraries.</p>
        <p><strong>Clone the repository (if applicable):</strong></p>
        <pre><code>git clone &lt;your-repository-url&gt;
cd &lt;your-repository-directory&gt;</code></pre>

        <p><strong>Install dependencies:</strong></p>
        <p>All necessary libraries can be installed via pip. It is recommended to use a virtual environment.</p>
        <pre><code>pip install gradio pandas scikit-learn sentence-transformers Faker fuzzywuzzy python-Levenshtein</code></pre>

        <h3>2. Dataset</h3>
        <p>This project uses a static, pre-generated dataset named <code>static_lead_dataset_10000_filter.csv</code>. This ensures that the model's performance is consistent and the application's results are reproducible.</p>
        <p>The dataset contains 10,000 synthetic company records with the following columns:</p>
        <ul>
            <li><strong><code>company_name</code></strong>: The fictional name of the company.</li>
            <li><strong><code>industry</code></strong>: The industry sector of the company.</li>
            <li><strong><code>employee_count</code></strong>: The number of employees.</li>
            <li><strong><code>annual_revenue_millions_usd</code></strong>: The company's annual revenue in millions of USD.</li>
            <li><strong><code>description</code></strong>: A short, auto-generated business description.</li>
            <li><strong><code>is_good_lead</code></strong>: A pre-computed label (1 for Good, 0 for Bad) used to train the Stage 1 classification model.</li>
        </ul>
        <p>The dataset is loaded from the path <code>/kaggle/input/icp-dataset/static_lead_dataset_10000_filter.csv</code> within the notebook. For local execution, ensure this CSV file is in the same directory as the notebook or update the file path accordingly.</p>

        <h3>3. Notebook Overview (<code>icp-with-ui-ux (1).ipynb</code>)</h3>
        <p>The project is contained within a single Jupyter Notebook. The notebook is structured into the following parts:</p>
        <ul>
            <li><strong>Part 1: Preparation and Data Loading:</strong> Installs and imports all necessary libraries and loads the static dataset from the CSV file.</li>
            <li><strong>Part 2: Exploratory Data Analysis (EDA):</strong> Provides an analysis of the dataset, including class distribution and feature characteristics.</li>
            <li><strong>Part 3 & 4: Model Training & Evaluation (Stage 1 Filter):</strong> Preprocesses the data, trains a <code>RandomForestClassifier</code>, and evaluates it using standard metrics.</li>
            <li><strong>Part 5: Personalized Ranking Logic (Stage 2 Ranker):</strong> Defines the function that ranks pre-filtered leads using Cosine Similarity.</li>
            <li><strong>Part 6: Gradio Web UI:</strong> Defines and launches the interactive Gradio interface, complete with a custom dark theme.</li>
        </ul>

        <h3>How to Run</h3>
        <ol>
            <li>Open the <code>icp-with-ui-ux (1).ipynb</code> notebook in a Jupyter environment (like Jupyter Lab or Kaggle Notebooks).</li>
            <li>Ensure the dataset path in the <code>load_dataset</code> function is correct for your environment.</li>
            <li>Run all the cells in order from top to bottom.</li>
            <li>The final cell will launch the Gradio web interface. You can interact with it directly in the notebook output or open the public URL in a new browser tab.</li>
        </ol>
    </div>
</body>
</html>
