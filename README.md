# PatentTrendAI: Automated Patent Trend Detection and Forecasting

PatentTrendAI is an automated patent analytics system designed to detect technology sub-trends, calculate innovation sentiment, and forecast future patent filing activity using artificial intelligence-related patent data.

The project combines Natural Language Processing, semantic embeddings, unsupervised clustering, sentiment analysis, time-series forecasting, and dashboard-based visualization into one reproducible workflow. It was developed as a major project for the Bachelor of Technology program in Computer Science & Engineering.

---

## Project Overview

Patent documents contain a large amount of structured technical information. They help identify where research and development activity is increasing, which companies are active in a domain, and how a technology area is evolving over time. However, manually reviewing hundreds of patent titles, abstracts, assignees, and filing dates is time-consuming.

Commercial patent analytics platforms such as Derwent Innovation, Orbit Intelligence, and PatSnap provide strong tools for patent landscaping, but they are often expensive, enterprise-focused, and fragmented across separate modules. PatentTrendAI was developed as a lightweight and open-source alternative that can perform core patent trend analysis tasks in one workflow.

The system performs the following operations:

- Fetches or generates patent records
- Cleans and structures patent data
- Applies NLP preprocessing to patent titles and abstracts
- Extracts keywords using TF-IDF
- Generates semantic embeddings using Sentence-BERT
- Groups patents into technology subdomains using K-Means clustering
- Calculates innovation positivity scores using VADER sentiment analysis
- Forecasts cluster-wise patent activity using Prophet
- Displays all outputs in an interactive Streamlit dashboard

---

## Motivation

This project was inspired by real patent analytics workflows, where analysts often perform keyword searching, patent reading, claim charting, technology scouting, and assignee tracking manually.

In fast-growing domains such as Artificial Intelligence, patent datasets can grow quickly and become difficult to analyze manually. A single AI patent dataset may include records related to neural networks, image processing, natural language generation, autonomous systems, cybersecurity, edge computing, and other subdomains.

PatentTrendAI aims to reduce the initial manual burden by automatically organizing patents into meaningful technology clusters and providing visual insights for further analysis.

---

## Key Features

### 1. Patent Data Acquisition

The real-data pipeline fetches AI-related patent records from the PatentsView API. The mock-data pipeline generates synthetic patent records with the same schema to validate the full workflow without depending on external API availability.

### 2. Mock Pipeline Validation

A complete mock pipeline is included to test the system using synthetically generated patent records. This helps verify that preprocessing, clustering, sentiment analysis, forecasting, and visualization work correctly before applying the workflow to real patent data.

### 3. Real Patent Data Pipeline

The real-data notebook retrieves AI-related patent records from PatentsView and applies the validated workflow to actual patent data.

### 4. Text Preprocessing

Patent titles and abstracts are cleaned by removing punctuation, numbers, stopwords, short tokens, and patent-specific repeated terms such as:

- invention
- embodiment
- method
- system
- apparatus
- claim
- disclosed
- wherein

This improves the quality of downstream NLP analysis.

### 5. TF-IDF Keyword Extraction

TF-IDF is used to identify important terms and phrases within patent abstracts. It supports cluster labeling by extracting representative keywords from each technology cluster.

### 6. Sentence-BERT Embeddings

Sentence-BERT is used to convert patent abstracts into semantic embeddings. These embeddings help group patents based on meaning rather than exact keyword overlap.

### 7. K-Means Clustering

K-Means clustering groups patents into technology subdomains. The project uses elbow analysis and silhouette score to support cluster count selection.

### 8. Innovation Sentiment Analysis

VADER sentiment analysis is applied to patent abstracts. The compound sentiment score is used as a lightweight innovation positivity indicator for each patent and each cluster.

### 9. Time-Series Forecasting

Prophet is used to forecast monthly patent activity for each technology cluster over a 24-month horizon.

### 10. Interactive Dashboard

A Streamlit dashboard with Plotly visualizations presents:

- Dataset overview
- Cluster distribution
- Monthly patent filing trends
- Top assignees
- Cluster-specific analysis
- Sentiment scores
- Forecasting results
- Patent-level exploration

---

## System Architecture

PatentTrendAI follows a five-layer architecture:

