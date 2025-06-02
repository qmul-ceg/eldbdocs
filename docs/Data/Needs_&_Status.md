# Needs & Status Tables
## Needs & Status Overview

The *status* tables contain recent information on social factors and needs affecting patients that may impact of their health and clinical treatment.

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

## `status_homeless`
*Homelessness code (HOMELESS_COD).*

| fieldname   | description                       |
| ----------- | --------------------------------- |
| latest_date | latest date of code for register  |
| latest_code | SNOMED concept id for latest code |
| latest_name | code term for latest code         |

## `status_housebound`
*Housebound code (HOUSEBOUND_COD).*

| fieldname   | description                       |
| ----------- | --------------------------------- |
| latest_date | latest date of code for register  |
| latest_code | SNOMED concept id for latest code |
| latest_name | code term for latest code         |

## `status_carer`
*Carer code (ISACARER_COD), excluding patients with a more recent Not A Carer code (NOTACARER_COD).*

| fieldname   | description                       |
| ----------- | --------------------------------- |
| latest_date | latest date of code for register  |
| latest_code | SNOMED concept id for latest code |
| latest_name | code term for latest code         |

## `status_interpreter` (interpreter required)
*Includes interpreter requirement codes (REQINTERPRETER_CEG, NOINTERPNEEDED_CEG),  
spoken language interpreter codes (SPOKENLANGINTERP_CEG), preferred language codes,  
and communication support codes (COMSSUPPORT_CEG) including deafblind, sign language, lip-speaker, speech-to-text reporting, and advocate.*

| fieldname                    | description                                             |
| ---------------------------- | ------------------------------------------------------- |
| interpreter_latest_date      | latest date of code for interpreter needed register     |
| interpreter_latest_code      | SNOMED concept id for latest interpreter needed code    |
| interpreter_latest_name      | code term for latest interpreter needed code            |
| interpreter_lang_latest_date | latest date of code for language interpreter register   |
| interpreter_lang_latest_code | SNOMED concept id for latest language interpreter code  |
| interpreter_lang_latest_name | code term for latest language interpreter code          |
| preflang_latest_date         | latest date of code for preferred language register     |
| preflang_latest_code         | SNOMED concept id for latest preferred language code    |
| preflang_latest_name         | code term for latest preferred language code            |
| coms_support_latest_date     | latest date of communication support code               |
| coms_support_latest_code     | SNOMED concept id for latest communication support code |
| coms_support_latest_name     | code term for latest communication support code         |
















