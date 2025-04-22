# ⚽ Deep Learning-based Expected Assists (xA) Estimation in Football

![xA Model](https://img.shields.io/badge/Expected%20Assists-Football%20Analytics-blue) ![Deep Learning](https://img.shields.io/badge/Deep%20Learning-FCNN-orange) ![Status](https://img.shields.io/badge/Status-Active-green)

## 📌 Overview

This project presents a novel two-stage deep learning pipeline to estimate **Expected Assists (xA)** in football, aiming to overcome the limitations of traditional xA metrics. Most standard models equate xA to the xG (Expected Goals) of the resulting shot, neglecting the passer’s positioning, intent, and context. Our approach:

1. **Predicts the probability** that a pass leads to a shot using spatial and contextual features.
2. **Estimates the xG** of the resulting shot using StatsBomb data.
3. **Calculates xA** as:  
   \[
   \text{xA} = P(\text{pass leads to shot}) \times \mathbb{E}[\text{xG}|\text{shot}]
   \]

The model is trained on pseudo-xA labels generated via DBSCAN clustering and integrates seamlessly into a **Streamlit-based UI** for visualizing Bayern Munich player performance over a full season.

---

## 🧠 Key Features

- ⚙️ **Two-stage xA Estimation** using neural networks and unsupervised clustering
- 🧪 **Fully Connected Neural Network (FCNN)** trained on contextualized pass data
- 📊 **Interactive Streamlit Dashboard** to display match-wise player ratings and metrics
- 📦 Modular architecture for easy integration with other football analytics tools

---

## 📂 Dataset

- `passes_data.csv`: Spatial, contextual, and pass metadata
- `bayern_match_summary.csv`: Player-level match stats (xA, xG, assists, passes, etc.)
- `final_ratings.csv`: Model-generated player ratings used in the dashboard

---

## 🧪 Methodology

### 🔄 Preprocessing
- One-hot encoding of categorical features: `pass_technique`, `play_pattern`, `pass_type`
- Min-max scaling of numerical features

### 📌 Clustering for Pseudo-xA
- Applied **DBSCAN** on pass features to cluster similar passes
- Computed average xG of passes within each cluster → pseudo-xA

### 🧠 FCNN Architecture
- Inputs: Scaled + encoded pass features
- Output: Pseudo-xA prediction
- Loss: MSE, Optimizer: Adam

### 📈 Streamlit Dashboard
- Player performance visualization by match and season
- Ratings based on xA, xG, pass ratio, and normalized z-scores

---

## 🖼️ UI Demo

<img src="https://user-images.githubusercontent.com/your-streamlit-screenshot.png" width="100%" alt="Streamlit UI Screenshot">

---

## 🚀 Getting Started

### 📦 Install Dependencies
```bash
pip install -r requirements.txt
