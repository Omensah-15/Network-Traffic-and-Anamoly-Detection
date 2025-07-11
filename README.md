
# 📡 Anomaly Detection in Network Traffic for Telecom Infrastructure

A machine learning-based system for detecting anomalies in network traffic using real-world simulated IoT and telecom data. This project aims to enhance the security of embedded and critical networked systems by identifying potential threats in real time.

## 📁 Dataset Overview

The dataset includes:
- Normal and anomalous (malicious) traffic — labeled for supervised learning
- Network traffic features:
  - **Packet Size**
  - **Inter-Arrival Time**
  - **Protocol Type (TCP, UDP, ICMP)**
  - **Source & Destination IPs**
  - **TCP Flags**
  - **Packet Count (5s window)**
  - **Spectral Entropy & Frequency Band Energy** (via Wavelet Transform)

Target label:
- `0` = Normal Traffic  
- `1` = Anomalous Traffic

## 🧠 Models & Performance

| Model            | Accuracy | Key Observations |
|------------------|----------|------------------|
| Isolation Forest | **0.864** | Best overall performance |
| LOF              | 0.856    | Lower anomaly recall |
| Autoencoder      | 0.856    | Limited anomaly detection |

> ⚠️ All models struggled with anomaly class recall (very low precision/recall for label `1`).

## 🔍 Root Cause Insights

- **Higher Inter-Arrival Times** in anomalies
- **Increased Packet Count (5s)** during malicious activity
- **Anomalous IPs**: `192.168.1.2`, `192.168.1.3`
- **Frequent Protocols in Attacks**: TCP (44%), UDP (42%)

## 🚨 Actionable Takeaways

- Deploy Isolation Forest model for real-time detection
- Focus on:
  - High packet sizes
  - Low inter-arrival times
  - Burst packet counts
- Investigate suspicious IPs and protocol usage patterns

## ⚙️ Sample Real-Time Prediction

| Packet Size | Inter-Arrival | Packet Count (5s) | Predicted |
|-------------|----------------|-------------------|-----------|
| 500         | 0.10           | 8                 | ✅ Anomaly |
| 1500        | 0.02           | 25                | ✅ Anomaly |

## 📌 Technologies Used

- Python
- Scikit-learn
- Keras (Autoencoder)
- Wavelet Transform for feature extraction

## 🧾 Conclusion

This project shows the potential of unsupervised models like Isolation Forest in identifying network anomalies with decent accuracy. It also reveals the challenge of highly imbalanced datasets in anomaly detection and the need for feature engineering and monitoring strategies.
