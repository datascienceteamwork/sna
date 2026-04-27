## 🎬 Movie Actors Collaboration Network Analysis

Questo progetto analizza la rete globale di collaborazioni cinematografiche attraverso la **Social Network Analysis (SNA)** e il **Machine Learning**.  

Partendo da un dataset di film, viene costruito un **grafo pesato** dove:
- i **nodi** rappresentano gli attori  
- gli **archi** rappresentano i film condivisi  

L'obiettivo è esplorare:
- centralità
- coesione strutturale
- predizione di future collaborazioni  

---

## 📁 Struttura del Progetto

Il progetto è organizzato in modo modulare.  
La cartella `risultati` viene gestita automaticamente dai notebook per garantire la persistenza dei dati processati.

```bash
├── dataset/
│   ├── dataset_ridotto.csv   # Dataset finale utilizzato
│   ├── data.csv              # Dataset originale
│   └── riduzione.ipynb       # Notebook per riduzione dataset
├── codice/
│   ├── 01_etl.ipynb            # Pulizia e preparazione dati
│   ├── 02_eda.ipynb            # Analisi esplorativa (EDA)
│   ├── 03_grafo.ipynb          # Costruzione del grafo (Giant Component)
│   ├── 04_centralita.ipynb     # Metriche di centralità
│   ├── 05_struttura_rete.ipynb # Community Detection e sottostrutture
│   ├── 06_prediction.ipynb     # Link Prediction (ML)
│   └── risultati/              # Output (CSV, PKL, immagini)
├── requirements.txt            # Dipendenze del progetto
└── SNA_relazione.pdf           # Relazione progetto SNA    
```
---

## 🛠️ Tecnologie e Algoritmi

**Librerie principali:**
- NetworkX  
- Pandas  
- NumPy  
- Scikit-learn  
- Matplotlib / Seaborn  

---

## 📊 Dataset

Dataset di riferimento (film più popolari dal 1915 al 2023):  
https://www.kaggle.com/datasets/dk123891/10000-movies-data

Il file `data.csv` deve essere collocato in `dataset/`.

Il dataset viene poi ridotto tramite lo script `riduzione.ipynb`, ottenendo `dataset_ridotto.csv` con film nel periodo 1980–2023.

---

## 🔄 Pipeline dei notebook

I notebook vanno eseguiti **in ordine**. Ogni notebook dipende dagli output del precedente.

```
01_etl → 02_eda → 03_grafo → 04_centralita
                            → 05_struttura_rete
                            → 06_prediction
```

### 01 — ETL
Carica il dataset grezzo, normalizza i nomi di attori e registi, filtra il rumore, costruisce la edge list persona–film e le coppie di collaborazione tra attori.

**Output:** `movies_cleaned.csv`, `edges.csv`, `collab_df.csv`, `node_features.csv`

### 02 — EDA
Analisi esplorativa: distribuzioni di rating, anno, genere, numero di attori per film e peso delle collaborazioni. Tutto con visualizzazioni matplotlib/seaborn.

**Input:** `movies_cleaned.csv`, `collab_df.csv`

### 03 — Costruzione Grafo
Costruisce il grafo di collaborazioni con NetworkX. Applica due filtri (attori con ≥ 2 film, nodi con degree ≥ 2), estrae la Giant Component e salva il grafo serializzato.

**Input:** `movies_cleaned.csv`, `collab_df.csv`  
**Output:** `graph_data.pkl`

### 04 — Centralità
Calcola e visualizza sulla Giant Component: Degree, Betweenness, Closeness, Eigenvector e PageRank. Include confronto Top-20 tra le metriche.

**Input:** `graph_data.pkl`

### 05 — Struttura della Rete
Analisi strutturale: triadi e clustering, clique massimali, K-Core decomposition, ego network di attori chiave (Sandler, De Niro, Kumar), community detection con algoritmo di Louvain.

**Input:** `graph_data.pkl`

### 06 — Link Prediction
Predizione di collaborazioni future usando metriche topologiche (Common Neighbors, Jaccard, Adamic-Adar, Resource Allocation). Valutazione con AUC-ROC e Precision-Recall su train/test split. Score composito normalizzato.

**Input:** `graph_data.pkl`  
**Output:** `link_predictions.csv`

---
## ⚙️ Installazione ed Utilizzo

### 1. Clona il repository
```bash
git clone https://github.com/datascienceteamwork/sna.git
cd sna
pip install -r requirements.txt
```