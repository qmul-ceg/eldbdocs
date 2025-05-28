# Prescription Tables

## Prescriptions Overview

The prescription tables contain patients prescribed the specified medications in the previous 6 months. 

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
## `prescribed_antidepressants`
*Anti-depressant medication (BNF 0403) excluding Amitriptyline hydrochloride (BNF 0403010B0) recorded >=last 6 months, selecting latest Repeat prescription or, where no Repeat prescription is found, latest Acute prescription. With earliest date of prescription course, prescription type and count of prescriptions within the course.*

| fieldname                  | description                                                |
| -------------------------- | ---------------------------------------------------------- |
| latest6m_date              | latest date of code for prescription in the last 12 months |
| latest6m_code              | SNOMED concept id for latest code in the last 12 months    |
| latest6m_name              | code term for latest code in the last 12 months            |
| prescription_type          | type of prescription (repeat / acute)                      |
| prescription_count         | count of prescriptions within the prescription course      |
| prescription_earliest_date | earliest prescription date for the prescription course     |
| bnf_code                   | British National Formulary code for medication             |

See [Antidepressants](../Analysis/Mental_Health.md#Antidepressants) for more detail of the medications included.
## `prescribed_statins`
*Statins meds code (STAT_COD) recorded >=last 6 months, and earliest recorded*

| fieldname                  | description                                                |
| -------------------------- | ---------------------------------------------------------- |
| latest6m_date              | latest date of prescription code in the last 12 months     |
| latest6m_code              | SNOMED concept id for latest code in the last 12 months    |
| latest6m_name              | code term for latest code in the last 12 months            |
| earliest_date              | earliest date of prescription code                         |
| earliest_code              | SNOMED concept id for earliest prescription code           |
| earliest_name              | code term for earliest prescription code                   |
