# Vaccination Tables

## Vaccinations Overview

The vaccination tables contain patients vaccinated with the specified medications.

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

**`table name` (full name, abbreviation)**  
*The business rules syntax used to create the table with (CLUSTER ID)s and date ranges.*    
Table of fieldnames + description specific to the table  
Additional information  

***
## `vaccination_covid`
*Covid Vaccination code (C19VACC_CEG) or Covid Vaccination meds code (C19VACCMEDS_CEG)*

| fieldname   | description                                       |
| ----------- | ------------------------------------------------- |
| latest_date | latest date of code for immunisation              |
| latest_code | SNOMED concept id for latest code                 |
| latest_name | code term for latest code                         |
| code_type   | source of code (a = admin record, m = medication) |
| vacc_num    | estimated count of covid vaccinations received    |

