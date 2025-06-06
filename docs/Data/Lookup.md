# Lookup Tables
The lookup tables (prefixed with `lu_`) contain code maps and categorisations to help with data analysis.
### Information format:

**`table name`**  
*Summary explanation of the table's purpose.*    
Table of fieldnames + description specific to the table.
**Non-Duplicate field** shown in bold as the main lookup field.
Additional information
Supporting tables, such as keys for main table

***
## `lu_ageband`
*Age banded by a selection age band standards.*

| fieldname      | description                                                            |
| -------------- | ---------------------------------------------------------------------- |
| **age**        | patient age                                                            |
| five_year      | five-year age bands (A:0-4 \~ W:110-114)                               |
| five_year_term | five-year age bands text term                                          |
| ten_year       | ten-year age bands (A:0-9 \~ L:110-119)                                |
| ten_year_term  | ten-year age bands text term                                           |
| ons_a          | ONS A age bands (A:0-24 \~ D:65-119)                                   |
| ons_a_term     | ONS A age bands text term                                              |
| ons_b          | ONS B age bands (A:0-24 \~ E:75-119)                                   |
| ons_b_term     | ONS B age bands text term                                              |
| ons_c          | ONS C age bands (A:0-15 \~ I:85-119)                                   |
| ons_c_term     | ONS C age bands text term                                              |
| ons_d          | ONS D age bands (A:0-4 \~ R:85-119)                                    |
| ons_d_term     | ONS D age bands text term                                              |
| ons_e          | ONS E age bands (A:0-84 \~ F:105-119)                                  |
| ons_e_term     | ONS E age bands text term                                              |
| ons_f          | ONS F age bands (A:0-4 \~ S:90-119)                                    |
| ons_f_term     | ONS F age bands text term                                              |
| ons_g          | ONS G age bands (A:0-15 \~ C:65-119)                                   |
| ons_g_term     | ONS G age bands text term                                              |
| esp_1976       | European Std Population 1976 (A:0-4 \~ R:85-111)                       |
| esp_1976_term  | European Std Population 1976 text term                                 |
| esp_2013       | European Std Population 2013 (A:0, B:1-4, C:5-9 \~ U:95-111)           |
| esp_2013_term  | European Std Population 2013 text term                                 |
| eth_band       | ethnicity report bands (A:0-4 \~ E:65-119)                             |
| eth_band_term  | ethnicity report band text term                                        |
| profile_a      | population profiling a bands (A:16-18 \~ J:85-119)                     |
| profile_a_term | population profiling a bands text term                                 |
| profile_b      | population profiling b bands (A:0-4 \~ K:85-119)                       |
| profile_b_term | population profiling b bands text term                                 |
| ceg_piqi       | practice improvement quality indicators age bands (A:0-17 \~ D:65-119) |
| ceg_piqi_term  | practice improvement quality indicators age bands text term            |

### `lu_ageband_key`
*Full text terms for the Age Standard bandings in `lu_ageband`*

| fieldname | description                                    |
| --------- | ---------------------------------------------- |
| age_std   | age banding standard                           |
| band      | banding letter used with the age band standard |
| term      | age band text term                             |

## ## `lu_imd2019`
*IMD 2019  (Indice of Multiple Deprivation) as calculated in 2019 against Lower Super Output Areas (LSOA) defined in 2011.  With national rankings and quintiles by ICB and Local Authority (LAD).*

| fieldname            | description                                                                     |
| -------------------- | ------------------------------------------------------------------------------- |
| **lsoa2011**         | Lower Super Output Area ONS code defined in 2011                                |
| imd2019_score        | Indice of Multiple Deprivation calculated by ONS in 2019 (England only)         |
| country_id           | country identifier                                                              |
| imd2019_rank         | IMD rank by country calculated by ONS                                           |
| imd2019_quintile     | IMD quintile by country                                                         |
| imd2019_decile       | IMD decile by country                                                           |
| icb                  | Integrated Care Board ONS code<br>(England only, otherwise defaults to country) |
| icb_name             | ICB name                                                                        |
| icb_id               | ICB identifier                                                                  |
| imd2019_quintile_icb | IMD quintile by ICB                                                             |
| lad2023              | Local Authority District ONS code defined in 2023                               |
| lad2023_name         | Local Authority District name                                                   |
| imd2019_quintile_lad | IMD quintile by LAD                                                             |
| lad_id               | LAD identifier (London only)                                                    |
| area_id              | area/LAD identifier (North East London only)                                    |

