## Weekly Logistics Performance & Risk Monitoring Pipeline

This project implements an **industry-style logistics monitoring system** that transforms raw order-level data into weekly operational KPIs, classifies delivery risk, and automates insight generation using **Python** and **n8n**.

The goal is to mirror how analytics and operations teams monitor delivery reliability, identify risk early, and communicate actionable insights—moving from static analysis to an automated, decision-ready workflow.

---

## Project Summary

This repository demonstrates an **end-to-end analytics and automation pipeline** for monitoring logistics performance on a weekly basis.

The project combines:

- Python-based KPI engineering for structured, reproducible analysis  
- Rule-based risk classification aligned with operational thresholds  
- n8n workflow automation to orchestrate data ingestion, logic execution, and downstream outputs  
- AI-assisted explanation to translate metrics into plain-English insights for stakeholders  


## Problem Statement

In real-world logistics operations, teams face three recurring challenges:

- Raw data is abundant, but actionable weekly insights are not  
- Performance issues (late deliveries, regional disruptions) are often detected too late  
- Manual reporting does not scale and is prone to inconsistency  

Operations teams need:

- Consistent weekly KPIs  
- Clear risk signals (not just raw metrics)  
- Automated workflows that reduce manual effort while improving interpretability  

This project addresses these challenges by designing a system that measures, classifies, and explains logistics risk in a way that supports operational decision-making.

---

## Solution Overview

The solution is structured as a **two-layer system**:

### Analytics Layer (Python / Jupyter)

- Ingest raw logistics data  
- Engineer weekly KPIs aligned with business questions  
- Apply deterministic risk classification logic  
- Output clean, machine-readable datasets  

### Automation Layer (n8n)

- Trigger workflows on a schedule or manual execution  
- Fetch KPI outputs from a remote repository  
- Apply business rules and filtering  
- Generate human-readable risk explanations  
- Export finalized outputs for reporting or downstream systems  

This separation reflects how analytics is typically deployed in industry: **clear data contracts upstream, automation and orchestration downstream**.

---

## Tech Stack

The project uses a focused, production-relevant stack:

### Analytics & Data Processing

- Python  
- pandas  
- Jupyter Notebook  

### Workflow Automation

- n8n (scheduled triggers, data transformation, orchestration)  

### AI & Interpretation

- OpenAI Chat Model (used strictly for explanation, not decision-making)  

### Data Formats

- CSV (analytics outputs)  
- JSON (workflow data exchange)  


## KPI Engineering & Risk Design


Instead of exploratory metrics, the KPIs were designed to answer **specific operational questions**:

| KPI | Description | Business Relevance |
|----|-------------|--------------------|
| `late_delivery_rate` | Share of orders delivered late in a given week | Measures delivery reliability |
| `avg_delivery_delay` | Average delay (in days/weeks) for late orders | Captures severity of delays |
| `cancellation_rate` | Proportion of canceled orders | Indicates downstream customer impact |
| `total_orders` | Total number of orders per week | Represents operational scale |
| `top_risk_region` | Region with highest late delivery rate | Highlights geographic risk concentration |
| `top_region_risk_rate` | Late delivery rate of the top risk region | Quantifies regional severity |

These KPIs reflect how logistics managers evaluate performance during **weekly ops reviews**, rather than ad-hoc analysis.

---

## Risk Classification Logic

Beyond KPI calculation, the project introduces **explicit business logic** to translate metrics into operational signals.

Each weekly record is classified into a **risk level**:

- **LOW** – Performance within acceptable thresholds  
- **MEDIUM** – Early warning signals; monitor closely  
- **HIGH** – Requires immediate operational attention  

Risk classification is driven by deterministic rules based on:
- Late delivery rate thresholds
- Average delivery delay severity
- Combined performance patterns across weeks

This approach mirrors industry practice:
- **Rules define risk**
- **Analytics supports decisions**
- **AI explains outcomes**, but does not replace logic

The separation ensures transparency, auditability, and trust in automated decisions.

---

## Workflow Automation with n8n

The second phase of the project operationalizes the analysis using **n8n**, transforming static outputs into an automated pipeline.

The n8n workflow performs the following steps:

1. **Trigger**
   - Manual execution or scheduled trigger (weekly ops cadence)

2. **Data Ingestion**
   - Fetches KPI CSV files directly from a GitHub repository
   - Mimics enterprise patterns where data is sourced from shared repositories or upstream systems

3. **Data Parsing**
   - Converts CSV files into structured items for processing

4. **Business Logic Execution**
   - Applies rule-based risk classification
   - Filters records requiring attention (e.g., HIGH risk weeks)

5. **AI-Powered Risk Explanation**
   - Uses an AI model to generate concise, plain-English explanations
   - Explains *why* a week is flagged as risky, without influencing the classification itself

6. **Output Generation**
   - Produces clean, structured CSV outputs
   - Ready for reporting, dashboards, or downstream workflows


## Outputs & Deliverables

The primary output is a **weekly risk monitoring table**, where each row represents one operational week and includes:

- Engineered performance KPIs
- A deterministic risk level
- A human-readable explanation of *why* the risk was assigned

### Example Output Fields

| Field | Description |
|------|-------------|
| `year_week` | Weekly time window for monitoring |
| `late_delivery_rate` | Proportion of late deliveries |
| `avg_delivery_delay` | Average delay severity |
| `top_risk_region` | Region contributing most to risk |
| `risk_level` | LOW / MEDIUM / HIGH classification |
| `risk_explanation` | AI-generated operational summary |

### Why This Output Matters

This format is intentionally aligned with real operational use cases:

- **Managers** can scan risk levels quickly
- **Analysts** can trace decisions back to KPIs
- **Stakeholders** can understand issues without reading raw metrics
- **Systems** can consume the output programmatically

Instead of dashboards alone, the project produces **portable, structured artifacts** that can plug into alerts, reports, or BI tools.

---

## How to Run the Project

This project is designed to be easy to reproduce and extend.

### 1. Analytics (Python)

1. Clone the repository
2. Open the Jupyter Notebook in the `/notebooks` directory
3. Run all cells to:
   - Load raw logistics data
   - Generate weekly KPIs
   - Apply risk classification logic
4. Export the final CSV outputs

The notebook is written as a **production-style analytics script**, not an exploratory notebook.

### 2. Automation (n8n)

1. Import the provided n8n workflow JSON
2. Ensure the workflow nodes are connected in the documented order
3. Configure:
   - GitHub raw file URL (HTTP Request node)
   - Trigger type (manual or scheduled)
4. Execute the workflow to:
   - Fetch KPI data
   - Apply logic and filtering
   - Generate AI explanations
   - Export final CSV outputs

No local file system access is required; the workflow operates entirely on hosted data.

---

## Key Learning Outcomes & Industry Alignment

This project demonstrates a transition from **learning tools** to **thinking like an analytics engineer**.

Key competencies showcased:

- Designing KPIs around business questions
- Translating metrics into operational risk signals
- Writing deterministic, auditable business logic
- Automating analytics workflows using n8n
- Using AI responsibly to enhance interpretability, not decision-making
- Producing clean data contracts for downstream systems

Overall, the project reflects how modern data and AI teams operate:
**Python for logic, automation for scale, and AI for communication**.

