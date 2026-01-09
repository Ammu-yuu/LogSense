# 🛡️ LogSense – Intelligent Security Log Classification

## 📌 Overview

LogSense is a lightweight machine learning project designed to assist security and IT teams in **triaging system and security logs**.
The goal is to automatically classify log messages as **Normal**, **Warning**, or **Suspicious**, helping analysts prioritise alerts and focus on high-risk events more efficiently.

This project focuses on **explainable, practical ML** rather than complex deep-learning approaches, making it suitable for real-world SOC and Detect & Respond environments.

---

## 🎯 Problem Statement

Security teams often deal with **large volumes of log data**, where critical signals can be buried among routine system messages.
Manually reviewing logs is time-consuming and error-prone.

LogSense aims to:

* Reduce alert fatigue
* Provide fast, consistent initial triage
* Support analysts with decision-making, not replace them

---

## 🧠 Solution Approach

* Log messages are treated as **text data**
* Text is transformed using **TF-IDF vectorisation**
* A **Logistic Regression** classifier is trained for interpretability and speed
* The trained model can be accessed via a script or REST API

---

## 🛠️ Tech Stack

| Layer           | Technology              |
| --------------- | ----------------------- |
| Language        | Python                  |
| ML              | scikit-learn            |
| Data Processing | pandas, numpy           |
| Model Storage   | joblib                  |
| API (Optional)  | FastAPI                 |
| Deployment      | Local / Container-ready |

---

## 📂 Project Structure

```
logsense/
│
├── data/
│   └── logs.csv                # Labeled log dataset
│
├── model/
│   ├── train.py                # Model training pipeline
│   ├── predict.py              # Local prediction script
│   └── model.pkl               # Saved trained model
│
├── api/
│   └── main.py                 # FastAPI inference service
│
├── notebooks/
│   └── exploration.ipynb       # Data exploration & analysis
│
├── requirements.txt
└── README.md
```

---

## 📊 Dataset

The dataset consists of system and security log messages with associated labels:

* `normal`
* `warning`
* `suspicious`

Example:

```csv
log_message,label
"Accepted password for user root",normal
"Multiple failed login attempts detected",suspicious
"Password expiry warning for user",warning
```

The dataset may be sourced from public log datasets or synthetically generated to simulate realistic security events.

---

## ⚙️ Installation & Setup

### Prerequisites

* Python 3.9+
* pip

### Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Training the Model

To train the classifier:

```bash
python model/train.py
```

This will:

* Vectorise log messages using TF-IDF
* Train a Logistic Regression model
* Save the trained model to `model/model.pkl`

---

## 🔍 Running Predictions

Test the model locally:

```bash
python model/predict.py
```

Example output:

```json
"suspicious"
```

---

## 🌐 Running the API (Optional)

Start the FastAPI server:

```bash
uvicorn api.main:app --reload
```

Send a request:

```http
POST /predict
{
  "log": "Failed password for admin from 10.0.0.5"
}
```

Response:

```json
{
  "classification": "suspicious"
}
```

---

## 📈 Future Improvements

* Confidence scoring for predictions
* Integration with SIEM tools
* Alert threshold tuning
* Role-based access controls
* Real-time log streaming
* Frontend dashboard for analysts

---

## 🧪 Testing

* Unit tests for preprocessing and classification
* Mock log inputs for validation
* API endpoint testing via Postman

---

## 🎓 Key Learnings

* Applying machine learning to real-world security problems
* Text preprocessing and feature extraction
* Model interpretability and trade-offs
* End-to-end ML system design
* Translating technical output into actionable insights

---

## 📄 Disclaimer

This project uses publicly available or simulated data and is intended for **educational and demonstrative purposes only**.
It does not perform live intrusion detection.

---