The boundary changes in LSOA 2021 make it difficult to map to the LSOA 2011 based IMD 2019 scores and ranking.  See [lu_lsoa2021](#lu_lsoa2021) for more detail.  LSOA and IMD based on the patient's postcode are provided in [CORE](../Data/Core.md).

| identifier | area                                     |
| ---------- | ---------------------------------------- |
| BD         | Barking & Dagenham                       |
| CL         | City of London                           |
| HK         | Hackney                                  |
| HV         | Havering                                 |
| NH         | Newham                                   |
| RB         | Redbridge                                |
| TH         | Tower Hamlets                            |
| WF         | Waltham Forest                           |
| CH         | City & Hackney                           |
| BHR        | Barking & Dagenham, Havering & Redbridge |
| TNW        | Tower Hamlets, Newham, & Waltham Forest  |

## `lu_localauthority`
*ONS codes for local authorities with associated regional codes*

| fieldname      | description                                                                                              |
| -------------- | -------------------------------------------------------------------------------------------------------- |
| lad2023        | Local Authority District ONS code defined in 2023                                                        |
| lad2023_name   | Local Authority District name                                                                            |
| **lau2021**    | Local Administrative Unit 1 code defined in 2021 (district or unitary authorities)                       |
| lau2021_name   | Local Administrative Unit name                                                                           |
| itl2021_3      | International Territorial Level 3 code defined in 2021 (county, grouped district or unitary authorities) |
| itl2021_3_name | ITL3 2021 name                                                                                           |
| itl2021_2      | International Territorial Level 2 code defined in 2021 (large or grouped counties, urban district)       |
| itl2021_2_name | ITL2 2021 name                                                                                           |
| itl2021_1      | International Territorial Level 1 code defined in 2021 (national region)                                 |
| itl2021_1_name | ITL1 2021 name                                                                                           |

Note that some LAD2023 breakdown into smaller LAU2021, which cause some duplication in the `lad2023` fields.  This is not the case, however, for authorities in London.

### `lu_ons`
*ONS codes for Country, Region, NHS Region, County, ICB, Sub-ICB, Local Authority District, with ODS code and CEG short identifier where applicable.*

| fieldname           | description                             |
| ------------------- | --------------------------------------- |
| id                  | table id                                |
| ons_field           | field name as found in ONS datasets     |
| field_description   | description of ONS field                |
| classification_year | year associated with ONS field category |
| **ons_code**        | ONS code                                |
| ods_code            | ODS code if applicable                  |
| name                | area or organisation name               |
| short_id            | short identifier for name               |

## `lu_lsoa2021`
*Lower Super Output Area (LSOA) defined in 2021 within England and Wales with associated LSOA 2011, LAD 2022 + LAD 2019 (Local Authority), and IMD score 2019*

| fieldname          | description                                                     |
| ------------------ | --------------------------------------------------------------- |
| id                 | table id                                                        |
| lsoa2021_code      | ONS (e-code) for LSOA 2021                                      |
| lsoa2021_name      | LSOA 2021 name (Local Authority name & identifier)              |
| changed            | relationship indicator for LSOA2011 to LSOA2021 (U, S, M, X)    |
| lsoa2011_code      | ONS code (e-code) for LSOA 2011                                 |
| lsoa2011_name      | LSOA 2011 name (Local Authority name & identifier)              |
| lad2022_code       | ONS code (e-code) 2022 for local authority                      |
| lad2022_name       | Local Authority name 2022                                       |
| lad2022_name_wales | Local Authority name 2022 (Welsh Language)                      |
| lad2019_code       | ONS code (e-code) 2019 for local authority                      |
| lad2019_name       | Local Authority name 2019                                       |
| imd2019_score      | Indices of Multiple Deprivation score calculated by ONS         |
| imd2019_quintile   | Indices of Multiple Deprivation quintile calculated for England |

| identifier | change action |
| ---------- | ------------- |
| U          | unchanged     |
| S          | split         |
| M          | merged        |
| X          | fragmented    |

For more information, see the [ONS Open Geography Portal](<https://geoportal.statistics.gov.uk>).

## `lu_ethnicity2`
*Revised SNOMED to ethnicity categorisations for 5+1, 16+1, 18+1 and 19+1 based on 2021 census, with code count and Read2/CTV3 mapping.*

| fieldname      | datatype     | nullable | description                                           |
| -------------- | ------------ | -------- | ----------------------------------------------------- |
| id             | int          | 0        | row id                                                |
| dbid           | int          | 1        | compass cim id                                        |
| code_count     | int          | 1        | count of code recorded in `observation` (at Feb 2025) |
| **sn_code**    | varchar(20)  | 1        | SNOMED code                                           |
| sn_name        | varchar(200) | 1        | SNOMED code name                                      |
| sn_description | varchar(200) | 1        | SNOMED code description                               |
| ethnall        | varchar(50)  | 1        | code included in the PCD ETHNALL refset               |
| eth2016        | varchar(50)  | 1        | code included in the PCD ETH2016 refset               |
| ethnicitynd    | varchar(50)  | 1        | code included in the PCD ETHNICITYND refset           |
| ethnic_5a      | int          | 1        | ethnicity 5+1 (2001) categorisation (0-6)             |
| ethnic_5a_name | varchar(50)  | 1        | ethnicity 5+1 (2001) category names                   |
| ethnic_16      | varchar(2)   | 1        | ethnicity 16+1 categorisation (eg A-Z,99)             |
| ethnic_16_name | varchar(50)  | 1        | ethnicity 16+1 category names                         |
| ethnic_5       | varchar(1)   | 1        | ethnicity 5+1 (2011) categorisation (eg W, M, U)      |
| ethnic_5_name  | varchar(50)  | 1        | ethnicity 5+1 (2011) category names                   |
| ethnic_18      | varchar(2)   | 1        | ethnicity 18+1 categorisation (eg W1-O9, NS, UU)      |
| ethnic_18_name | varchar(150) | 1        | ethnicity 18+1 category names                         |
| ethnic_19      | varchar(2)   | 1        | ethnicity 19+1 categorisation (eg W1-O9, NS, UU)      |
| ethnic_19_name | varchar(150) | 1        | ethnicity 19+1 category names                         |
| r2_code        | varchar(max) | 1        | mapped Read2 codes                                    |
| r3_code        | varchar(max) | 1        | mapped Read3/CTV3 codes                               |

### `lu_ethnicity2_map`
*Cross reference for ethnic categories to ensure consistency across categorisations.*

| fieldname      | datatype     | nullable | description                                      |
| -------------- | ------------ | -------- | ------------------------------------------------ |
| id             | int          | 0        | row id                                           |
| ethnic_5a      | int          | 0        | ethnicity 5+1 (2001) categorisation (0-6)        |
| ethnic_5a_name | varchar(50)  | 1        | ethnicity 5+1 (2001) category names              |
| ethnic_16      | varchar(2)   | 0        | ethnicity 16+1 categorisation (eg A-Z,99)        |
| ethnic_16_name | varchar(50)  | 1        | ethnicity 16+1 category names                    |
| ethnic_5       | varchar(1)   | 0        | ethnicity 5+1 (2011) categorisation (eg W, M, U) |
| ethnic_5_name  | varchar(50)  | 1        | ethnicity 5+1 (2011) category names              |
| ethnic_18      | varchar(2)   | 0        | ethnicity 18+1 categorisation (eg W1-O9, NS, UU) |
| ethnic_18_name | varchar(150) | 1        | ethnicity 18+1 category names                    |
| **ethnic_19**  | varchar(2)   | 0        | ethnicity 19+1 categorisation (eg W1-O9, NS, UU) |
| ethnic_19_name | varchar(150) | 1        | ethnicity 19+1 category names                    |

Fieldnames have been revised to a simpler `ethnic_`+ number of categories, eg `ethnic_18`. Where needed, a letter suffix differentiates categories with the same number of categories, eg `ethnic_5` and `ethnic_5a`.		
- `ethnic_5a` & `ethnic_16` based on 2001 census. Used as standard NHS categories. Chinese classifed as O Other ethnic group / R Chinese  
- `ethnic_5` & `ethnic_18` based 2011 census, also known as Self Defined Ethnicity (SDE). Used by public services and in Governmental reporting. Chinese reclassifed as A Asian / A4 Chinese. Arab added as O Other ethnic group / O2 Arab  
- `ethnic_19` based 2021 census. Roma added as W White / W9 Roma  

## `lu_practice`
*GP Practices in North East London*

| fieldname       | description                                                                                                                                                                                                            |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| area_id         | area identifier for GP Practice (CH, NH, TH, WF, BK, HV, RB). This equates to the former CCGs and current Place-Based Partnerships or Areas within the [North East London ICB](<https://northeastlondon.icb.nhs.uk/>). |
| area            | area name                                                                                                                                                                                                              |
| **ods_code**    | ODS (Organisation Data Service) identifier for the GP Practice. <https://odsportal.digital.nhs.uk/>                                                                                                                    |
| practice_name   | GP Practice name, as defined for CEG reporting. This may differ from the name on ODS records.                                                                                                                          |
| listsize        | currently registered patient count for practice at the run date                                                                                                                                                        |
| status          | activity status for the practice at the run date (active, inactive)                                                                                                                                                    |
| start_date      | date the practice opened                                                                                                                                                                                               |
| end_date        | date the practice closed                                                                                                                                                                                               |
| pcn_ods         | ODS identifier for the Primary Care Network (PCN) associated with the practice                                                                                                                                         |
| pcn_name        | name of associated PCN                                                                                                                                                                                                 |
| clinical_system | clinical data system used by the practice (EMIS, SystmOne)                                                                                                                                                             |
| uprn            | Unique Property Reference Number (UPRN) identifier for the address of the practice. <https://uprn.uk/>                                                                                                                 |

## `lu_smoking`
*Categorisation of smoking codes for Current, Ex and Non Smoker.*

| fieldname       | description                                                                                           |
| --------------- | ----------------------------------------------------------------------------------------------------- |
| id              | row identifier                                                                                        |
| **code**        | code (SNOMED, Read2, CTV3, EMIS Local)                                                                |
| scheme          | code scheme identifier (71, 1040444, 1130062, 1335379)                                                |
| name            | code text description                                                                                 |
| ndasmok_cod     | code cluster id for National Diabetes Audit (NDA): (NDASMOK_COD)                                      |
| smok_cod        | code cluster id for QOF: (SMOK_COD, NULL)                                                             |
| smok_status_qof | code cluster id for QOF: (LSMOK_COD, EXSMOK_COD, NSMOK_COD, NULL)                                     |
| smok_status     | smoking status calculated from QOF & NDA cluster + code term (CSMOK, NONSMOK, EXSMOK, NSMOK, UNKNOWN) |
| dbid            | compass identifier for code                                                                           |
| sn_dbid         | compass identifier for SNOMED code associated with code                                               |

| identifier | code scheme |
| ---------- | ----------- |
| 71         | SNOMED      |
| 1040444    | Read 2      |
| 1130062    | CTV3        |
| 1335379    | EMIS Local  |

| identifier | smoking status                   |
| ---------- | -------------------------------- |
| LSMOK_COD  | Smoker                           |
| EXSMOK_COD | Exsmoker                         |
| NSMOK      | Never Smoked                     |
| CSMOK      | Current Smoker                   |
| NONSMOK    | Current Non-Smoker               |
| EXSMOK     | Exsmoker                         |
| UNKNOWN    | smoking status cannot be defined |

### `lu_smoking_key`
*Full terms for `lu_smoking.dbo.smok_status` identifiers*

| fieldname       | description                          |
| --------------- | ------------------------------------ |
| Id              | numeric identifier to smoking status |
| **smok_status** | smoking status                       |
| name            | name term for smoking status         |
