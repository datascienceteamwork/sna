🎥 Movie Stars Collaboration Network Analysis

Questo progetto analizza la struttura e l’evoluzione della rete globale di collaborazioni tra attori cinematografici utilizzando tecniche avanzate di Social Network Analysis (SNA) e Machine Learning.

Attraverso la teoria dei grafi, il lavoro esplora come:

la coesione strutturale
la centralità degli attori
le dinamiche di comunità

modellino l’industria del cinema.

📊 Panoramica del Progetto

L’analisi si basa su un dataset di migliaia di film, trasformato in un grafo pesato in cui:

i nodi rappresentano gli attori
gli archi rappresentano le collaborazioni (film in comune)

Il progetto è suddiviso in fasi modulari, ciascuna documentata in un notebook dedicato.

📂 Struttura dei Notebook
01_etl.ipynb
Caricamento e pulizia dei dati, estrazione delle liste di attori e generazione del dataset delle collaborazioni.
02_eda.ipynb
Analisi esplorativa dei dati (EDA) e studio della distribuzione dei pesi degli archi.
03_grafo.ipynb
Costruzione del grafo, estrazione della Giant Component (4.313 nodi, 29.944 archi) e analisi del grado.
04_centralita.ipynb
Calcolo delle principali metriche di centralità:
Degree
Betweenness
Closeness
Eigenvector
PageRank
05_struttura_rete.ipynb
Analisi della coesione:
Triadi
Clique massimali
Community Detection (Louvain)
06_prediction.ipynb
Modelli di Link Prediction per prevedere collaborazioni future.
🛠️ Tecnologie e Algoritmi

Librerie principali:

NetworkX
Pandas
NumPy
Scikit-learn
Matplotlib / Seaborn

⚙️ Installazione ed Utilizzo
1. Clona il repository
git clone https://github.com/tuo-username/movie-stars-sna.git
cd movie-stars-sna
2. Installa le dipendenze
pip install -r requirements.txt
3. Esecuzione

I notebook sono numerati in ordine logico.
Eseguire in sequenza:

01 → 02 → 03 → 04 → 05 → 06

📌 Il file graph_data.pkl (generato nel notebook 03) funge da checkpoint per le analisi successive.

👥 Autori
Domenico La Porta
Lorenzo Meloccaro
Yassir Flavio Suarez Sanchez