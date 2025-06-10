# NHS Health Check Tables

## NHS Health Checks Overview

The NHS Health Check tables contain recent information on NHS Health Checks (invited, done, declined) by patient.

### Common Fields
Each table has the following fields:

| fieldname  | description                                                     |
| ---------- | --------------------------------------------------------------- |
| label      | descriptive label of the table contents. eg 'diabetes'          |
| area_id    | area id for GP Practice                                         |
| ods_code   | ODS (Organisation Data Service) identifier for the GP Practice. |
| person_id  | identifier of person                                            |
| patient_id | identifier of patient at a practice                             |

### Information format:

**`table name` (relationship)**
**Measure (full title and synoymns)**
*The business rules syntax used to create the table with (CLUSTER ID)s and date ranges.*    
Table of fieldnames + description specific to the table  
Additional information  

***
## `nhs_healthcheck` (NHS Health Check done, NHS HC)
*NHS Health Check code (NHSHC_CEG) recorded \>= last 5 years. Selecting earliest date from LTC table (hypertension, diabetes, atrial_fibrillation, ckd, stroke_tia, heart_failure, pad, f_hypercholesterolemia, prescribed_statins) as ineligibility date and table.*  

| fieldname            | description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| earliest5y_date      | earliest date of health check code in last 5 years                |
| earliest5y_code      | SNOMED concept id for earliest code                               |
| earliest5y_name      | code term for earliest code                                       |
| latest_date          | latest date of code for register                                  |
| latest_code          | SNOMED concept id for latest code                                 |
| latest_name          | code term for latest code                                         |
| inelig_earliest_date | earliest date a patient became ineligible for an NHS Health Check |
| inelig_table         | name/reason of ineligibility                                      |
| valid_nhshc          | NHS Health Check validity (Y/N)                                   |

For full information on NHS Health Checks and eligibility criteria see [Analysis: NHS Health Checks](../Analysis/NHS_Health_Checks.md)

## `nhs_healthcheck_declined`
*NHS Health Check Declined code (NHSHCDEC_CEG) recorded \>= last 5 years.*  

| fieldname   | description                       |
| ----------- | --------------------------------- |
| latest_date | latest date of code for register  |
| latest_code | SNOMED concept id for latest code |
| latest_name | code term for latest code         |

## `nhs_healthcheck_invite`
*NHS Health Check Invite code (NHSHCINV_CEG) recorded \>= last 5 years. Selecting earliest date from LTC tables (hypertension, diabetes, atrial_fibrillation, ckd, stroke_tia, heart_failure, pad, f_hypercholesterolemia, prescribed_statins) as ineligibility date and table.*  

| fieldname            | description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| latest_date          | latest date of code for register                                  |
| latest_code          | SNOMED concept id for latest code                                 |
| latest_name          | code term for latest code                                         |
| inelig_earliest_date | earliest date a patient became ineligible for an NHS Health Check |
| inelig_table         | name/reason of ineligibility                                      |
| valid_nhshc          | NHS Health Check validity (Y/N)                                   |

For full information on NHS Health Checks and eligibility criteria see [Analysis: NHS Health Checks](../Analysis/NHS_Health_Checks.md)

## `nhs_healthcheck_elig2024`
*CORE 2024 table filtered for patients aged \>= 40  
Excluding patients with an ELDB2024 record of Hypertension, Diabetes, CKD, Heart Failure, PAD, Familial Hypercholesterolemia, Stroke/TIA, CHD, Atrial Fibrillation, or Statin prescription.*  

| fieldname      | description                                                                                                                 |
| -------------- | --------------------------------------------------------------------------------------------------------------------------- |
| relrun_date    | relative run date for the database build                                                                                    |
| person_id      | identifier of person across multiple NHS organisations. Analogous to NHS Number.                                            |
| patient_id     | identifier of patient at a practice. Analogous to EMIS number.                                                              |
| age            | age in years of patient on the run date                                                                                     |
| sex            | sex (Female, Male, Other, Unknown) for patient                                                                              |
| ethnicity_code | latest ethnicity SNOMED concept id.                                                                                         |
| ethnic_16      | ethnicity 16+1 categorisation (eg A-Z,99)                                                                                   |
| ethnic_5a      | ethnicity 5+1 (2001) categorisation (0-6)                                                                                   |
| area_id        | area id for GP Practice (CH, NH, TH, WF, BK, HV, RB).                                                                       |
| ods_code       | ODS (Organisation Data Service) identifier for the GP Practice.                                                             |
| practice_name  | GP Practice name, as defined for CEG reporting. This may differ from the name on ODS records.                               |
| reg_date       | calculated registration date for patient at practice                                                                        |
| lsoa_2011      | LSOA (Lower Super Output Area) for 2011 relating to the patient's identified current address.                               |
| pt_area_id     | area_id based on patient's identified current address. NULL means the patient lives outside the North East London ICB area. |

> Note:
> Columns `ceg_16` and `nhs_5` have been renamed `ethnic_16` and `ethnic_5a` respectively in order to fit with the revised [ethnicity tables](Lookup.md#lu_ethnicity2).