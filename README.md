# Financial Persona Clustering

Unsupervised clustering on synthetic banking data to segment customers 
into financial persona types — covering spend behaviour, income, debt, 
and demographic profile.

---

## About

This project was built by Lara Wahbi as part of a self-directed learning 
journey into machine learning and customer analytics. The goal was to apply 
clustering techniques to real-world-style financial data and produce 
interpretable persona profiles — similar in concept to personality type 
frameworks but grounded in financial behaviour.

**Background:** 8+ years in data engineering, business intelligence, and 
data governance across international organisations including UNHCR, WFP, 
and IFRC. This project reflects a deliberate move into applied machine 
learning to complement an existing analytics foundation.

---

## The Five Personas

| Cluster | Persona | Customers | Avg Age | Avg Income | Avg Debt | Credit Score |
|---------|---------|-----------|---------|------------|----------|--------------|
| 0 | Settled Retiree | 263 | 74 | $38k | $14k | 714 |
| 1 | Stretched Middle | 495 | 45 | $38k | $65k | 710 |
| 2 | Affluent Spender | 371 | 49 | $61k | $91k | 713 |
| 3 | Disciplined Saver | 64 | 54 | $46k | $28 | 742 |
| 4 | Financially Vulnerable | 26 | 55 | $26k | $41k | 699 |

---

## Project Structure
customer-segmentation/
│
├── data/                        ← not included, see instructions below
│   └── README.md                ← data download instructions
│
├── notebooks/
│   ├── 01_data_loading.ipynb    ← load and join the five raw files
│   ├── 02_feature_engineering.ipynb  ← build financial ratios and signals
│   ├── 03_preprocessing.ipynb   ← scale and clean for clustering
│   ├── 04_clustering.ipynb      ← elbow method, silhouette, k=5 model
│   ├── 05_cluster_profiles.ipynb ← persona interpretation
│   └── 06_report.ipynb          ← full visual report
│
├── src/                         ← reusable functions
├── outputs/                     ← generated charts, not included in repo
├── requirements.txt
└── README.md

---

## Dataset

Created by CaixaBank Tech for the 2024 AI Hackathon. Synthetic banking 
data covering 1,219 customers and 13 million transactions across the 2010s.

Download from Kaggle:
https://www.kaggle.com/datasets/computingvictor/transactions-fraud-datasets

Once downloaded, place these files in the `data/` folder:
- `transactions_data.csv`
- `users_data.csv`
- `cards_dat.csv`
- `mcc_codes.json`
- `train_fraud_labels.json`

---

## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/larawahbi/financial-persona-clustering.git
cd financial-persona-clustering
```

**2. Create and activate a virtual environment**
```bash
python3 -m venv venv
source venv/bin/activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Register the kernel with Jupyter**
```bash
python -m ipykernel install --user --name=venv --display-name "Python (customer-seg)"
```

**5. Download the dataset** and place files in the `data/` folder as described above.

**6. Run the notebooks in order** — 01 through 06 — each one saves 
its output for the next to pick up.

---

## Tools and Libraries

- Python 3.12
- pandas, numpy
- scikit-learn
- matplotlib, seaborn
- Jupyter / VS Code

---

## Key Findings

The Stretched Middle is the largest group — nearly half the customer 
base — carrying the highest debt-to-income ratio despite being in peak 
earning years. The Disciplined Saver group, though small at 64 customers 
and 59% female, demonstrates the highest credit score of all personas 
with essentially zero debt. The Financially Vulnerable group is the 
most distinct — near-zero credit access, lowest spend, and narrowest 
merchant range — suggesting financial exclusion rather than simply 
low income.