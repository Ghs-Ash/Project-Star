# Project-Star

# 🌌 Exoplanet Detection using Machine Learning (LSTM) — Project Documentation

## 📌 Project Overview

This project focuses on detecting the presence of exoplanets by analyzing stellar brightness data collected over time. Using time-series modeling with LSTM (Long Short-Term Memory), the system identifies patterns in light intensity that indicate the possible presence of a planet orbiting a star.

exoplanet-ml-project/
│
├── data/
│   ├── exoTrain.csv
│   └── exoTest.csv
│
├── notebooks/
│   └── eda.ipynb
│
├── src/
│   ├── preprocess.py
│   ├── train.py
│   ├── model.py
│   ├── predict.py
│   └── visualize.py
│
├── api/
│   └── main.py
│
├── models/
│   └── lstm_model.h5
│
├── outputs/
│   └── heatmaps/
│
├── requirements.txt
├── Dockerfile
├── README.md
└── .gitignore
---

## 🎯 Objective

* Analyze stellar brightness (flux) data
* Detect dips in brightness caused by transiting planets
* Build a predictive model to classify stars:

  * `1 → Planet Present`
  * `0 → No Planet`

---

## 📊 Dataset

* Source: NASA Exoplanet dataset (CSV format)
* Data contains:

  * Thousands of brightness readings per star (time-series)
  * Label column indicating planet presence

---

## 🧹 Data Preprocessing

Steps performed:

1. Removed unnecessary columns (if any)
2. Handled missing/null values
3. Normalized brightness values
4. Separated features (X) and labels (y)
5. Reshaped data for LSTM:

```
(samples, timesteps, features)
```

Example:

```
(1000, 3197, 1)
```

---

## 🧠 Model Selection

### Why LSTM?

* Data is sequential (time-series)
* LSTM captures temporal dependencies
* Detects subtle patterns like periodic dips in brightness

---

## 🏗️ Model Architecture

* Input Layer
* LSTM Layer (64 units)
* Dense Layer (Sigmoid activation)

---

## ⚙️ Model Training

* Loss Function: Binary Crossentropy
* Optimizer: Adam
* Epochs: 10 (adjustable)
* Train/Test Split applied

Training command:

```
model.fit(X_train, y_train, epochs=10)
```

---

## 💾 Model Saving

After training, the model was saved using:

```
model.save("exoplanet_model.h5")
```

This `.h5` file contains:

* Model architecture
* Weights
* Training configuration

---

## 🔍 Prediction Pipeline

A prediction script was created to:

1. Load the trained model
2. Read new CSV input
3. Apply same preprocessing
4. Reshape input
5. Generate predictions

Output:

```
0 → No Planet
1 → Planet Present
```

---

## 🌐 API Development

Built using FastAPI:

### Endpoint:

```
POST /predict
```

### Functionality:

* Accept CSV file upload
* Run model inference
* Return prediction as JSON

---

## 🐳 Dockerization

* Created Dockerfile
* Included:

  * Model (.h5)
  * Prediction script
  * FastAPI app
* Built and ran container locally

---

## ☁️ AWS Deployment

### Service Used:

* EC2 instance

### Steps:

1. Launched EC2 instance
2. Installed Docker
3. Deployed container
4. Exposed port 8000

---

## 🧪 Testing

Tested using:

```
curl -X POST http://<EC2-IP>:8000/predict -F "file=@test.csv"
```

---

## ⚠️ Key Challenges

* Ensuring input CSV matches training format
* Proper reshaping for LSTM
* Handling large feature size (~3000 columns)

---

## 🚀 Final Architecture

```
User CSV → FastAPI → LSTM Model (.h5) → Prediction Output
```

---

## 📈 Future Improvements

* Add real-time data streaming
* Integrate with S3 for batch processing
* Use auto-scaling for production load
* Improve model accuracy with more tuning

---

## 💡 Key Learnings

* Time-series modeling using LSTM
* End-to-end ML pipeline deployment
* API integration with ML models
* Docker + AWS deployment
* Handling real-world structured datasets

---

## 🔗 LinkedIn Post (Short Version)

🚀 Built an End-to-End Exoplanet Detection System using LSTM!

* Processed NASA stellar brightness data
* Used LSTM for time-series pattern detection
* Built FastAPI for real-time predictions
* Dockerized and deployed on AWS EC2

This project simulates real-world ML deployment pipelines and combines AI + Cloud 🚀

#MachineLearning #AWS #LSTM #DevOps #MLOps #AI

---

## ✅ Status

✔ Completed
✔ Deployed

---

