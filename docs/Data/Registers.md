---
publish: "true"
---
# Register Tables
## Registers Overview

The register tables contain all patients with a specified diagnosis or long term condition. 

### Common Fields
Each table has the following fields:

fieldname   | description
----------  |------------
label       | descriptive label of the table contents. Be 'diabetes'
area_id     | area id for GP Practice
ods_code    | ODS (Organisation Data Service) identifier for the GP Practice.
person_id   | identifier of person
patient_id  | identifier of patient at a practice

### Information format:

**`table name` (full condition name, abbreviation)**  
*The business rules syntax used to create the table with (CLUSTER ID)s and date ranges.*    
Table of fieldnames + description specific to the table  
Additional information  

***
## `anxiety`
*Anxiety code (ANX_CEG) recorded \>= last 24 months.*

fieldname   | description
----------  |------------
latest_date | latest date of code for register
latest_code | SNOMED concept id for latest code
latest_name | code term for latest code

Anxiety covers a range of Common Mental Health disorders, including:
-   Generalised Anxiety and Panic Attacks
-   Anxiety associated with specific behaviours or situations
-   Phobias
-   Obsessive-Compulsive behaviour (OCD)
-   Post-Trauma Stress (PSTD)
-   Occupation-related Stress

For full information on the range of Mental Health registers and prescribing see [Analysis: Mental Health](../Analysis/Mental_Health.md)

