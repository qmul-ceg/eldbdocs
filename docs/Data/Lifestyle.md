---

publish: "true"
---

# Lifestyle Status

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

## `status_household`

*Calculated using ASSIGN algorithm.*

## `status_household`

*Household assignment data calculated using the ASSIGN algorithm.*

| Field name        | Description                                                                                                                                                                                               |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `match_status_id` | Internal ID for ASSIGN processing outcome                                                                                                                                                                 |
| `match_status`    | ASSIGN outcome for household residency status. One of:<br>`1` = Residency<br>`2` = Non-Residential Property<br>`3` = Imprecise Match<br>`4` = Multiple Address<br>`5` = No Match Data<br>`6` = Improbable |
| `property_id`     | Internal database ID for property matched by ASSIGN                                                                                                                                                       |
| `patient_count`   | Count of patients found at the `property_id`                                                                                                                                                              |

*See Data Analysis and Information: Household for more details.*

## `status_carer`

*Carer code (ISACARER_COD), excluding patients with a more recent Not A Carer code (NOTACARER_COD).*

| fieldname   | description                       |
| ----------- | --------------------------------- |
| latest_date | latest date of code for register  |
| latest_code | SNOMED concept id for latest code |
| latest_name | code term for latest code         |

## `status_interpreter`

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
