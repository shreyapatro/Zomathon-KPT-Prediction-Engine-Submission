# Zomathon-KPT-Prediction-Engine-Submission
Smart KPT Signal Engine (SKSE): A scalable signal enrichment framework that improves Kitchen Prep Time prediction accuracy by 42% using rider behavior correction and kitchen load inference, reducing rider wait and ETA errors at scale.
# 🚀 Smart KPT Signal Engine (SKSE)

---

## 📌 Problem Statement

Zomato's Kitchen Prep Time (KPT) model relies heavily on merchant-marked Food Order Ready (FOR) signals.  
However, these signals are often biased due to:

- Rider-influenced marking behavior  
- No visibility into dine-in / competitor load  
- Manual inconsistencies across merchants  

At 1M+ daily orders, even small KPT errors lead to:

- Increased rider wait time  
- ETA inaccuracies (P50/P90)  
- Higher cancellation rates  
- Operational cost escalation  

---

## 💡 Solution: Smart KPT Signal Engine (SKSE)

Instead of modifying the core ML model, SKSE enhances the **input signal layer** using three modules:

### 1️⃣ Label Correction Engine (LCE)
- Uses rider wait time as a ground-truth proxy
- Computes Merchant Reliability Score (MRS)
- Corrects biased FOR labels
- Achieves ~42% reduction in KPT label noise (simulation)

### 2️⃣ Kitchen Load Estimator (KLE)
- Infers hidden kitchen rush using proxy signals:
  - Time-of-day multipliers
  - Day-of-week patterns
  - Order velocity anomalies
  - KPT residual deviations
- Produces real-time Kitchen Load Index (KLI)

### 3️⃣ Smart Signal Layer (SSL)
- Replaces single noisy FOR input
- Enriches model with 7 high-quality features
- Requires no modification to existing model architecture

---

## 📊 Simulation Results

Synthetic dataset: 100,000 orders  
Full-scale impact simulation: 1,000,000 orders/day

### KPT Accuracy Improvement
- MAE Before: 3.84 mins  
- MAE After: 2.23 mins  
- Improvement: ~42%

### Operational Impact at 1M Orders/Day
- Rider wait reduced by ~1.6 mins/order  
- 26,667 rider hours saved daily  
- ~₹4 Crore/day operational savings (₹150/hr rider cost)

---

## 🏗 Scalability

Tiered deployment strategy:

- Tier 1 (70% merchants): Works using existing GPS + app logs  
- Tier 2: Stage prompts + queue velocity  
- Tier 3: POS API integration + IoT ticket counter  

Designed to scale across 300K+ merchants.

---

## 🛠 Tech Stack

- Python
- NumPy
- Pandas
- Matplotlib
- Statistical Simulation
- Signal Engineering

---

## 🎯 Key Insight

We do not replace the KPT model.  
We fix the signals it learns from.

---

## 👤 Author

Shreya Patro  
Computer Science | Data Science Enthusiast  
