# Referral Tables
## Referrals Overview

The Referral tables contain contain recent referral information by patient.

### Common Fields
Each table has the following fields:

| fieldname  | description                                                     |
| ---------- | --------------------------------------------------------------- |
| label      | descriptive label of the table contents. eg 'diabetes'          |
| area_id    | area id for GP Practice                                         |
| ods_code   | ODS (Organisation Data Service) identifier for the GP Practice. |
| person_id  | identifier of person                                            |
| patient_id | identifier of patient at a practice                             |

### Information format
**`table name` (full condition name, abbreviation)**  
*The business rules syntax used to create the table with (CLUSTER ID)s and date ranges.*    
Table of fieldnames + description specific to the table  
Additional information
***
## `referral_social_prescribing`
Social referral prescribed (SOCPRESREF_COD)

| fieldname          | description                                                                            |
| ------------------ | -------------------------------------------------------------------------------------- |
| latest_date        | latest code date                                                                       |
| latest_code        | latest code                                                                            |
| latest_name        | latest code name                                                                       |

