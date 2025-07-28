
# Healthcare Power BI Dashboard

This repository contains all of the source data and artifacts needed to build an interactive Healthcare Dashboard in Power BI. The dashboard lets you explore patient demographics, visit patterns, diagnoses, procedures and provider performance.



## 📂 Repository Structure

```
.
├── Dashboard Requirements.pdf    # Functional & visual specs for the dashboard
├── Healthcare Provide Dataset.zip
│   └── cities.csv               # Lookup table of city names & regions
│   └── departments.csv          # Hospital department metadata
│   └── diagnoses.csv            # ICD‐10 diagnosis codes per visit
│   └── insurance.csv            # Payer information per patient
│   └── patients.csv             # Patient master file (demographics)
│   └── procedures.csv           # CPT/HCPCS procedures per visit
│   └── providers.csv            # Physician & staff details
│   └── visits.csv               # Encounter records (dates, dept, provider)
├── README.md                     # You are here
````

* **cities.csv**
  Contains `city_id`, `city_name`, `state` and `region` (e.g. Northeast, West).
* **departments.csv**
  `dept_id`, `dept_name` (e.g. Cardiology, Radiology), and cost center.
* **diagnoses.csv**
  One row per diagnosis: `visit_id`, `icd10_code`, `icd10_description`.
* **procedures.csv**
  One row per procedure: `visit_id`, `cpt_code`, `cpt_description`, `charge_amount`.
* **patients.csv**
  Patient‐level info: `patient_id`, `gender`, `birth_date`, `city_id`, `insurance_id`.
* **insurance.csv**
  Payer info: `insurance_id`, `plan_name`, `plan_type` (e.g. HMO, PPO).
* **providers.csv**
  Provider info: `provider_id`, `provider_name`, `specialty`, `dept_id`.
* **visits.csv**
  Encounters: `visit_id`, `patient_id`, `provider_id`, `visit_date`, `dept_id`, `visit_type` (e.g. Inpatient, Outpatient).



## 📝 Dashboard Requirements

See **Dashboard Requirements.pdf** for full wireframes and KPI definitions. In summary, your Power BI dashboard should include:

1. **Executive Summary**

   * Total patients, visits, revenue (sum of procedure charges), by period
   * Trend‐lines: monthly visits, revenue, avg. length of stay (if inpatient)

2. **Patient Demographics**

   * Gender & age distributions
   * Geographic heatmap by region/city

3. **Clinical Metrics**

   * Top 10 diagnoses & procedures by volume & cost
   * Department utilization (visits, revenue)

4. **Provider Performance**

   * Visits & revenue per provider
   * Average billing per visit & procedure mix

5. **Insurance & Payer Analysis**

   * Visits & revenue by plan type
   * Payer mix trends

6. **Interactivity & Filters**

   * Slicers for date range, department, provider, region, insurance plan


## 🚀 Getting Started

1. **Extract data**
   Unzip `Healthcare Provide Dataset.zip` into this repo root so that all `.csv` files sit alongside this README.

2. **Open Power BI Desktop**

   * **Get Data → Text/CSV →** select each file
   * Define relationships:

     * `patients.city_id` → `cities.city_id`
     * `patients.insurance_id` → `insurance.insurance_id`
     * `visits.patient_id` → `patients.patient_id`
     * `visits.provider_id` → `providers.provider_id`
     * `visits.dept_id` → `departments.dept_id`
     * `diagnoses.visit_id` & `procedures.visit_id` → `visits.visit_id`

3. **Build Data Model**

   * Mark date columns (`birth_date`, `visit_date`) as Date type
   * Create calculated columns / measures for age, length of stay, total charges, etc.

4. **Create Pages & Visuals**
   Follow the layouts in **Dashboard Requirements.pdf** to add report pages:

   * Summary page (cards, KPI visuals, time‐series charts)
   * Demographics page (bar charts, map)
   * Clinical metrics page (tables, bar charts)
   * Provider & payer pages (matrix visuals, bar/line combos)

5. **Publish & Share**

   * Save as `.pbix` and publish to Power BI Service
   * Configure any row‐level security or scheduled refresh as needed



## ⚙️ Requirements

* Power BI Desktop (February 2021 or later)
* Local machine with access to above CSVs
* (Optional) Power BI Pro account for sharing/publishing


