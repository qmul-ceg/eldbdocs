# Screening & Check Tables
## Screening & Checks Overview

The Screening & Check tables contain health screening results by patient.. 

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

**`table name` (full condition name, abbreviation)**  
*The business rules syntax used to create the table with (CLUSTER ID)s and date ranges.*    
Table of fieldnames + description specific to the table  
Additional information  

***
## `screen_bowel_cancer`
*Bowel Cancer Screening evidenced results (COLCANSCREV_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code
age_at_event  | age of patient when screening took place

For full information on cancer screening age ranges see [Analysis: Cancer Screening](../Analysis/Cancer_Screening.md)

## `screen_bowel_cancer_declined`
*Bowel Cancer Screening Declined code (COLCANSCRDEC_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

For full information on cervical cancer screening exclusions see [Analysis: Cancer Screening](../Analysis/Cancer_Screening.md#Screening-Exclusions)

## `screen_breast_cancer`
*Female, and Breast Cancer Screening code (BRCANSCR_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code
age_at_event  | age of patient when screening took place

For full information on cancer screening age ranges see [Analysis: Cancer Screening](../Analysis/Cancer_Screening.md)

## `screen_breast_cancer_declined`
*Female, and Breast Cancer Screening Declined code (BRCANSCRDEC_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

## `screen_cervical_cancer`
*Female, and Cervical Cancer Screening code (SMEAR_COD). With exclusion as No Cervix code (NOCX_COD).*  

fieldname                 | description
------------------------  |------------
latest_date               | latest date of code for register
latest_code               | SNOMED concept id for latest code
latest_name               | code term for latest code
age_at_event              | age of patient when screening took place
exclusion_earliest_date   | latest date of code for exclusion
exclusion_earliest_code   | SNOMED concept id for latest exclusion code
exclusion_earliest_name   | code term for latest exclusion code

For full information on cervical cancer screening age ranges and exclusions see [Analysis: Cancer Screening](../Analysis/Cancer_Screening.md)

## `screen_cervical_cancer_declined`
*Female, and Cervical Cancer Screening Declined code (CSDEC_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

***
## `screen_diabetic_retinal`
*Diabetic Retinal Screening code (RET_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

## `screen_diabetic_retinal_excepted`
*Diabetic Retinal Screening Excepted code (RETEXEC_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code

***
## `screen_pulse_check`
*Pulse Check code (PULRHYTH_COD).*  

fieldname     | description
------------  |------------
latest_date   | latest date of code for register
latest_code   | SNOMED concept id for latest code
latest_name   | code term for latest code
pulse_type    | standardised descriptor of pulse type associated with latest_name (regular, irregular, irregularly irregular, unknown)
> [!info]
> Pulse Checks are done opportunistically, which means there is no declined coding as with other screening services.
