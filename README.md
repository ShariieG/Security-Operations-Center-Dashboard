# 🔐 Security Operations Center (SOC) Log Analytics Dashboard

A Power BI security operations dashboard fed by an automated identity-telemetry pipeline: **Microsoft Entra ID sign-in and risk data → Microsoft Graph API → Power Automate → SharePoint → Power BI**. It gives security teams one view of authentication health, risky users, open incidents and the most common sign-in failure reasons.

`Power BI` `DAX` `Power Query` `Power Automate` `Microsoft Graph API` `Entra ID` `SharePoint`

<img width="1382" height="768" alt="SOC dashboard overview (sensitive values redacted)" src="https://github.com/user-attachments/assets/a5b4fedd-edf6-4bd9-8e50-0c99fc1bcaa7" />

> 🔒 Sensitive values are redacted in the screenshot. The repo contains no production data, credentials, API keys or tenant IDs.

---

## 🎯 What it shows

| Area | Visuals |
|---|---|
| **Authentication health** | Successful sign-in %, login volume by platform (Office 365, SharePoint, Teams and more) |
| **Compliance** | Azure-compliant device % |
| **Incidents** | Incident resolution rate, open incidents needing attention |
| **Risk** | At-risk users, high-risk events |
| **Root cause** | Top sign-in failure reasons (blocked sign-ins, locked accounts, failed strong authentication and more) |
| **Navigation** | Overview, Identity & Access, Audit and Threat Management pages |

---

## 🏗️ Architecture

```
Microsoft Entra ID (sign-in, risk and incident data)
        ↓
Microsoft Graph API
        ↓
Power Automate: scheduled extraction and orchestration
        ↓
JSON parsing and flattening
        ↓
SharePoint lists (storage layer)
        ↓
Power BI star-schema model (Power Query + DAX)
        ↓
SOC dashboard
```

---

## 📈 Key DAX measures

**Successful sign-ins %**
```dax
Successful Sign-Ins % =
VAR TotalAttempts = COUNTROWS('Fact_SignIns')
VAR Successes =
    CALCULATE(COUNTROWS('Fact_SignIns'), 'Dim_Status'[Status] = "Success")
RETURN
    DIVIDE(Successes, TotalAttempts, 0)
```

**Failed sign-ins**
```dax
Failed Sign-Ins =
CALCULATE(COUNTROWS('Fact_SignIns'), 'Dim_Status'[Status] = "Failure")
```

**Open incidents**
```dax
Open Incidents =
CALCULATE(
    COUNTROWS('Fact_Incidents'),
    'Fact_Incidents'[Status] IN { "New", "In Progress" }
)
```

**High-risk events**
```dax
High Risk Events =
CALCULATE(COUNTROWS('Fact_RiskEvents'), 'Fact_RiskEvents'[RiskLevel] = "High")
```

---

## 🧠 Skills demonstrated

- **Data engineering:** API-driven ETL with Power Automate, including JSON flattening
- **Data modelling:** star schema with sign-in, incident and risk fact tables
- **DAX:** KPI measures and filtered aggregations
- **Security analytics:** SOC-style KPIs and failure root-cause analysis
- **Dashboard design:** gauge-led KPI row, drill-down pages and clear status colours

---

## 📁 Repository contents

This repo documents the project. The `.pbix` file and source data aren't published, for security reasons.

---

## 👩🏾‍💻 Author

**Sharon Galela** · [LinkedIn](https://www.linkedin.com/in/sharon-galela-6998bb265) · [GitHub](https://github.com/ShariieG)
