# 🚨 Machine Learning-Based Anomaly Detection in Network Traffic for Telecom Infrastructure Monitoring

This project leverages machine learning models to detect anomalies in network traffic for telecom and embedded systems. The goal is to identify malicious behavior in real time and support secure infrastructure monitoring, especially in IoT, industrial control systems, and critical networks.

---

## 📊 Dataset Description

The dataset simulates real-world networked environments with labeled traffic data (normal & malicious) suitable for supervised learning tasks.

### 🔑 Key Features:
- **Packet Size** – Size of network packets in bytes
- **Inter-Arrival Time** – Time between packet arrivals
- **Protocol Type** – TCP, UDP, ICMP
- **Source & Destination IP** – IPs involved in the connection
- **TCP Flags** – Connection status
- **Packet Count (5s window)** – Number of packets in 5 seconds
- **Spectral Entropy** – Extracted using Wavelet Transform
- **Frequency Band Energy** – Derived from Wavelet Transform

### 🎯 Target Column:
- `0` – Normal traffic  
- `1` – Anomalous (malicious) traffic

---

## 🤖 Models & Evaluation

Three unsupervised models were tested:

### 1. **Isolation Forest**
- **Accuracy**: `0.8640`
- **Precision/Recall (Anomalies)**: `0.14 / 0.07`

### 2. **Local Outlier Factor (LOF)**
- **Accuracy**: `0.8560`
- **Precision/Recall (Anomalies)**: `0.06 / 0.03`

### 3. **Autoencoder**
- **Accuracy**: `0.8560`
- **Precision/Recall (Anomalies)**: `0.06 / 0.03`

> ✅ **Best Performing Model:** Isolation Forest

---

## 🧠 Root Cause Analysis

| Metric                        | Normal Mean | Anomaly Mean |
|------------------------------|-------------|--------------|
| Packet Size                  | 0.50        | 0.48         |
| Inter-Arrival Time           | 0.51        | 0.57         |
| Packet Count (5s)            | 0.50        | 0.58         |
| Protocol Type in Anomalies   | TCP: 44%, UDP: 42% |
| Top Anomalous Source IPs     | `192.168.1.2` (36%), `192.168.1.3` (54%) |

---

## 🧪 Actionable Insights

- **Anomalies Detected**: 50 out of 1000 packets
- **True Anomalies Identified**: 7/100
- Key triggers include:
  - High packet size
  - Low inter-arrival time
  - Spike in packet counts

### ⚠️ Potential Causes:
- Network congestion  
- DDoS attacks  
- Faulty or misconfigured devices

### 🛡️ Recommendation:
Deploy Isolation Forest for real-time monitoring and continuously inspect flagged IPs and traffic patterns.

---

## 🚦 Simulated Real-Time Detection (Sample Output)

| Packet Size | Inter-Arrival Time | Packet Count (5s) | Predicted |
|-------------|--------------------|-------------------|-----------|
| 500         | 0.10               | 8                 | Anomaly   |
| 1200        | 0.03               | 20                | Anomaly   |
| 450         | 0.12               | 7                 | Anomaly   |
| 1500        | 0.02               | 25                | Anomaly   |
| 600         | 0.09               | 9                 | Anomaly   |

---

## 🛠️ Technologies Used

- Python  
- Scikit-learn (Isolation Forest, LOF)  
- Keras (Autoencoder)  
- Wavelet Transform (Feature Engineering)

---

## 📌 Conclusion

This project demonstrates how machine learning models can be applied to detect network anomalies in real-time. Although detecting rare anomalies is challenging due to data imbalance, Isolation Forest showed the most promise and can be deployed in telecom infrastructure for proactive threat monitoring.