```text
Data Acquisition
        ↓
Data Storage and Structuring
        ↓
NLP Analysis
        ↓
Analytics
        ↓
Visualization and Dashboard
Layer 1: Data Acquisition

Collects patent records from PatentsView API or generates mock patent data.

Layer 2: Data Storage and Structuring

Stores raw patent records in CSV format and converts them into a structured Pandas DataFrame.

Layer 3: NLP Analysis

Performs text preprocessing, TF-IDF vectorization, Sentence-BERT embedding generation, and K-Means clustering.

Layer 4: Analytics

Calculates VADER sentiment scores and generates Prophet-based patent filing forecasts.

Layer 5: Visualization and Dashboard

Displays the final results using a Streamlit dashboard and Plotly charts.

Repository Structure
PatentTrendAI/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   ├── 01_mock_patent_pipeline.ipynb
│   └── 02_real_patent_pipeline.ipynb
│
├── data/
│   └── README.md
│
├── docs/
│   └── screenshots/
│       ├── architecture_diagram.png
│       ├── dashboard_overview.png
│       ├── cluster_analysis.png
│       ├── forecasting_tab.png
│       ├── sentiment_analysis.png
│       └── patent_explorer.png
│
└── outputs/
    └── README.md
Notebooks
01_mock_patent_pipeline.ipynb

This notebook generates synthetic patent records and validates the complete PatentTrendAI workflow.

It includes:

Mock patent data generation
Text preprocessing
TF-IDF vectorization
Sentence-BERT embedding generation
K-Means clustering
Cluster label generation
VADER sentiment analysis
Prophet forecasting
Output validation

The mock pipeline was used to test the complete system before running the workflow on real patent records.

02_real_patent_pipeline.ipynb

This notebook fetches real AI-related patent records from the PatentsView API and applies the final analysis workflow.

It includes:

PatentsView API query construction
Real patent data extraction
CSV storage
Data cleaning
NLP preprocessing
Semantic clustering
Innovation sentiment scoring
Cluster-wise forecasting
Dashboard-ready output generation
Dataset

The project uses two types of datasets.

1. Mock Patent Dataset

The mock dataset contains synthetically generated patent records. It was created to validate the pipeline without relying on external API access.

Each mock record includes:

Patent ID
Patent title
Patent abstract
Patent date
Assignee
2. Real Patent Dataset

The real dataset contains AI-related patent records fetched from the PatentsView API.

The real-data pipeline retrieves patent records based on AI-related search terms such as:

artificial intelligence
machine learning
neural network
deep learning
natural language processing
computer vision
Technologies Used
Technology	Purpose
Python	Main programming language
Google Colab	Notebook development and execution
Pandas	Data loading, cleaning, structuring, and CSV handling
NumPy	Numerical operations and array handling
scikit-learn	TF-IDF vectorization, K-Means clustering, silhouette score
Sentence-BERT	Semantic embedding generation
NLTK	Stopword handling
VADER Sentiment	Sentiment analysis
Prophet	Time-series forecasting
Plotly	Interactive visualizations
Streamlit	Dashboard development
Matplotlib	Diagnostic plotting
Requests	API communication
Installation

Clone the repository:

git clone https://github.com/your-username/PatentTrendAI.git

Move into the project folder:

cd PatentTrendAI

Install the required Python libraries:

pip install -r requirements.txt
Requirements

The project uses the following main libraries:

pandas
numpy
scikit-learn
sentence-transformers
nltk
vaderSentiment
prophet
plotly
streamlit
matplotlib
requests
How to Run the Project
Option 1: Run in Google Colab
Open Google Colab.
Upload the notebook from the notebooks/ folder.
Run the cells sequentially.
Start with the mock notebook.
Then run the real patent notebook.

Recommended order:

1. notebooks/01_mock_patent_pipeline.ipynb
2. notebooks/02_real_patent_pipeline.ipynb
Option 2: Run Locally

Install requirements:

pip install -r requirements.txt

Open Jupyter Notebook:

jupyter notebook

Then open and run:

notebooks/01_mock_patent_pipeline.ipynb
notebooks/02_real_patent_pipeline.ipynb
Dashboard

The dashboard is built using Streamlit and Plotly.

To run the dashboard locally:

streamlit run dashboard.py

The dashboard includes five major sections:

Overview
Cluster Analysis
Trend Forecast
Sentiment Analysis
Patent Explorer
Dashboard Preview

Add your screenshots in the docs/screenshots/ folder and update the paths below if needed.

Overview Tab

Cluster Analysis

Forecasting Tab

Sentiment Analysis

Patent Explorer

Methodology
Step 1: Data Acquisition

The system either generates mock patent records or fetches real patent records from the PatentsView API.

Step 2: Data Structuring

Patent records are converted into a structured tabular format using Pandas.

Step 3: Text Preprocessing

Patent titles and abstracts are cleaned by removing punctuation, digits, stopwords, short tokens, and repeated patent-specific terms.

Step 4: TF-IDF Vectorization

TF-IDF is used to extract important words and phrases from the cleaned patent abstracts.

Step 5: Sentence-BERT Embedding

Sentence-BERT converts patent abstracts into 384-dimensional semantic vectors.

Step 6: K-Means Clustering

K-Means clusters patent embeddings into technology subdomains.

Step 7: Cluster Labeling

Top TF-IDF terms from each cluster are used to create human-readable cluster labels.

Step 8: Sentiment Analysis

VADER calculates compound sentiment scores for each patent abstract. These scores are aggregated at the cluster level as innovation positivity scores.

Step 9: Forecasting

Prophet forecasts cluster-wise monthly patent activity for the next 24 months.

Step 10: Dashboard Visualization

Streamlit and Plotly display all major outputs through an interactive dashboard.

Output Files

The pipeline may generate the following files:

File Name	Description
patents_raw.csv	Raw patent records
patents_preprocessed.csv	Cleaned patent dataset
patents_clustered.csv	Patent dataset with cluster assignments
sentiment_summary.csv	Cluster-level sentiment summary
forecasts.csv	Forecast output for patent filing activity
embeddings.npy	Sentence-BERT embedding matrix

Generated files may be excluded from the repository to keep it lightweight.

Results Summary

The system was developed and tested in two stages.

Mock Data Results

The mock pipeline successfully validated the end-to-end workflow using synthetic patent records. It confirmed that the pipeline could generate, clean, cluster, score, forecast, and visualize patent records.

Real Data Results

The real-data pipeline was applied to AI-related patent records fetched from PatentsView. The system produced coherent technology clusters, cluster-level sentiment scores, and 24-month filing activity forecasts.

Representative technology clusters included:

Neural network training and model optimization
Image processing and convolutional detection
Language generation and sequence modeling
Project Limitations

The current version of PatentTrendAI has the following limitations:

The system currently focuses on U.S. patent records available through PatentsView.
The analysis is primarily based on patent titles and abstracts, not full claims.
The dataset size is limited for academic project execution.
VADER is a general-purpose sentiment tool and is not specifically trained on patent language.
Forecast accuracy depends on the volume and quality of historical patent data.
The current version does not include citation network analysis.
Assignee normalization is lightweight and may not fully merge all company name variations.
Future Scope

Future improvements may include:

Support for larger patent datasets
Integration with international patent sources such as EPO and WIPO
Claim-level NLP analysis
Citation network analysis
BERTopic or HDBSCAN-based topic modeling
Domain-specific sentiment models for patent language
Better assignee name normalization
Cloud deployment for multi-user access
PDF or HTML report export
Competitive intelligence dashboard at assignee level
Support for other technology domains such as biotechnology, semiconductors, green energy, and telecommunications
Academic Context

This project was developed as a major project report for the Bachelor of Technology program in Computer Science & Engineering.

Project Title: PatentTrendAI: Automated Patent Trend Detection and Forecasting
Student: Srishti Srivastava
Roll Number: 221030346
Department: Computer Science & Engineering and Information Technology
Institution: Jaypee University of Information Technology
Academic Year: 2025–2026

Author

Srishti Srivastava
Bachelor of Technology
Computer Science & Engineering
Jaypee University of Information Technology

Acknowledgement

This project was developed with guidance from the Department of Computer Science & Engineering and Information Technology, Jaypee University of Information Technology.

The project was also inspired by practical exposure to patent analytics workflows, including technology scouting, patent landscaping, keyword searching, and IP strategy support.

The system uses open-source tools and libraries, including Python, Pandas, scikit-learn, Sentence-BERT, VADER, Prophet, Streamlit, Plotly, and the PatentsView API.

References
R. Krestel, R. Chikkamath, C. Hewel, and J. Risch, “A survey on deep learning for patent analysis,” World Patent Information, vol. 65, Art. no. 102035, Jun. 2021.
H. Bekamiri, D. S. Hain, and R. Jurowetzki, “PatentSBERTa: A deep NLP based hybrid model for patent distance and classification using augmented SBERT,” Technological Forecasting and Social Change, vol. 206, Art. no. 123536, Sep. 2024.
N. Reimers and I. Gurevych, “Sentence-BERT: Sentence embeddings using Siamese BERT-networks,” in Proc. 2019 Conf. Empirical Methods in Natural Language Processing and 9th Int. Joint Conf. Natural Language Processing, Hong Kong, China, 2019, pp. 3982–3992.
F. Pedregosa et al., “Scikit-learn: Machine learning in Python,” Journal of Machine Learning Research, vol. 12, pp. 2825–2830, 2011.
License

This project is intended for academic and educational use.

A license file may be added later depending on the intended public use of the repository.


A few things to edit before uploading:

- Replace `https://github.com/your-username/PatentTrendAI.git` with your actual repository link.
- Keep only screenshot links for images you actually upload.
- Add `dashboard.py` to the repository only if you have a separate dashboard file.
- Remove the Dashboard section command if your dashboard exists only inside the Colab notebook.
