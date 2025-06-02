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

*NHS Health Check Invite code (NHSHCINV_CEG) recorded \>= last 5 years. Selecting earliest date from LTC table (hypertension, diabetes, atrial_fibrillation, ckd, stroke_tia, heart_failure, pad, f_hypercholesterolemia, prescribed_statins) as ineligibility date and table.*  

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

*All 2024 CORE registers aged \>= 40, excluding patients with hypertension, diabetes, ckd, heart failure, pad, familial hypercholesterolemia, stroke/tia, CHD, atrial fibrillation, and statin prescription.*  
