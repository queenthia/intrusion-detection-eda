#intrusion-detection-eda

Cybersecurity Intrusion Detection

Authors

Group of 3 – Master's Data Science Programme  
**Niyongabo Queenthia Olga 2025/MSIS/045/PS**
**Siama Mary 2025/MSIS/044/PS**
**Kyogabirwe Scovia 2025/PGD/002/PS**

project Overview
This project applies to a cybersecurity network intrusion dataset. The goal is to identify the most predictive features for the binary target variable 'attack_detected' (1 = attack, 0 = normal traffic).

Dataset
Source: 'Cybersecurity_intrusion_data.csv' From Kaggle
Columns: 11
Rows: 9,537 network sessions  
Target:'attack_detected'(binary: 0 or 1)

Mapping Table

Guided by the CIA Triad (ISO/IEC 27001) and the Cyber Kill Chain (Lockheed Martin, 2011) frameworks:

| Raw Dataset Column | Construct | Framework | Why It Predicts Attacks |

| `failed_logins` | Credential Threat (Integrity) | CIA Triad | Brute-force attempts violate system integrity |
| `login_attempts` | Reconnaissance Activity | Kill Chain Stage 1 | High volume indicates automated credential scanning |
| `ip_reputation_score` | Threat Intelligence Signal | Kill Chain Stage 2 | Low-reputation IPs correlate with known malicious actors |
| `encryption_used` | Confidentiality Control | CIA Triad | Weak encryption (None/DES) signals attacker behaviour |
| `network_packet_size` | Traffic Anomaly / Availability | CIA Triad | Abnormal sizes indicate exfiltration or DoS payloads |
| `protocol_type` | Network Attack Vector | Kill Chain Stage 3 | ICMP/UDP commonly abused in amplification attacks |
| `unusual_time_access` | Behavioural Anomaly | Kill Chain Stage 4 | Off-hours access indicates compromised credentials |

How to Run (Anaconda)

1. Clone this repository or download the files
2. Open **Anaconda Navigator** → Launch **Jupyter Notebook**
3. Navigate to 'Cybersecurity_Intrusion_EDA.ipynb'
4. Place 'cybersecurity_intrusion_data.csv' in the same folder
5. Run **Cell → Run All**
   Methods Used

| Task                     | Method                       | Justification                                                 |
| ------------------------ | ---------------------------- | ------------------------------------------------------------- |
| Missing value handling   | KNN Imputation (k=5)         | Uses similar rows; better than mean for correlated features   |
| Encoding (ordinal)       | Manual Label Encoding        | None=0, DES=1, AES=2 reflects security strength order         |
| Encoding (nominal)       | One-Hot Encoding             | Protocol type and browser type have no natural order          |
| Class imbalance          | SMOTE                        | Creates synthetic minority samples; avoids biased classifiers |
| Numerical significance   | Pearson Correlation + T-test | Tests linear relationship and group mean differences          |
| Categorical significance | Chi-Square Test              | Tests independence between category and target                |
