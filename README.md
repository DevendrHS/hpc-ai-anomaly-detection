# HPC-Based AI Anomaly Detection

**Scalable Real-Time Network Intrusion Detection using Parallel Deep Learning on HPC Clusters**

A project that combines Artificial Intelligence with High Performance Computing (HPC) to detect network anomalies and intrusions accurately and in real time, by parallelizing model training across multiple nodes.

---

## Team

- Devendra Yadav
- Amina Begum

**Organization:** CDAC CINE, Research Park

---

## Problem Statement

Modern networks generate massive volumes of traffic data every second. Traditional anomaly detection models train and run sequentially, making them too slow for real-time threat detection at scale. By the time an intrusion or fault is identified, damage may already be done. This project addresses that gap by using parallel computing to make AI-based anomaly detection both accurate and fast enough for real-world use.

---

## Objective

1. Design and implement a parallel deep-learning-based anomaly detection model deployable on an HPC cluster.
2. Reduce training and inference latency using data & model parallelism (MPI, multi-node/multi-GPU execution).
3. Achieve accurate, real-time detection on large-scale network traffic datasets.
4. Evaluate scalability by measuring speedup and efficiency across an increasing number of nodes/cores.
5. Compare traditional ML (Isolation Forest, One-Class SVM) vs. Deep Learning (Autoencoder, LSTM) under parallel execution.

---

## Dataset

**NSL-KDD** — a benchmark dataset for network intrusion detection.

| Property | Value |
|---|---|
| Training records | 125,973 |
| Features | 41 (+ label) |
| Missing values | 0 |
| Normal traffic | 67,343 records |
| Attack traffic | 58,630 records (22 attack types, e.g. neptune, satan, smurf) |

Source: [Kaggle - NSL-KDD](https://www.kaggle.com/datasets/hassan06/nslkdd)

---

## Tech Stack

- **Language:** Python
- **ML / DL:** PyTorch, scikit-learn
- **Data handling:** pandas, numpy
- **Visualization:** matplotlib, seaborn
- **Parallelization:** MPI4py / Horovod / PyTorch DDP
- **Cluster scheduling:** SLURM
- **Environment:** Linux HPC Cluster

---

## Project Structure

```
hpc-ai-anomaly-detection/
│
├── data/               # Dataset files (not tracked in git - see .gitignore)
├── src/                # Source code
│   ├── explore_data.py     # Data exploration & sanity checks
│   ├── preprocess.py       # Cleaning, encoding, scaling
│   ├── baseline_model.py   # Sequential (single-node) model
│   ├── parallel_train.py   # Parallel/distributed training
│   └── evaluate.py         # Accuracy, speedup, efficiency evaluation
├── results/            # Graphs, benchmark reports, output logs
├── docs/               # Project report, presentation, paper draft
├── requirements.txt    # Python dependencies
├── .gitignore
└── README.md
```

---

## How to Run

### 1. Clone the repository
```bash
git clone https://github.com/your-username/hpc-ai-anomaly-detection.git
cd hpc-ai-anomaly-detection
```

### 2. Set up the environment
```bash
python -m venv myenv
myenv\Scripts\activate        # Windows
source myenv/bin/activate     # Linux/Mac

pip install -r requirements.txt
```

### 3. Download the dataset
```bash
kaggle datasets download -d hassan06/nslkdd -p data
```
Extract `KDDTrain+.txt` and `KDDTest+.txt` into the `data/` folder.

### 4. Explore the data
```bash
python src/explore_data.py
```

### 5. Preprocess the data
```bash
python src/preprocess.py
```

### 6. Train the model
```bash
python src/baseline_model.py       # sequential baseline
python src/parallel_train.py       # parallel / HPC version
```

---

## Project Status

- [x] **Day 1** — Environment setup, NSL-KDD dataset downloaded, initial data exploration
- [ ] **Day 2** — Data preprocessing pipeline (encoding, scaling, binary labels)
- [ ] Baseline (sequential) Autoencoder/LSTM model
- [ ] Parallel training implementation (MPI4py / Horovod)
- [ ] Scalability benchmarking (1, 2, 4, 8 nodes)
- [ ] Comparative evaluation (ML vs DL, sequential vs parallel)
- [ ] Final report & research paper draft

---

## Deliverables

1. Trained parallel anomaly-detection model (Autoencoder/LSTM) with saved weights
2. Fully documented source code (this repository)
3. Benchmark report — speedup, efficiency & scalability graphs
4. Research paper draft
5. Project report
6. Live demonstration of real-time anomaly detection

---

## Innovation Angle

Beyond basic parallel training, this project also studies communication-overhead optimization (e.g., gradient compression) and reports energy/power consumption alongside speedup — an emerging "green HPC" angle that strengthens the research contribution.