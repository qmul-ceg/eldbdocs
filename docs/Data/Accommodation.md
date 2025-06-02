# Accommodation Tables

## Accommodation Overview

The Accommodation tables contain recent information on patient housing and accommodation.
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
**Measure (full title and synonyms)**
*The business rules syntax used to create the table with (CLUSTER ID)s and date ranges.*    
Table of fieldnames + description specific to the table  
Additional information 
***
## `status_household`
*Household assignment data calculated using the ASSIGN algorithm.*

| Field name        | Description                                                                                                                                                                                               |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `match_status_id` | Internal ID for ASSIGN processing outcome                                                                                                                                                                 |
| `match_status`    | ASSIGN outcome for household residency status. One of:<br>`1` = Residency<br>`2` = Non-Residential Property<br>`3` = Imprecise Match<br>`4` = Multiple Address<br>`5` = No Match Data<br>`6` = Improbable |
| `property_id`     | Internal database ID for property matched by ASSIGN                                                                                                                                                       |
| `patient_count`   | Count of patients found at the `property_id`                                                                                                                                                              |

*See Data Analysis and Information: Household for more details.*

