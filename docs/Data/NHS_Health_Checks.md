---
publish: "true"
---

# Register Tables

## Registers Overview

The register tables contain patients with a specified diagnosis or long term condition. 

### Common Fields

Each table has the following fields:

| fieldname  | description                                                     |
| ---------- | --------------------------------------------------------------- |
| label      | descriptive label of the table contents. Be 'diabetes'          |
| area_id    | area id for GP Practice                                         |
| ods_code   | ODS (Organisation Data Service) identifier for the GP Practice. |
| person_id  | identifier of person                                            |
| patient_id | identifier of patient at a practice                             |

### Information format:

**`nhs_healthcheck` (NHS Health Checks, NHS HC)**  
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
| valid_nhshc          | Y/N column for NHS HC validity                                    |

***

## `nhs_healthcheck_declined`

*NHS Health Check Declined code (NHSHCDEC_CEG) recorded \>= last 5 years.*  

| fieldname   | description                       |
| ----------- | --------------------------------- |
| latest_date | latest date of code for register  |
| latest_code | SNOMED concept id for latest code |
| latest_name | code term for latest code         |

***

## `nhs_healthcheck_invite`

*NHS Health Check Invite code (NHSHCINV_CEG) recorded \>= last 5 years. Selecting earliest date from LTC table (hypertension, diabetes, atrial_fibrillation, ckd, stroke_tia, heart_failure, pad, f_hypercholesterolemia, prescribed_statins) as ineligibility date and table.*  

| fieldname            | description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| latest_date          | latest date of code for register                                  |
| latest_code          | SNOMED concept id for latest code                                 |
| latest_name          | code term for latest code                                         |
| inelig_earliest_date | earliest date a patient became ineligible for an NHS Health Check |
| inelig_table         | name/reason of ineligibility                                      |
| valid_nhshc          | Y/N column for NHS HC validity                                    |

***

## `nhs_healthcheck_elig2023`

*All 2023 CORE registers aged \>= 40, excluding patients with hypertension, diabetes, ckd, heart failure, pad, familial hypercholesterolemia, stroke/tia, CHD, atrial fibrillation, and statin prescription.*  
