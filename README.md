# AI Job Market Analyst

**AI-Based Job Market Analysis, Skill Extraction, Job Matching & Recommendation System**

An end-to-end data science project that analyzes the AI / tech job market (primarily Pakistan), extracts and normalizes skills, matches candidates to jobs, predicts role categories with machine learning, and delivers everything through a multi-page Streamlit application.

---

## Project Overview

Users can:
- Explore the job market with interactive dashboards
- Search jobs by title, location, skills, experience, etc.
- Get personalized job recommendations based on their skills and profile
- Perform skill-gap analysis against target roles
- Predict the most suitable role category from free-text skills
- Understand market trends (salary, demand, required skills, remote work, etc.)

The system is built as a complete pipeline inside a single well-documented Jupyter notebook and can be deployed as a public Streamlit app.

---

## Dataset

**File:** `ai_job_market_dataset.csv`  
**Size:** ~10,000 job postings × 32 columns

Key fields:
- Job metadata (title, company, location, country, industry, source)
- Employment details (work type, employment type, experience level, years of experience, education)
- Compensation (`salary_min`, `salary_max`, currency, `salary_normalized_usd`)
- Skills (required, preferred, programming languages, data tools, ML skills, cloud, databases, soft skills)
- Target role category (Machine Learning, Data Science, Data Engineering, Business Intelligence, Artificial Intelligence, Data Analytics, etc.)

The dataset is focused on the Pakistani tech job market (PKR salaries, major cities: Islamabad, Lahore, Karachi, etc.) but includes normalized USD salaries for comparability.

---

## Pipeline (Notebook Steps)

| Step | Description |
|------|-------------|
| **1** | Project setup & dataset inspection (shape, dtypes, missing values, duplicates, categorical inconsistencies) |
| **2** | Data cleaning (text normalization, date parsing, salary standardization, consistent categories) |
| **3** | Exploratory Data Analysis + visualizations |
| **4** | NLP – TF-IDF vectorization of job descriptions |
| **5** | Skill extraction & standardization (vocabulary, multi-hot encoding, free-text skill extraction) |
| **6** | Job Matching Algorithm (explainable 0–100 score) |
| **7** | Machine Learning model – predict `target_role_category` (7 classes) |
| **8** | Recommendation System (combines NLP + ML + matcher) |
| **9** | Streamlit multi-page web application |
| **10–11** | Public deployment via Cloudflare Tunnel |

---

## Streamlit Application Pages

1. **Dashboard** – High-level market overview  
2. **Job Search** – Filterable job explorer  
3. **Job Recommendation** – Personalized recommendations  
4. **Skill Gap Analysis** – Compare user skills vs target role  
5. **ML Prediction** – Predict role category from skills  
6. **EDA Dashboard** – Interactive exploratory analysis  

---

## Tech Stack

- **Data & Analysis:** Pandas, NumPy, Matplotlib, Seaborn  
- **NLP:** scikit-learn (TF-IDF), custom skill extraction  
- **Machine Learning:** scikit-learn (classification models)  
- **Web App:** Streamlit  
- **Deployment:** Cloudflare Tunnel (`cloudflared`)  
- **Environment:** Google Colab / Jupyter Notebook  

---

## How to Run

### Option 1: Google Colab (Recommended)

1. Open `Ai_job_market_analyzer.ipynb` in Google Colab.
2. Upload `ai_job_market_dataset.csv` when prompted (or place it in `/content/`).
3. Run all cells in order.
4. The notebook will create the project structure, train models, and launch the Streamlit app.
5. Use the Cloudflare tunnel cells to get a public URL.

### Option 2: Local

```bash
# Clone the repository
git clone https://github.com/dannial-ahmad/Ai-market-analyst.git
cd Ai-market-analyst

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn streamlit

# Run the notebook (or convert the relevant cells into scripts)
jupyter notebook Ai_job_market_analyzer.ipynb
