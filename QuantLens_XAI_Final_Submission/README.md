# QuantLens-XAI: Final Faculty Submission Package

[![Course](https://img.shields.io/badge/Course-BCSE418L%20Explainable%20AI-blue.svg)](https://vit.ac.in)
[![Institution](https://img.shields.io/badge/Institution-Vellore%20Institute%20of%20Technology-orange.svg)](https://vit.ac.in)
[![Candidate](https://img.shields.io/badge/Candidate-Nikhil%20Anand%20%7C%2024BCE1674-emerald.svg)](https://github.com/nikhilanand0105/QuantLensAi)
[![Python](https://img.shields.io/badge/Python-3.9%20%7C%203.10%20%7C%203.11-3776AB.svg?logo=python&logoColor=white)](https://python.org)
[![PyTorch MPS](https://img.shields.io/badge/PyTorch-2.8%20MPS%20Accelerated-EE4C2C.svg?logo=pytorch&logoColor=white)](https://pytorch.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-3.1%20Multiclass-brightgreen.svg)](https://xgboost.readthedocs.io)
[![SHAP](https://img.shields.io/badge/SHAP-0.49.1%20TreeExplainer-yellow.svg)](https://github.com/slundberg/shap)
[![LIME](https://img.shields.io/badge/LIME-0.2.0.1%20Surrogates-9cf.svg)](https://github.com/marcotcr/lime)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.0%20Active-47A248.svg?logo=mongodb&logoColor=white)](https://mongodb.com)
[![Tests](https://img.shields.io/badge/Tests-140%2F140%20Passing%20(100%25)-success.svg)](tests/)

---

## Academic Candidate & Course Metadata

- **Student Name:** Nikhil Anand
- **Registration Number:** 24BCE1674
- **Degree Program:** B.Tech Computer Science and Engineering (SCOPE)
- **Course Code & Title:** BCSE418L — Explainable Artificial Intelligence
- **Faculty Guide / Reviewer:** Explainable AI Review Committee, School of Computer Science and Engineering
- **Institution:** Vellore Institute of Technology (VIT), Vellore
- **Academic Year:** 2026–2027
- **Project Title:** **QuantLens-XAI: A Closed-Loop Explainable AI Framework for Financial Time Series**

---

## Submission Package Contents

This submission folder contains all four required components organized for academic review:

```
QuantLens_XAI_Final_Submission/
├── QuantLens_XAI_Final_Report_Final (1).pdf     # 1. Complete 20-Page Academic Project Report
├── QuantLens_XAI_Final_Review_Clean (1).pptx     # 2. 16-Slide Final Review Presentation Deck
├── README.md                                     # 3. Master Submission Guide & Technical Documentation
└── codebase/                                     # 4. Clean, Reproducible, End-to-End Source Codebase
    ├── app.py                                    # Flask web application & SSE streaming server
    ├── config.py                                 # Configuration, database URIs, model paths
    ├── quantlens/                                # Core XAI, modeling, feedback & broker packages
    │   ├── routes.py                             # REST API endpoints & UI routing
    │   ├── models_cnn.py                         # TimeSeriesConv1D (Metal MPS accelerated)
    │   ├── xai_gradcam.py                        # 1D Temporal Grad-CAM implementation
    │   ├── xai_feedback.py                       # Closed-loop perturbation & retraining engine
    │   ├── xai_metrics.py                        # 10-Metric Scientific XAI Evaluation Suite
    │   ├── xai_sensitivity.py                    # Sensitivity sweeps, noise & regime analysis
    │   ├── orchestrator.py                       # 8-stage natural language strategy pipeline
    │   ├── paper_broker.py                       # Simulated order execution & portfolio accounting
    │   ├── simulation_engine.py                  # Historical backtesting & candle replay
    │   └── db_mongodb.py                         # MongoDB document store manager
    ├── models/                                   # Pre-trained model checkpoints & metadata
    │   ├── model_xgb_reliance.json               # XGBoost multiclass model checkpoint
    │   ├── model_mlp_reliance.pt                 # PyTorch deep MLP model weights
    │   ├── pytorch_cnn_reliance.pt               # TimeSeriesConv1D PyTorch weights
    │   ├── scaler_reliance.pkl                   # StandardScaler fitted on train split
    │   └── *.json                                # Model metadata, features, metrics
    ├── data/                                     # Historical datasets & state files
    │   ├── RELIANCE.NS.csv                       # 1,687 daily candles of RELIANCE.NS (2018-2024)
    │   └── paper_broker_state.json               # Virtual paper broker ledger state
    ├── templates/                                # HTML5/CSS3 frontend templates
    │   └── quantlens.html                        # 9-tab terminal UI with Tab 09 XAI Research Lab
    ├── tests/                                    # Automated verification test suites (140 assertions)
    │   ├── test_quantlens_research_xai_suite.py  # 30/30 assertions (XAI feedback, Grad-CAM, metrics)
    │   ├── test_quantlens_final_polish_30_invariants.py # 30/30 assertions (trading logic invariants)
    │   ├── test_quantlens_complete_demo.py       # 30/30 assertions (end-to-end demo flow)
    │   ├── test_quantlens_cinematic_demo_e2e.py  # 30/30 assertions (SSE pipeline & browser)
    │   └── test_quantlens_autopilot_e2e.py       # 20/20 assertions (continuous paper trading)
    ├── scripts/                                  # Reproducible report/asset generation scripts
    │   ├── build_final_docx_report.py            # Word report compilation script
    │   ├── build_final_pptx.py                   # PowerPoint presentation builder
    │   └── generate_subreport_assets.py          # Publication-grade chart generation
    ├── subreports/                               # Empirical evidence manifest & figures
    │   ├── evidence/                             # Canonical CSV results & checklists
    │   └── assets/                               # 19 publication-grade charts & screenshots
    ├── requirements.txt                          # Python dependencies specification
    ├── start_quantlens.sh                        # One-click startup shell script
    └── reset_quantlens_demo.sh                   # Demo state reset script
```

---

## Primary Faculty Mandate & Technical Fulfillment

### The Instructor's Exact Instructions:
> *"Not just stop with LIME/ SHAP/ GradCAM explanation. revert the explanation generated into the models involved again and evaluate the performance with xai metrics and compare."*
>
> *"Such as stability, consistency, faithfulness, fidelity, robustness, actionability, confidence, etc... Include sensitivity analysis in results."*

### Quantitative Scientific Achievements:
1. **Closed-Loop Feedback Intervention:** Reverted SHAP, LIME, and Grad-CAM attributions back into model inference graphs across 4 controlled perturbation protocols (Mean, Median, Zero, Gaussian Noise) against **Random-$k$** and **Least-$k$** controls.
   - Perturbing SHAP Top-3 features caused an average confidence drop of **$\Delta P = 0.285$** and flipped **64.2% of decisions**, versus only **$0.048$** for Random-3 controls.
   - **Faithfulness Drop Ratio = 5.93x**, proving empirical causal necessity.
2. **1D Temporal Grad-CAM:** Adapted Grad-CAM to sliding-window temporal convolutions ($T=30$ sessions, 10 normalized channels) with Metal MPS acceleration. Masking top-5 salient temporal bars caused a **24.8% confidence drop** versus **2.9%** for random masking (**8.55x ratio**), localizing historical inflection bars ($T-4$ to $T-2$).
3. **10-Metric Scientific XAI Suite:**
   - **Stability:** 0.941 (SHAP) vs 0.724 (LIME) under 1% Gaussian jitter.
   - **Consistency:** Spearman rank correlation $ho = 0.352$.
   - **Faithfulness Monotonicity:** 0.833 (SHAP) vs 0.667 (LIME).
   - **Deletion AUC:** 0.492 (SHAP) vs 0.584 (LIME).
   - **Fidelity:** $R^2 = 1.000$ (SHAP exact tree paths) vs $0.887$ (LIME local surrogates).
   - **Robustness:** 0.880 sign-flip resistance.
   - **Actionability:** 40.9% (9 of 22 features directly controllable by traders).
   - **Calibration (ECE):** 0.124 expected calibration error.
   - **Sensitivity:** 0.332 attribution response under volatility shocks.
   - **Sparsity:** Gini coefficient 0.629 (LIME concise rules) vs 0.561 (SHAP).
   - **Latency:** 1.02 ms (SHAP) vs 21.34 ms (LIME).
4. **Sensitivity Analysis Lab:**
   - Identified the critical **$\delta = 2.0\%$ Gaussian noise bifurcation threshold** where decision flip rates escalate non-linearly from 8.2% to 42.1%.
   - Measured an **+84% surge in volatility feature attributions** during market drawdown regimes.
5. **Explanation-Guided Model Retraining:**
   - Retraining XGBoost exclusively on the top-6 SHAP features boosted out-of-sample Macro F1 from **0.2897 to 0.3410 (+17.7% relative gain)** on 248 chronologically held-out test bars, proving that XAI acts as an active feature selection filter eliminating collinear market noise.

---

## Quick Start & Setup Instructions

### 1. Prerequisites
- macOS (Apple Silicon M1/M2/M3/M4 recommended for Metal MPS) or Linux (Ubuntu 20.04+)
- Python 3.9, 3.10, or 3.11
- MongoDB 6.0+ or 7.0+ running locally on port 27017
- Ollama with `qwen2.5:0.5b` model pulled locally

### 2. Installation Commands
```bash
# Navigate to the codebase directory
cd codebase

# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate

# Install required dependencies
pip install --upgrade pip
pip install -r requirements.txt
pip install pypdf python-pptx docx matplotlib seaborn

# Verify MongoDB is running
mongosh --eval "db.runCommand({ ping: 1 })"

# Start Ollama service (if not running) and pull model
ollama serve > /dev/null 2>&1 &
ollama pull qwen2.5:0.5b
```

### 3. Run Automated Test Suite (140/140 Passing)
```bash
python3 tests/test_quantlens_research_xai_suite.py
python3 tests/test_quantlens_final_polish_30_invariants.py
python3 tests/test_quantlens_complete_demo.py
python3 tests/test_quantlens_cinematic_demo_e2e.py
python3 tests/test_quantlens_autopilot_e2e.py
```

### 4. Launch the Web Application
```bash
PORT=5001 python3 app.py
```
Access the application at: **`http://127.0.0.1:5001/quantlens`**

---

## 8-Minute Faculty Demonstration Walkthrough

1. **Step 1: Dashboard Overview (0:00 - 1:00):** Open `http://127.0.0.1:5001/quantlens` to showcase the cinematic mission control, multi-model status, and paper trading state.
2. **Step 2: Natural-Language Strategy Formulation (1:00 - 2:00):** Enter *"Buy RELIANCE when EMA 10 crosses EMA 30 and RSI < 65"* and click Run Strategy. Show the 7-stage local Ollama extraction trace and Pydantic validation.
3. **Step 3: Tab 09 — XAI Research Lab (2:00 - 5:30) [CORE FACULTY MANDATE]:**
   - Click **🔬 09. XAI Research Lab**.
   - Show the 3-panel closed-loop feedback pipeline animation.
   - Inspect the **1D Grad-CAM Temporal Heatmap**; explain how Bar $T-4$ to $T-2$ governs Model C decisions.
   - Review the **10-Metric Scientific Table** (Stability, Monotonicity, Fidelity, etc.).
   - Trigger the **Real-Time Perturbation Sweep**; point out the 5.93x Faithfulness Ratio over Random controls.
   - Show the **Retraining Leaderboard**; point out the +17.7% Macro F1 gain for SHAP Top-6 retrained models.
4. **Step 4: Continuous Autopilot & Paper Broker (5:30 - 7:00):** Show simulated order execution, virtual cash balance, and zero-capital risk ledger.
5. **Step 5: Viva Defense Q&A (7:00 - 8:00):** Use the embedded 30-Question Viva Defense Accordion in Tab 09 to answer examiner questions.

---

*QuantLens-XAI Academic Submission Package • Nikhil Anand (24BCE1674) • SCOPE, Vellore Institute of Technology • BCSE418L Final Review • Academic Year 2026–2027*
