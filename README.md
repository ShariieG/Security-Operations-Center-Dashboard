# 🔐 Security Operations Center (SOC) Log Analytics & Ingestion Dashboard

## 📋 Overview

This project demonstrates an enterprise-style **Security Operations Center (SOC) analytics dashboard** built using cloud-based data ingestion, automated workflows, and Power BI modeling.
<img width="1382" height="768" alt="Gemini_Generated_Image_ibj9ribj9ribj9ri (1)" src="https://github.com/user-attachments/assets/a5b4fedd-edf6-4bd9-8e50-0c99fc1bcaa7" />


It simulates identity, authentication, and security telemetry pipelines using Microsoft ecosystem tools such as Microsoft Graph APIs, Power Automate, and Power BI.

> ⚠️ **Note:** All data used in this project is synthetic or anonymized for portfolio purposes. No production or sensitive organizational data is included.

---

## 🎯 Objectives

- Build SOC-style security analytics dashboards
- Automate ingestion of identity and security logs
- Design scalable Power BI data models
- Develop KPI-driven security intelligence reporting
- Demonstrate API-driven data engineering workflows

---

## 🏗️ Architecture

```
Azure Entra ID / Identity Source
        ↓
Microsoft Graph API (Simulated / Controlled Access)
        ↓
Power Automate (ETL & Workflow Orchestration)
        ↓
Data Transformation (JSON parsing & flattening)
        ↓
Storage Layer (SharePoint / Tables / Files)
        ↓
Power BI Data Model (Star Schema)
        ↓
SOC Analytics Dashboard
```

---

## 📊 Dashboard Features

### 🔐 Identity & Authentication Monitoring
- Sign-in success vs failure tracking
- Authentication pattern analysis
- MFA failure simulation
- Conditional access behavior insights

### 🚨 Security Incident Tracking
- Open incident status monitoring
- Threat categorization views
- Incident resolution tracking

### 🌍 Risk & Anomaly Detection (Simulated)
- Unusual login location detection
- High-frequency authentication failure alerts
- Suspicious access pattern indicators

---

## 📈 Key DAX Measures

### Authentication Success Rate
```DAX
Successful Sign-Ins % =
VAR TotalAttempts = COUNTROWS('Fact_SignIns')
VAR Successes =
    CALCULATE(
        COUNTROWS('Fact_SignIns'),
        'Dim_Status'[Status] = "Success"
    )
RETURN
    DIVIDE(Successes, TotalAttempts, 0)
```

### Open Incidents
```DAX
Open Incidents =
CALCULATE(
    COUNTROWS('Fact_Incidents'),
    'Fact_Incidents'[Status] IN { "New", "In Progress" }
)
```

### Failed Sign-Ins
```DAX
Failed Sign-Ins =
CALCULATE(
    COUNTROWS('Fact_SignIns'),
    'Dim_Status'[Status] = "Failure"
)
```

### High Risk Events
```DAX
High Risk Events =
CALCULATE(
    COUNTROWS('Fact_RiskEvents'),
    'Fact_RiskEvents'[RiskLevel] = "High"
)
```

---

## ⚙️ Data Pipeline

| Step | Tool |
|------|------|
| Data Ingestion | Microsoft Graph API |
| Workflow Orchestration | Power Automate (scheduled triggers) |
| Schema Normalization | JSON parsing & flattening |
| Semantic Modeling | Power BI Star Schema |
| Storage Layer | SharePoint / Tables |

---

## 🧠 Skills Demonstrated

- **Power BI** — DAX, data modeling, dashboard design
- **Data Engineering** — ETL pipeline design and transformation
- **API Integration** — Microsoft Graph API simulation
- **Security Analytics** — SOC-style monitoring and KPI tracking
- **Power Automate** — Workflow automation and scheduling
- **Azure Ecosystem** — Entra ID, cloud storage, identity fundamentals

---

## 🔒 Data Privacy

- All datasets are anonymized or fully synthetic
- No real organizational data is used
- No credentials, API keys, or tenant IDs are exposed
- Secure architecture principles are applied throughout

---

## 📌 Use Cases

This project is suited for:

- Data Analytics portfolio demonstration
- SOC / Security Analyst role showcase
- Power BI + Azure ecosystem skill validation
- API-driven analytics architecture examples

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ — it helps others discover it!
