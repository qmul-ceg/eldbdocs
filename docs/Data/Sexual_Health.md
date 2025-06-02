# Sexual Health Tables
## Sexual Health Overview

The Sexual Health tables contain recent information on sexual health and contraception by patient.

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
## `larc` (Long-Acting Reversible Contraception)
*Long-Acting Reversible Contraception (LARC): includes IUCD and Implant procedures. Codes: IUCDFIT_CEG, IUCDREM_CEG, IMPFIT_CEG, IMPREM_CEG.*

fieldname                  | description
-------------------------- |------------
iucdfit_latest_date        | latest date of IUCD fitting code
iucdfit_latest_code        | SNOMED concept id for latest IUCD fit
iucdfit_latest_name        | code term for latest IUCD fit code
iucdremoved_latest_date    | latest date of IUCD removed code
iucdremoved_latest_code    | SNOMED concept id for latest IUCD removed
iucdremoved_latest_name    | code term for latest IUCD removed code
implantfit_latest_date     | latest date of Implant fitting code
implantfit_latest_code     | SNOMED concept id for latest Implant fit
implantfit_latest_name     | code term for latest Implant fit code
implantremoved_latest_date | latest date of Implant removed code
implantremoved_latest_code | SNOMED concept id for latest Implant removed
implantremoved_latest_name | code term for latest Implant removed code
