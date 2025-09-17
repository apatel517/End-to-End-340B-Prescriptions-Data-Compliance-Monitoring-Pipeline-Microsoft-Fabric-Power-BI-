# 🏥 End-to-End 340B Prescriptions Data Compliance Monitoring Pipeline – Microsoft Fabric + Power BI

This project showcases a **fully automated, event-driven 340B compliance monitoring pipeline** using Microsoft Fabric and Power BI.  
It replaces **manual Excel-based compliance reviews** with scalable, auditable, and real-time dashboards.

---

## 🏥 Why I Built This

Many health systems still check 340B compliance manually using spreadsheets or Excel:

- Staff filter **prescriptions** by provider, patient, location, and Medicaid.  
- Use pivot tables and VLOOKUPs to generate monthly reports.  
- Slow, error-prone, and reactive.

With thousands of **prescriptions per month**, manual checks cannot scale—and mistakes can cost millions.

---

## 🚀 How This Project Solves It

I built a **fully automated, event-driven pipeline**:

### 1. Bronze (Notebook)
- Load raw CSVs: **Prescription**, Patient, Provider, Location  
- Store in Lakehouse tables

### 2. Silver (Dataflow Gen2)
- Clean, standardize, join datasets  
- Apply compliance flagging rules to each **prescription**:
  - Provider employment  
  - Patient eligibility (last encounter + 12 months)  
  - 340B location  
  - Medicaid  
  - Duplicate discount risk  

### 3. Gold (Dataflow Gen2)
- Classify **each prescription** as **Compliant** or **Non-Compliant**, with reason

### 4. Automated Trigger
- Pipeline is **event-driven**: runs end-to-end when a new **prescription file** drops in Lakehouse  
- Power BI dashboards update in near real-time  
- Eliminates manual scheduling or intervention

### 5. SQL Queries for Validation
- Optional: run SQL queries on Lakehouse tables to tally results per **prescription**  
- Cross-check Power BI dashboards to ensure accuracy and auditability

---

## 🧪 Synthetic Data

Generated using Python and R:

- Realistic 340B workflows  
- Safe testing without PHI  
- Supports full Bronze → Silver → Gold → Validation workflow

**Files created:**

- `patient_eligibility.csv`  
- `prescriptions.csv`  
- `provider_roster.csv`  
- `location.csv`  

---

## 🧰 Tools & Technologies

- **Microsoft Fabric:** Lakehouse, Pipelines, Dataflow Gen2  
- **PySpark Notebooks:** Bronze layer ingestion  
- **Dataflow Gen2:** Silver and Gold transformations  
- **Power BI:** Dashboards and KPIs  
- **Python & R:** Data simulation for Prescription, Patient, Provider, and Location datasets  
- **SQL Endpoints:** Validation queries to ensure Power BI accuracy  

---

## 📊 Compliance Flagging Logic

| Flag | Logic | Human Explanation |
|------|-------|-----------------|
| Provider Employment | Prescription date not within provider’s employment dates | Checks provider was active at CE when Rx was issued |
| Patient Eligibility | Prescription date > last encounter + 12 months | Patients eligible only up to 12 months after last encounter |
| 340B Location | Location flagged as non-340B | Prescription must come from valid 340B site |
| Medicaid | Prescription billed to Medicaid | Flags ineligible prescriptions |
| Duplicate Discount | Same prescription in Medicaid & 340B | Prevents double-dipping |

---

## ✅ Business Impact

- ⛔ Eliminated manual Excel-based compliance reviews  
- 🔄 Fully automated **event-driven pipeline** for ~8K prescriptions/month  
- 📊 Power BI dashboards update in real-time  
- ⚙️ SQL validation ensures dashboards match pipeline outputs  
- 💰 Identified **$4M in non-compliant prescriptions** and top drivers  

---

## 🔗 Connect With Me

- 📧 Email: [asadpatel517@gmail.com](mailto:asadpatel517@gmail.com)  
- 💼 LinkedIn: [https://linkedin.com/in/asad--patel](https://linkedin.com/in/asad--patel)  
- 💻 GitHub: [https://github.com/apatel517](https://github.com/apatel517)

---

## 📄 View Full Project Documentation

👉 **[Click here to view the complete PDF](./340B-Fabric-Project/340B_Fabric_Portfolio_AsadPatel_Final07.26.pdf)**  