## `asthma`
*Asthma code (AST_COD) excluding patients with a more recent resolved code (ASTRES_COD), and include Asthma Treatment meds code (ASTTRT_COD) recorded \>= last 12 months. (QOF)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `atrial_fibrillation` (AF)
*Atrial Fibrillation code (AFIB_COD) excluding patients with a more recent resolved code (AFIBRES_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `autism`
*Autism code (AUTISM_COD) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `cancer`
*Cancer code (CAN_COD) recorded \>= 2003-04-01*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `chd` (Chronic Heart Disease)
*CHD code (CHD_COD) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `ckd` (Chronic Kidney Disease)
*Aged \>= 18 years, and CKD code (CKD_COD) excluding patients with a more recent resolved code (CKDRES_COD) or a more recent CKD 1 or 2 code (CKD1AND2_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `copd` (Chronic Obstructive Pulmonary Disease)
*COPD code (COPD_COD) excluding patients with a more recent resolved code (COPDRES_COD), and where patients have a previous resolved code (COPDRES_COD), COPD code (COPD_COD) after the latest resolved code (COPDRES_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `dementia`
*Dementia code (DEM_COD) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `depression`
*Aged \>= 18 years, and Depression code (DEPR_COD) recorded \>= 2006-04-01 excluding patients with a more recent resolved code (DEPRES_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

For full information on the range of Mental Health registers and prescribing see [Analysis: Mental Health](../Analysis/Mental_Health.md)

## `diabetes` (Diabetes Mellitus, DM)
*Aged \>= 18 years, and Diabetes code (DM_COD) excluding patients with a more recent resolved code (DMRES_COD). Selecting most recent Diabetes Type code (DMTYPE1_COD, DMTYPE2_COD) to define diabetes type.*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code
dm_type       | diabetes type (TYPE_1 or TYPE_2)

## `eating_disorder`
*Eating disorder code (EATINGDIS_CEG) recorded \>= last 24 months*

fieldname     | description
----------    |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

For full information on the range of Mental Health registers and prescribing see [Analysis: Mental Health](../Analysis/Mental_Health.md)

## `epilepsy`
*Epilepsy code (EPIL_COD) excluding patients with a more recent resolved code (EPILRES_COD), and include Epilepsy Drug meds code (EPILDRUG_COD) recorded \>= last 6 months*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `f_hypercholesterolemia` (Familial Hypercholesteremia, FH)
*Familial Hypercholestelemia code (FHYP_COD) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `gestational_diabetes` (GDM)
*Gestational diabetes code (GESTDIAB_COD) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `heart_failure` (HF)
*Heart failure code (HF_COD) excluding patients with a more recent resolved code (HFRES_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `hepatitis_b` (Hepatitis B, HepB, HBV)
*Hepatitis B code (HBV_CEG) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

## `hepatitis_c` (Hepatitis C, HepB, HCV)
*Hepatitis C code (HCV_CEG) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

## `hiv` (Human Immunodeficiency Virus)
*HIV code (HIV_CEG) recorded ever*

fieldname     | description
----------    |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

## `hypertension` (HT)
*Hypertension (HYP_COD) excluding patients with a more recent resolved code (HYPRES_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `learning_disabilities` (LD)
*Learning Disabilities code (LD_COD) recorded ever*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `motor_neurone_disease` (MND)
*Motor Neurone Disease code (MND_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `multiple_sclerosis` (MS)
*Multiple Sclerosis code (MS_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `non_dm_hyperglycaemia` (Non-Diabetic Hyperglycaemia, NDH)
*Aged \>= 18 years, and Non-Diabetic Hyperglycaemia code (NDH_COD) or IGT code (IGT_COD) or Pre-Diabetes code (PRD_COD) excluding patients with a Diabetes code (DM_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `obesity`
*Aged \>= 18 years, and BMI Value code (BMIVAL_COD) \>=30 recorded \>= last 12 months, or Non-Value BMI Indicating \>= 30 code (BMI30_COD) recorded \>= last 12 months*

fieldname     | description
----------    |------------
latest12m_date   | latest date of code for register in the last 12 months
latest12m_code   | SNOMED concept id for latest code in the last 12 months
latest12m_name   | code term for latest code in the last 12 months
bmi30plus_latest12m_date   | latest date of code for register in the last 12 months with BMI \>=30
bmi30plus_latest12m_code   | SNOMED concept id for latest code in the last 12 months with BMI \>=30
bmi30plus_latest12m_name   | code term for latest code in the last 12 months with BMI \>=30

## `osteoporosis`
*Osteoporosis code (OSTEO_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `palliative_care`
*Palliative Care code (PALCARE_COD) excluding patients with a more recent not indicated code (PALCARENI_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `parkinsons_disease`
*Parkinson's Disease code (PD_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `pad` (Peripheral Arterial Disease)
*PAD code (PAD_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `personality_disorder`
*Personality Disorder code (PERSONALITYDIS_CEG)*

fieldname     | description
----------    |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

For full information on the range of Mental Health registers and prescribing see [Analysis: Mental Health](../Analysis/Mental_Health.md)

## `psoriasis`
*Psoriasis code (PSORIASIS_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `rh_arthritis` (Rheumatoid Arthritis)
*Aged \>= 16 years, and Rheumatoid Arthritis code (RARTH_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `severe_mental_illness` (SMI)
*Mental Health code (MH_COD) excluding patients with a more recent remission code (MHREM_COD), and include Lithium meds code (LIT_COD) recorded \>= last 6 months excluding patients with a more recent Lithium Stopped code (LITSTP_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code
lithium_latest_date   | latest, ie prescription, date of code for medication recorded \>= last 6 months
lithium_latest_code   | SNOMED concept id for latest code for medication recorded \>= last 6 months
lithium_latest_name   | code term for latest code for medication recorded \>= last 6 months

Severe Mental Illness (SMI) includes both schizophrenia and bipolar disorder and anyone on lithium who is not also coded having these conditions. For full information on the range of Mental Health registers and prescribing see [Analysis: Mental Health](../Analysis/Mental_Health.md)

## `sti` (Sexually Transmitted Infection, STD)
*Sexually Transmitted Infection code (STI_COD)*

fieldname     | description
----------    |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

## `sickle_cell` (SCD)
*Sickle Cell code (SICKLE_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code

## `stroke_tia` (Stroke / Transient Ischaemia Attack)
*Stroke code (STRK_COD) or TIA code (TIA_COD)*

fieldname     | description
----------    |------------
earliest_date | earliest, ie diagnosis, date of code for register
earliest_code | SNOMED concept id for earliest code
earliest_name | code term for earliest code