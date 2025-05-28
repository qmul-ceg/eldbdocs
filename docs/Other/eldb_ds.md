East London Database

**eldb2024 Data and Schema**

# Table of Contents

[Table of Contents [1](#table-of-contents)](#table-of-contents)

[Overview [1](#overview)](#overview)

[Accessing the ELDB Server
[2](#accessing-the-eldb-server)](#accessing-the-eldb-server)

[eldb2024 Data [3](#eldb2024-data)](#eldb2024-data)

[eldb2024 Structure & Information
[4](#eldb2024-structure-information)](#eldb2024-structure-information)

[Lookup Tables & Information
[6](#lookup-tables-information)](#lookup-tables-information)

[CORE [11](#core)](#core)

[Registers [13](#registers)](#registers)

[Measures [21](#measures)](#measures)

[Prescriptions [24](#prescriptions)](#prescriptions)

[Vaccinations [25](#vaccinations)](#vaccinations)

[NHS Health Checks [26](#nhs-health-checks)](#nhs-health-checks)

[Screening & Checks [27](#screening-checks)](#screening-checks)

[Smoking, Alcohol & Drug Use
[29](#smoking-alcohol-drug-use)](#smoking-alcohol-drug-use)

[Sexual Health [31](#sexual-health)](#sexual-health)

[Lifestyle Status [32](#lifestyle-status)](#lifestyle-status)

[Data Analysis and Information
[34](#data-analysis-and-information)](#data-analysis-and-information)

[Appendix 1: Alcohol Units Per Week
[39](#appendix-1-alcohol-units-per-week)](#appendix-1-alcohol-units-per-week)

[Appendix 2: Database Version Log
[40](#appendix-2-database-version-log)](#appendix-2-database-version-log)

[Document Version Log
[41](#document-version-log)](#document-version-log)

# Overview

The East London Database is a series of annual databases containing data
from the 1st April for patients registered with GP practices within
north east London on that date. The coverage has expanded over the years
to now include all practices in the North East London ICB area (City &
Hackney, Newham, Tower Hamlets, Waltham Forest, Redbridge, Barking &
Dagenham, and Havering).

- **eldb2014 -- eldb2019**: contain data obtained from EMIS for inner
  east London. Hosted in MS Access and not currently available to
  external analysts.

- **eldb2020**: contains data from EMIS for inner east London. It is
  hosted and available to external analysts on our ELDB SQL Server.

- **eldb2021 -- onwards**: contains data from our copy of the Discovery
  Data Service for all North East London. It is hosted and available to
  external analysts on our ELDB SQL Server.

Each year contains tables providing the earliest and/or latest codes for
the standard QOF registers and clinical measures (Blood Pressure, HbA1c
etc) as well as additional register, activity, and status tables. We
have made changes and improvements to the schema and included tables for
the database each year.

This guide provides information on the data and schema specifically for
East London Database 2024 (eldb2024). Please refer to other documents
and sources for information about previous years.

**\
**

# Accessing the ELDB Server

The ELDB SQL Server is secured inside a Virtual Private Network (VPN)
with Two-Factor Authentication (2FA). Users connect into the VPN using
client software installed on their laptop or PC and authenticate using a
smart phone app. Querying the data will require appropriate software
(such as MS Access, SQL Server Management Studio, Power Query) installed
on the user's device. Details are provided in other documents.

Because this setup requires installing software on devices not managed
by CEG or QMUL, there is a limit to the amount of support CEG can
provide for this process or for resolving problems. CEG can help with
connection issues to the VPN and to the ELDB server, and provide a
series of guides for this purpose. Installation issues will need to be
handle by the device's user or administrator.

**\
**

# eldb2024 Data

eldb2024 contains data derived from the Discovery Data Service (DDS),
via the CEG Compass database, for all practices within the North East
London ICB area (City & Hackney, Newham, Tower Hamlets, Waltham Forest,
Redbridge, Barking & Dagenham, and Havering). Voror, the company
managing DDS, receive data on a daily basis from EMIS and TTP, the two
clinical system providers in the area, which they process into the DDS.
CEG maintain an API to file and update a copy of this data each night
into our Compass database. The eldb2024 database has been created from
Compass, using purpose built SQL scripts, as a one-off snapshot of the
data at 01/04/2024.

The ELDB data is not an exact copy, therefore, of the patient records
held on the GP clinical systems. Not all data fields are passed to Voror
and the data undergoes a series of transformations on its path to the
eldb2024 database. The clinical systems are also designed for managing
the healthcare of currently registered patients and so the data they
contain is constantly being updated and is not always in sync with DDS
and Compass. Compass has been validated as providing results close to
those pulled from clinical systems and further validation checks were
carried out on the eldb2024 results. Reports derived from eldb2024
should not be compared, however, with reports derived directly from EMIS
Web and SystmOne.

For eldb2024, a snapshot of the full Compass data was taken and used to
build the register and other tables. This means that the source data is
consistent throughout eldb2024 and anomalies of patient inclusion,
age-at-event and code changes, as found in previous ELDB, should not be
present.

## Known Data Issues:

**Patient Registration** -- A patient's current practice registration
and date, as shown in the CORE table, is calculated using the available
registration data in Compass. The EMIS API to DDS does not contain the
full detailed registration process history which EMIS uses to refine its
GP Practice Currently Registered list, particularly in relation to
patients moving to or from a practice. The practice lists in ELDB can
therefore include patients that EMIS would define as having moved to
another practice. Listsizes with EMIS may differ by ±2%.

**Code Episode** -- EMIS uses the Episode field for an entered clinical
code in its QOF syntax to identify patients and diagnosis dates for
Depression and Epilepsy. This field indicates whether an entered code
relates to a new or first episode of the condition, or an ongoing
review. The EMIS API however does not pass this field to DDS. Without
this field, the registers derived from Compass can only find the initial
diagnosis date of the condition. Furthermore, it means patients with a
resolved code followed by a code with a Review or End Episode flag are
excluded from EMIS reports but included in Compass based reports.

**\
**

# eldb2024 Structure & Information

All ELDB databases are primarily based on a star schema consisting of a
central CORE table, containing every registered patient (1 line per
patient), linked by a patient identifier to multiple tables containing
the details for patients found for specific Registers, Measures and
Activities. Additional columns and Lookup tables are provided where
useful to assist with classification and categorisation.

In eldb2024 the database schema, build history and design is set out in
the following tables:

### Tables

**db_tables**

List of all tables within the database

- sc -- table schema

- table_name -- table name

- object_id -- table id, as defined by server

- create_date -- creation date of table

- create_time -- creation time of table

- modified_date -- last modification date of table

- Modified_time -- last modification time of table

- column_count -- count of columns within table

- row_count -- count of rows in table

### Columns

**db_columns**

List of all columns within the database

- sc -- table schema

- table_name -- table name

- object_id -- table id, as defined by server

- column_id -- column id and order of column within table

- column_name -- column name

- datatype -- column data type

- max_length -- maximum length of data within column

- is_nullable -- column may contain NULLs. Yes (1) or No (0).

- is_primary_key -- column is included within the table's Primary Key

- is_index -- column is included within a table index

- column_count -- count of entries in column

### Codes

**db_codes**

List of codes, with counts, for each code column in the database

- id -- code id within the table

- table_name -- table name

- column_name -- column name

- code -- SNOMED code

- code_name -- code description

- code_count -- count of codes within column

See the NHS Digital PCD Portal for more information on the standard
codesets:

<https://digital.nhs.uk/data-and-information/data-collections-and-data-sets/data-collections/quality-and-outcomes-framework-qof/quality-and-outcome-framework-qof-business-rules/primary-care-domain-reference-set-portal>

### Table Counts

**db_counts**

Patient counts by Practice for each Register and Activity table within
the database.

- area_id -- area id for GP Practice

- ods_code -- ODS (Organisation Data Service) identifier for the GP
  Practice.

- practice_name -- GP Practice name.

- clinical_system -- clinical data system (EMIS, SystmOne) used within
  the GP Practice. This is based on information from CEG reporting.

- \[column for each register/activity table\] -- patient count for table
  by GP Practice.

### Database Routines

**db_routines**

List of all stored procedures and functions within the database. Use for
build and admin.

- sc -- routine schema

- routine_name -- routine name

- object_id -- id, as defined by server

- type -- routine type (P = stored procedure, FN = function, TT = table
  type)

- create_date -- creation date

- create_time -- creation time

- modified_date -- last modification date

- modified_time -- last modification time

**\
**

# Lookup Tables & Information

### Age Bands

**lu_ageband**

Age banded by a selection age band standards.

- age -- patient age

- five_year -- five-year age bands (A:0-4 \~ W:110-114)

- five_year_term -- five-year age bands text term

- ten_year -- ten-year age bands (A:0-9 \~ L:110-119)

- ten_year_term -- ten-year age bands text term

- ons_a -- ONS A age bands (A:0-24 \~ D:65-119)

- ons_a_term -- ONS A age bands text term

- ons_b -- ONS B age bands (A:0-24 \~ E:75-119)

- ons_b_term -- ONS B age bands text term

- ons_c -- ONS C age bands (A:0-15 \~ I:85-119)

- ons_c_term -- ONS C age bands text term

- ons_d -- ONS D age bands (A:0-4 \~ R:85-119)

- ons_d_term -- ONS D age bands text term

- ons_e -- ONS E age bands (A:0-84 \~ F:105-119)

- ons_e_term -- ONS E age bands text term

- ons_f -- ONS F age bands (A:0-4 \~ S:90-119)

- ons_f_term -- ONS F age bands text term

- ons_g -- ONS G age bands (A:0-15 \~ C:65-119)

- ons_g_term -- ONS G age bands text term

- esp_1976 -- European Std Population 1976 (A:0-4 \~ R:85-111)

- esp_1976_term -- European Std Population 1976 text term

- esp_2013 -- European Std Population 2013 (A:0, B:1-4, C:5-9 \~
  U:95-111)

- esp_2013_term -- European Std Population 2013 text term

- eth_band -- ethnicity report bands (A:0-4 \~ E:65-119)

- eth_band_term -- ethnicity report band text term

- profile_a -- population profiling a bands (A:16-18 \~ J:85-119)

- profile_a_term -- population profiling a bands text term

- profile_b -- population profiling b bands (A:0-4 \~ K:85-119)

- profile_b_term -- population profiling b bands text term

- ceg_piqi -- practice improvement quality indicators age bands (A:0-17
  \~ D:65-119)

- ceg_piqi_term -- practice improvement quality indicators age bands
  text term

**lu_ageband_key**

- age_std -- age banding standard

- band -- banding letter used with the age band standard

- term -- age band text term

### Indices of Multiple Deprivation (IMD)

**lu_deprivation**

Lower Super Output Area (LSOA) defined in 2011 within northeast London
with related Indices of Multiple Deprivation (IMD) based on 2015 and
2019 data. Quintiles (1 as most deprived) calculated within Local
Authority, Integrated Care Partnership, east London region and
nationally.

- LSOA_code_2011 -- ONS code (e-code) for LSOA 2011

- LSOA_name_2011 -- LSOA 2011 name (Local Authority name & identifier)

- IMD_2015 -- IMD score from 2015 IoD data

- IMD_2019 -- IMD score from 2019 IoD data

- LA_code_2019 -- ONS code (e-code) for local authority

- LA_name_2019 -- Local Authority name

- LA_id -- Local Authority identifier (CL, HK, NH, TH, WF, BD, HV, RB).

  - CL = City of London

  - HK = Hackney

  - NH = Newham

  - TH = Tower Hamlets

  - WF = Waltham Forest

  - BD = Barking & Dagenham

  - HV = Havering

  - RB = Redbridge

- LA_quintile_2015 -- IMD_2015 quintile within Local Authority

- LA_quintile_2019 -- IMD_2019 quintile within Local Authority

- ICP_id -- Integrated Care Partnership identifier (CH, BHR, TNW)

  - CH = City & Hackney

  - BHR = Barking & Dagenham, Havering & Redbridge

  - TNW = Tower Hamlets, Newham, & Waltham Forest

- ICP_quintile_2015 -- IMD_2015 quintile within Integrated Care
  Partnership

- ICP_quintile_2019 -- IMD_2019 quintile within Integrated Care
  Partnership

- EL_id -- east London region identifier (IEL, OEL)

  - IEL = Inner East London (CH, NH, TH)

  - OEL = Outer East London (WF, BD, HV, RB)

- EL_quintile_2019 -- IMD_2019 quintile within east London region

- NEL_quintile_2019 -- IMD_2019 quintile within northeast London

- National_quintile_2019 -- IMD_2019 quintile within England & Wales

### Lower Super Output Area (LSOA)

**lu_lsoa**

Lower Super Output Area (LSOA) defined in 2011 within England and Wales
with associated local authorities.

- LSOA_code_2011 -- ONS code (e-code) for LSOA 2011

- LSOA_name_2011 -- LSOA 2011 name (Local Authority name & identifier)

- LA_code_2019 -- ONS code (e-code) for local authority

- LA_name_2019 -- Local Authority name

**lu_lsoa2021**

Lower Super Output Area (LSOA) defined in 2021 within England and Wales
with associated LSOA 2011, LAD 2022 + LAD 2019 (Local Authority), and
IMD score 2019

- id -- table id

- lsoa2021_code -- ONS (e-code) for LSOA 2021

- lsoa2021_name - LSOA 2021 name (Local Authority name & identifier)

- changed -- relationship indicator for LSOA2011 -- LSOA2021

  - U = unchanged

  - S = split

  - M = merged

  - X = fragmented

<!-- -->

- lsoa2011_code -- ONS code (e-code) for LSOA 2011

- lsoa2011_name -- LSOA 2011 name (Local Authority name & identifier)

- lad2022_code - ONS code (e-code) 2022 for local authority

- lad2022_name - Local Authority name 2022

- lad2022_name_wales - Local Authority name 2022 (Welsh Language)

- lad2019_code -- ONS code (e-code) 2019 for local authority

- lad2019_name -- Local Authority name 2019

- imd2019_score -- Indices of Multiple Deprivation score calculated by
  ONS

- imd2019_quintile - Indices of Multiple Deprivation quintile calculated
  for England

For more information, see the ONS Open Geography Portal
(<https://geoportal.statistics.gov.uk>).

### Ethnicity

**lu_ethnicity**

- id -- row identifier

- code -- code (SNOMED, Read2, CTV3, EMIS Local)

- dbid -- database identifier for code

- scheme -- identifier for code scheme (SNOMED, Read2, CTV3, EMIS Local)

  - 71 = SNOMED

  - 1040444 = Read 2

  - 1130062 = CTV3

  - 1335379 = EMIS Local

- scheme_id --code scheme identifier text description eg. SN

- Term -- code text description

<!-- -->

- ceg_16 -- ethnicity categorisation using CEG 16+1

- ceg_16_term -- CEG ethnicity categories text description

- nhs_5 -- ethnicity categorisation using NHS 5+1

- nhs_5_term -- NHS 5+1 ethnicity categories text description

- nhs_16 -- ethnicity categorisation using NHS 16+1

- nhs_16_term -- NHS 16+1ethnicity categories text description

- sn_concept -- SNOMED concept id

- sn_description -- SNOMED description id

- sn_term -- SNOMED code term

**lu_ethnicity_sde**

- id -- row identifier

- sn_code -- SNOMED concept id

- sn_name -- SNOMED description id

- sn_description -- SNOMED code term

- sde_5 -- summary grouping of the 18+1 categories code value

- sde_5_name -- summary grouping of the 18+1 categories text description

- sde_18 -- Self-Defined Ethnicity 18+1 code value

- sde_18_name - Self-Defined Ethnicity 18+1 text description

**lu_ethnicity_key**

- ethnic_std -- ethnicity standard

- Category -- category letter used with ethnicity standard

- Term -- category text term

### GP Practice

**lu_practice**

- area_id -- area identifier for GP Practice (CH, NH, TH, WF, BK, HV,
  RB). This equates to the former CCGs and current Place-Based
  Partnerships or Areas within the North East London ICB.
  <https://northeastlondon.icb.nhs.uk/>

  - CH = City & London

  - NH = Newham

  - TH = Tower Hamlets

  - WF = Waltham Forest

  - BK = Barking & Dagenham

  - HV = Havering

  - RB = Redbridge

<!-- -->

- area -- area name

- ods_code -- ODS (Organisation Data Service) identifier for the GP
  Practice. <https://odsportal.digital.nhs.uk/>

- practice_name -- GP Practice name, as defined for CEG reporting. This
  may differ from the name on ODS records.

- listsize -- currently registered patient count for practice at the run
  date

- status -- activity status for the practice at the run date (active,
  inactive)

- start_date -- date the practice opened

- end_date -- date the practice closed

- pcn_ods -- ODS identifier for the Primary Care Network (PCN)
  associated with the practice

- pcn_name -- name of associated PCN

- clinical_system -- clinical data system used by the practice (EMIS,
  SystmOne)

- uprn -- Unique Property Reference Number (UPRN) identifier for the
  address of the practice. <https://uprn.uk/>

### Smoking

**lu_smoking**

- id -- row identifier

- code -- code (SNOMED, Read2, CTV3, EMIS Local)

- scheme -- identifier for code scheme (SNOMED, Read2, CTV3, EMIS Local)

  - 71 = SNOMED

  - 1040444 = Read 2

  - 1130062 = CTV3

  - 1335379 = EMIS Local

- name -- code text description

- ndasmok_cod -- code inclusion in National Diabetes Audit (NDA) code
  cluster (NDASMOK_COD)

- smok_cod -- code inclusion in Quality Outcomes Framework (QOF) code
  cluster (SMOK_COD, NULL)

- smok_status_qof -- Quality Outcomes Framework (QOF) code cluster
  associated with code (LSMOK_COD, EXSMOK_COD, NSMOK_COD, NULL)

  - LSMOK_COD = Smoker

  - EXSMOK_COD = Exsmoker

  - NSMOK = Never Smoked

- smok_status -- smoking status based on code term and/or QOF code
  cluster (CSMOK, NONSMOK, EXSMOK, NSMOK, UNKNOWN)

  - CSMOK = Current Smoker

  - NONSMOK = Current Non-Smoker

  - EXSMOK = Exsmoker

  - NSMOK = Never Smoked

  - UNKNOWN = smoking status cannot be defined

- dbid -- database identifier for code

- sn_dbid -- database identifier for SNOMED code associated with code

**lu_smoking_key**

- Id -- numeric identifier to smoking status

- smok_status -- smoking status

- name -- name term for smoking status

**\
**

# CORE

**CORE**

*Regular registration with a start date prior to the run date and an end
date NULL or after the run date, at a currently active GP Practice,
excluding patients with Date of Death \>= run date or with a record
indicating patient has died, or identifiable*[^1] *by patient's name as
a Dummy/Test patient, or aged \>= 120 years.*

The details for all patients registered with a NEL GP Practice on the
run date.

- relrun_date -- relative run date for the database build

- person_id -- identifier of person across multiple NHS organisations.
  Analogous to NHS Number.

- patient_id -- identifier of patient at a practice. Analogous to EMIS
  number.

- age -- age in years of patient on the run date

- sex -- sex (Female, Male, Other, Unknown) for patient

- ethnicity_code -- latest ethnicity SNOMED concept id.

- ceg_16 -- CEG 16+1 ethnic categorisation, based on ethnicity_code

- nhs_5 -- NHS 5+1 ethnic categorisation, based on ethnicity_code

- area_id -- area id for GP Practice (CH, NH, TH, WF, BK, HV, RB).

- ods_code -- ODS (Organisation Data Service) identifier for the GP
  Practice.

- practice_name -- GP Practice name, as defined for CEG reporting. This
  may differ from the name on ODS records.

- reg_date -- calculated registration date for patient at practice

- lsoa_2011 -- LSOA (Lower Super Output Area) for 2011 relating to the
  patient's identified current address.

- pt_area_id -- area_id based on patient's identified current address.
  NULL means the patient lives outside the North East London ICB area.

Because of the difficulties identifying some registrations, there are
some persons (person_id) that appear as multiple patients (patient_id)
at different practices. This may be due to patients moving practice;
errors in the registration data held by a practice; or a patient
deliberately registering and receiving healthcare with multiple
practices. It is not possible to better define or clean the data. For
most analyses, we recommend using patient_id.

## CORE Views

Views are virtual tables within a SQL database that provide a specified
subset of the actual data. These Views appear as standard tables within
MS Access and can be linked for use in queries in the same way. A series
of Views are provided that filter the CORE table to each specific area.

### CORE Area -- Registration

View based on area_id, which is defined by the location of the
registered GP Practice.

**CORE_BK**

**CORE_CH**

**CORE_HV**

**CORE_NH**

**CORE_RB**

**CORE_TH**

**CORE_WF**

**CORE Area -- Residency**

*View based on pt_area_id, which is defined by patient's identified
current address. These are the patients actually resident within the
borough.*

**CORE_BK_pt**

**CORE_CH_pt**

**CORE_HV_pt**

**CORE_NH_pt**

**CORE_RB_pt**

**CORE_TH_pt**

**CORE_WF_pt**

**\
**

# Registers

The register tables contain all patients with a specified diagnosis or
long term condition. The business rules syntax used to create the table
is provided with cluster_id(s) and date ranges.

Each table has the following fields:

- label -- descriptive label of the table contents. Be 'diabetes'

- area_id - area id for GP Practice

- ods_code - ODS (Organisation Data Service) identifier for the GP
  Practice.

- person_id -- identifier of person

- patient_id -- identifier of patient at a practice

Additional fields specific to the table are described below.

[]{.indexref entry="Anxiety"}**Anxiety**

**anxiety**

*Anxiety code (ANX_CEG) recorded \>= last 24 months.*

- latest \_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

Anxiety covers a range of Common Mental Health disorders, including

- Generalised Anxiety and Panic Attacks

- Anxiety associated with specific behaviours or situations

- Phobias

- Obsessive-Compulsive behaviour (OCD)

- Post-Trauma Stress (PSTD)

- Occupation-related Stress

### []{.indexref entry="Asthma"}Asthma 

**asthma**

*Asthma code (AST_COD) excluding patients with a more recent resolved
code (ASTRES_COD), and include Asthma Treatment meds code (ASTTRT_COD)
recorded \>= last 12 months. (QOF)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Atrial Fibrillation (AF)"}Atrial Fibrillation (AF) 

**atrial_fibrillation**

*Atrial Fibrillation code (AFIB_COD) excluding patients with a more
recent resolved code (AFIBRES_COD)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Autism"}Autism

**autism**

*Autism code (AUTISM_COD)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Cancer"}Cancer

**cancer**

Cancer code (CAN_COD) recorded \>= 2003-04-01

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Chronic Heart Disease (CHD)"}Chronic Heart Disease (CHD)

**chd**

*CHD code (CHD_COD)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Chronic Kidney Disease (CKD)"}Chronic Kidney Disease (CKD)

**ckd**

Aged \>= 18 years, and CKD code (CKD_COD) excluding patients with a more
recent resolved code (CKDRES_COD) or a more recent CKD 1 or 2 code
(CKD1AND2_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Chronic Obstructive Pulmonary Disease (COPD)"}Chronic Obstructive Pulmonary Disease (COPD)

**copd**

COPD code (COPD_COD) excluding patients with a more recent resolved code
(COPDRES_COD), and where patients have a previous resolved code
(COPDRES_COD), COPD code (COPD_COD) after the latest resolved code
(COPDRES_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Dementia"}Dementia

**dementia**

*Dementia code (DEM_COD)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Depression"}Depression

**depression**

Aged \>= 18 years, and Depression code (DEPR_COD) recorded \>=
2006-04-01 excluding patients with a more recent resolved code
(DEPRES_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

- latest_date -- latest, ie diagnosis, date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### []{.indexref entry="Diabetes Mellitus (DM)"}Diabetes Mellitus (DM)

**diabetes**

Aged \>= 18 years, and Diabetes code (DM_COD) excluding patients with a
more recent resolved code (DMRES_COD). Selecting most recent Diabetes
Type code (DMTYPE1_COD, DMTYPE2_COD) to define diabetes type.

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

- dm_type - diabetes type (TYPE_1 or TYPE_2) for each patient.

### []{.indexref entry="Eating Disorder"}Eating Disorder

**eating_disorder**

Eating disorder code (EATINGDIS_CEG) recorded \>= last 24 months

- latest \_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### []{.indexref entry="Epilepsy"}Epilepsy

**epilepsy**

Epilepsy code (EPIL_COD) excluding patients with a more recent resolved
code (EPILRES_COD), and include Epilepsy Drug meds code (EPILDRUG_COD)
recorded \>= last 6 months

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Familial Hypercholesteremia (FH)"}Familial Hypercholesteremia (FH)

**f_hypercholesterolemia**

Familial Hypercholestelemia code (FHYP_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Gestational Diabetes"}Gestational Diabetes

**gestational_diabetes**

Gestational diabetes code (GESTDIAB_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Heart Failure (HF)"}Heart Failure (HF)

**heart_failure**

Heart failure code (HF_COD) excluding patients with a more recent
resolved code (HFRES_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### []{.indexref entry="Hepatitis B"}Hepatitis B

**hepatitis_b**

*Hepatitis B code (HBV_CEG)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

- latest_date -- latest, ie diagnosis, date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### []{.indexref entry="Hepatitis C"}Hepatitis C

**hepatitis_c**

*Hepatitis C code (HCV_CEG)*

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

- latest_date -- latest, ie diagnosis, date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### []{.indexref entry="Human Immunodeficiency Virus (HIV)"}Human Immunodeficiency Virus (HIV)

**hiv**

HIV code (HIV_CEG)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- 

### Hypertension (HT)[]{.indexref entry="Hypertension (HT)"}

**hypertension**

Hypertension (HYP_COD) excluding patients with a more recent resolved
code (HYPRES_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Learning Disabilities (LD)[]{.indexref entry="Learning Disabilities (LD)"}

**learning_disabilities**

Learning Disabilities code (LD_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Motor Neurone Disease (MND)[]{.indexref entry="Motor Neurone Disease (MND)"}

**motor_neurone_disease**

Motor Neurone Disease code (MND_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Multiple Sclerosis (MS)[]{.indexref entry="Multiple Sclerosis (MS)"}

**multiple_sclerosis**

Multiple Sclerosis code (MS_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Non-Diabetic Hyperglycaemia (NDH)[]{.indexref entry="Non-Diabetic Hyperglycaemia (NDH)"}

**non_dm_hyperglycaemia**

Aged \>= 18 years, and Non-Diabetic Hyperglycaemia code (NDH_COD) or IGT
code (IGT_COD) or Pre-Diabetes code (PRD_COD) excluding patients with a
Diabetes code (DM_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Obesity[]{.indexref entry="Obesity"}

**obesity**

Aged \>= 18 years, and BMI Value code (BMIVAL_COD) \>=30 recorded \>=
last 12 months, or Non-Value BMI Indicating \>= 30 code (BMI30_COD)
recorded \>= last 12 months

- latest12m_date -- latest date of code for register in the last 12
  months

- latest12m_code -- SNOMED concept id for latest code in the last 12
  months

- latest12m_name -- code term for latest code in the last 12 months

- bmi30plus_latest12m_date -- latest date of code for register in the
  last 12 months with BMI \>=30

- bmi30plus_latest12m_code -- SNOMED concept id for latest code in the
  last 12 months with BMI \>=30

- bmi30plus_latest12m_name -- code term for latest code in the last 12
  months BMI \>=30

### Osteoporosis[]{.indexref entry="Osteoporosis"}

**osteoporosis**

Osteoporosis code (OSTEO_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Palliative Care[]{.indexref entry="Palliative Care"}

**palliative_care**

Palliative Care code (PALCARE_COD) excluding patients with a more recent
not indicated code (PALCARENI_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Parkinson's Disease[]{.indexref entry="Parkinson’s Disease"}

**parkinsons_disease**

Parkinson\'s Disease code (PD_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Peripheral Arterial Disease (PAD)[]{.indexref entry="Peripheral Arterial Disease (PAD)"}

**pad**

PAD code (PAD_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Personality Disorder[]{.indexref entry="Personality Disorder"}

**personality_disorder**

Personality Disorder code (PERSONALITYDIS_CEG)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Psoriasis[]{.indexref entry="Psoriasis"}

**psoriasis**

Psoriasis code (PSORIASIS_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Rheumatoid Arthritis[]{.indexref entry="Rheumatoid Arthritis"}

**rh_arthritis**

Aged \>= 16 years, and Rheumatoid Arthritis code (RARTH_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Severe Mental Illness (SMI)[]{.indexref entry="Severe Mental Illness (SMI)"}

**severe_mental_illness**

Mental Health code (MH_COD) excluding patients with a more recent
remission code (MHREM_COD), and include Lithium meds code (LIT_COD)
recorded \>= last 6 months excluding patients with a more recent Lithium
Stopped code (LITSTP_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

- lithium_latest_date -- latest, ie prescription, date of code for
  medication recorded \>= last 6 months

- lithium_latest_code -- SNOMED concept id for latest code medication
  recorded \>= last 6 months

- lithium_latest_name -- code term for latest code medication recorded
  \>= last 6 months

Mental Health excluding remission + Lithium (6m) excluding Lithium
Stopped

MH includes both schizophrenia and bipolar disorder and anyone on
lithium who is not also coded having these conditions.

### Sexually Transmitted Infection (STI)[]{.indexref entry="Sexually Transmitted Infection (STI)"}

**sti**

Sexually Transmitted Infection code (STI_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Sickle Cell Disease (SCD)[]{.indexref entry="Sickle Cell Disease (SCD)"}

**sickle_cell**

Sickle Cell code (SICKLE_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

### Stroke or Transient Ischaemia Attack (TIA)[]{.indexref entry="Stroke or Transient Ischaemia Attack (TIA)"}

**stroke_tia**

Stroke code (STRK_COD) or TIA code (TIA_COD)

- earliest_date -- earliest, ie diagnosis, date of code for register

- earliest_code -- SNOMED concept id for earliest code

- earliest_name -- code term for earliest code

# Measures

### Blood related

**measures_blood**

HbA1c code (IFCCHBAM_COD), Cholesterol[]{.indexref entry="Cholesterol"}
code (CHOL2_COD), Fasting Blood Glucose[]{.indexref
entry="Fasting Blood Glucose"} code (FASPLASGLUC_COD), eGFR[]{.indexref
entry="eGFR"} code (EGFR_COD), Creatine[]{.indexref entry="Creatine"}
code (CRE_COD), Liver Function Test[]{.indexref
entry="Liver Function Test"} code (LFT_COD)

- hba1c_latest_date -- latest HbA1c IFCC date of code for measure

- hba1c_latest_code -- SNOMED concept id for latest HbA1c IFCC code

- hba1c_latest_name -- code term for latest HbA1c IFCC code

- hba1c_latest_value -- latest HbA1c IFCC value recorded

- chol_latest_date -- latest Cholesterol date of code for measure

- chol_latest_code -- SNOMED concept id for latest Cholesterol code

- chol_latest_name -- code term for latest Cholesterol code

- chol_latest_value -- latest Cholesterol value recorded

- fbg_latest_date -- latest fasting blood glucose date of code for
  measure

- fbg_latest_code -- SNOMED concept id for latest fasting blood glucose
  code

- fbg_latest_name -- code term for latest fasting blood glucose code

- fbg_latest_value -- latest fasting blood glucose value recorded

- egfr_latest_date -- latest egfr date of code for measure

- egfr_latest_code -- SNOMED concept id for latest egfr code

- egfr_latest_name -- code term for latest egfr code

- egfr_latest_value -- latest egfr value recorded

- creat_latest_date -- latest creatinine date of code for measure

- creat_latest_code -- SNOMED concept id for latest creatinine code

- creat_latest_name -- code term for latest creatinine code

- creat_latest_value -- latest creatinine value recorded

- lft_latest_date -- latest liver function test date of code for measure

- lft_latest_code -- SNOMED concept id for latest liver function test
  code

- lft_latest_name -- code term for latest liver function test code

- lft_latest_value -- latest liver function test value recorded

### Body related

**measures_body**

BMI[]{.indexref entry="BMI"} Value code (BMIVAL_COD)

- bmi_latest_date -- latest BMI date of code for measure

- bmi_latest_code -- SNOMED concept id for latest BMI code

- bmi_latest_name -- code term for latest BMI code

- bmi_latest_value -- latest BMI value recorded

### Heart related

**measures_heart**

Blood Pressure[]{.indexref entry="Blood Pressure"} code (BP_COD), Pulse
Rate[]{.indexref entry="Pulse Rate"} code (PLSRATE_COD)

- bp_latest_date -- latest Blood Pressure date (with values) for measure

- bpsys_latest_code -- SNOMED concept id for latest Systolic Blood
  Pressure code

- bpsys_latest_name -- code term for latest Systolic Blood Pressure
  measure

- bpsys_latest_value -- latest Systolic Blood Pressure value recorded

- bpdia_latest_code -- SNOMED concept id for latest Diastolic Blood
  Pressure code

- bpdia_latest_name -- code term for Diastolic Blood Pressure measure

- bpdia_latest_value -- latest Diastolic Blood Pressure value recorded

- bpparent_latest_code -- SNOMED concept id for latest parent Blood
  Pressure code

- bpparent_latest_name -- code term for parent Blood Pressure measure

- match_algorithm -- number code of the algorithm used for Blood
  Pressure match

- pulserate_latest_date -- latest pulse rate date of code for measure

- pulserate_latest_code -- SNOMED concept id for latest pulse rate code

- pulserate_latest_name -- code term for latest pulse rate measure

- pulserate_latest_value -- latest pulse rate value recorded

Further explanation of blood pressure data in the Data Analysis and
Information section.

### Lung related 

**measures_lung**

FEV1/FVC[]{.indexref entry="FEV1/FVC"} code (FEV1FVC_COD), MRC
Breathlessness[]{.indexref entry="MRC Breathlessness"} Score code
(MRC_COD)

- fev1fvc_latest_date -- latest FEV1/FVC date of code for measure

- fev1fvc_latest_code -- SNOMED concept id for latest FEV1/FVC code

- fev1fvc_latest_name -- code term for latest FEV1/FVC measure

- fev1fvc_latest_value -- latest FEV1/FVC value recorded

- mrc_latest_date -- latest MRC date of code for measure

- mrc_latest_code -- SNOMED concept id for latest MRC code

- mrc_latest_name -- code term for latest MRC measure

- mrc_latest_value -- latest MRC value recorded

### Risk related

**measures_risk**

CHADSVASC[]{.indexref entry="CHADSVASC"} code (CHADVASC_COD),
QRISK[]{.indexref entry="QRISK"} code (QRISK2AND3SCORE_COD), Clinical
Frailty[]{.indexref entry="Clinical Frailty"} Score code
(CLINFRAILSCR_COD), Electronic Frailty Index[]{.indexref
entry="Electronic Frailty Index"} code (FRAILEFI_CEG), Frailty
Status[]{.indexref entry="Frailty Status"} code (MILDFRAIL_COD,
MODFRAIL_COD, SEVFRAIL_COD), QDiabetes[]{.indexref entry="QDiabetes"}
code (QDIABETES_CEG)

- chadsvasc_latest_date -- latest CHADS VASC date of code for measure

- chadsvasc_latest_code -- SNOMED concept id for latest CHADS VASC code

- chadsvasc_latest_name -- code term for latest CHADS VASC measure

- chadsvasc_latest_value -- latest CHADS VASC value recorded

- qrisk_latest_date -- last Qrisk date of code for measure

- qrisk_latest_code -- SNOMED concept id for latest Qrisk code

- qrisk_latest_name -- code term for latest Qrisk measure

- qrisk_latest_value -- latest Qrisk value recorded

- frailty_cfs_latest_date -- latest Clinical Frailty Score date of code
  for measure

- frailty_cfs_latest_code -- SNOMED concept id for latest Clinical
  Frailty Score code

- frailty_cfs_latest_name -- code term for latest Clinical Frailty Score
  measure

- frailty_cfs_latest_value -- latest Clinical Frailty Score value
  recorded

- frailty_efi_latest_date -- latest Electronic Frailty Index date of
  code for measure

- frailty_efi_latest_code -- SNOMED concept id for latest Electronic
  Frailty Index code

- frailty_efi_latest_name -- code term for latest Electronic Frailty
  Index measure

- frailty_efi_latest_value -- latest Electronic Frailty Index value
  recorded

- frailty_status_latest_date -- latest Frailty Status date of code for
  measure

- frailty_status_latest_code -- SNOMED concept id for latest Frailty
  Status code

- frailty_status_latest_name -- code term for latest Frailty Status
  measure

- frailty_status -- descriptor of frailty associated with
  frailty_status_latest_name using Rockwood Frailty Scale terms

- qdiabetes_latest_date -- latest QDiabetes value date of code for
  meaure

- qdiabetes_latest_code -- SNOMED concept id for latest QDiabetes code

- qdiabetes_latest_name -- code term for latest QDiabetes measure

- qdiabetes_latest_value -- latest QDiabetes value recorded

The frailty_status column is a simpler frailty classifier column to use.
It takes recorded code terms as registered and converts them into their
equivalent term according to the Rockwood Frailty Scale. Those are: very
fit, well, managing well, vulnerable, mildly frail, Moderately Frail,
Severely Frail, Very Severely Frail, Terminally Ill.

# Prescriptions

### **Antidepressants**[]{.indexref entry="Antidepressants"}

prescribed_antidepressants

*Anti-depressant medication (BNF 0403) excluding Amitriptyline
hydrochloride (BNF 0403010B0) recorded \>=last 6 months, selecting
latest Repeat prescription or, where no Repeat prescription is found,
latest Acute prescription. With earliest date of prescription course,
prescription type and count of prescriptions within the course.*

- latest6m_date -- latest, ie prescription, date of code recorded \>=
  last 6 months

- latest6m_code -- SNOMED concept id for latest prescription \>= last 6
  months

- latest6m_name -- code term for latest prescription \>= last 6 months

- prescription_type -- type of prescription eg. repeat/acute

- prescription_count -- number of prescriptions within the prescription
  course

- prescription_earliest_date -- earliest, date of prescription course

- bnf_code -- British National Formulary code

### Statins[]{.indexref entry="Statins"}

prescribed_statins

Statins meds code (STAT_COD) recorded \>=last 6 months, and earliest
recorded

- latest6m_date -- latest, ie prescription, date of code for statin
  recorded \>= last 6 months

- latest6m_code -- SNOMED concept id for latest statin prescription \>=
  last 6 months

- latest6m_name -- code term for latest statin prescription \>= last 6
  months

- earliest_date -- earliest, ie prescription, date of code for statin
  recorded

- earliest_code -- SNOMED concept id for earliest statin prescription

- earliest_name -- code term for earliest statin prescription

# Vaccinations

### Covid Immunisation[]{.indexref entry="Covid Immunisation"}

**vaccination_covid**

Covid Vaccination code (C19VACC_CEG) or Covid Vaccination meds code
(C19VACCMEDS_CEG)

- latest_date -- latest, ie immunisation, date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for earliest code

- code_type -- indicates if code is an admin (a) or medication (m) code

- vacc_num -- estimated number of covid vaccinations received

# NHS Health Checks

### NHS Health Checks done (NHS HC)[]{.indexref entry="NHS Health Checks done (NHS HC)"}

**nhs_healthcheck**

NHS Health Check code (NHSHC_CEG) recorded \>= last 5 years. Selecting
earliest date from LTC table (hypertension, diabetes,
atrial_fibrillation, ckd, stroke_tia, heart_failure, pad,
f_hypercholesterolemia, prescribed_statins) as inelig date and table.

- earliest5y_date -- earliest, ie health check, date of code for
  register in the last 5 years

- earliest5y_code -- SNOMED concept id for earliest code

- earliest5y_name -- code term for earliest code

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- inelig_earliest_date -- earliest date a patient became ineligible for
  a NHS health check

- inelig_table -- name/reason of ineligibility

- valid_nhshc -- Y/N column of nhshs validity.

### NHS Health Checks declined[]{.indexref entry="NHS Health Checks declined"}

**nhs_healthcheck_declined**

NHS Health Check Declined code (NHSHCDEC_CEG) recorded \>= last 5 years

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### NHS Health Checks invited[]{.indexref entry="NHS Health Checks invited"}

**nhs_healthcheck_invite**

NHS Health Check Invite code (NHSHCINV_CEG) recorded \>= last 5 years.
Selecting earliest date from LTC table (hypertension, diabetes,
atrial_fibrillation, ckd, stroke_tia, heart_failure, pad,
f_hypercholesterolemia, prescribed_statins) as inelig date and table

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- inelig_earliest_date -- earliest date a patient became ineligible for
  an NHS health check

- inelig_table -- name/reason of ineligibility

- valid_nhshc -- Y/N column of nhshs validity.

### NHS Health Checks eligibility[]{.indexref entry="NHS Health Checks eligibility"}

**nhs_healthcheck_elig2023**

All 2023 CORE registers aged \>= 40, excluding patients with
hypertension, diabetes, ckd, heart failure, pad, familial
hypercholestrolemia, stroke tia, chd, arterial fibrillation and statin
prescription.

# Screening & Checks

### Bowel Cancer Screening done[]{.indexref entry="Bowel Cancer Screening done"}

**screen_bowel_cancer**

Bowel Cancer Screening evidenced results (COLCANSCREV_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- age_at_event -- age of patient when screening took place

### Bowel Cancer Screening declined[]{.indexref entry="Bowel Cancer Screening declined"}

**screen_bowel_cancer_declined**

Bowel Cancer Screening Declined code (COLCANSCRDEC_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Breast Cancer Screening done[]{.indexref entry="Breast Cancer Screening done"}

**screen_breast_cancer**

Female, and Breast Cancer Screening code (BRCANSCR_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- age_at_event -- age of patient when screening took place

### Breast Cancer Screening declined[]{.indexref entry="Breast Cancer Screening declined"}

**screen_breast_cancer_declined**

Female, and Breast Cancer Screening Declined code (BRCANSCRDEC_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Cervical Cancer Screening done[]{.indexref entry="Cervical Cancer Screening done"}

**screen_cervical_cancer**

Female, and Cervical Cancer Screening code (SMEAR_COD). With exclusion
as No Cervix code (NOCX_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- age_at_event -- age of patient when screening took place

- exclusion_earliest_date -- latest date of code for exclusion

- exclusion_earliest_code -- SNOMED concept id for latest exclusion code

- exclusion_earliest_name -- code term for latest code

### Cervical Cancer Screening declined[]{.indexref entry="Cervical Cancer Screening declined"}

**screen_cervical_cancer_declined**

Female, and Cervical Cancer Screening Declined code (CSDEC_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Diabetic Retinal Screening done[]{.indexref entry="Diabetic Retinal Screening done"}

**screen_diabetic_retinal**

Diabetic Retinal Screening code (RET_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for code

- latest_name -- code term for latest code

### Diabetic Retinal Screening excepted[]{.indexref entry="Diabetic Retinal Screening excepted"}

**screen_diabetic_retinal_excepted**

Diabetic Retinal Screening Excepted code (RETEXEC_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Pulse Check done[]{.indexref entry="Pulse Check done"}

**screen_pulse_check**

Pulse Check code (PULRHYTH_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- pulse_type -- standardised descriptor of pulse type associated with
  latest_name (regular, irregular, irregularly irregular, unknown)

The pulse_type column can be used when categorising pulse types or
looking at a specific category. Standardised pulse type descriptors in
pulse_type are: regular, irregular and irregularly irregular. Code names
such as "pulse rhythm" or "pulse rhythm finding" are defined as unknown.

Pulse Checks are done opportunistically, which means there is no
declined coding as with other screening services.

# Smoking, Alcohol & Drug Use

### Smoking[]{.indexref entry="Smoking"}

**smoking**

Smoking codes (SMOK_COD and NDASMOK_COD)

- latest_date -- latest code date

- latest_code -- latest code

- latest_name -- latest code name

- smoking_status -- provides smoking status according to latest code
  (from either SMOK_COD or NDASMOK_COD)

- qof_latest_date -- latest QOF code date

- qof_latest_code -- latest QOF code

- qof_latest_name -- latest QOF code name

- qof_smoking_status -- latest smoking status according to latest QOF
  code (SMOK_CODE). This column can be used when looking at smoking
  status by QOF definition only.

The QOF only columns have codes from SMOK_COD only. Hence, there will be
NULLs in those columns. If you are interested in all current smoking
codes, we suggest the use of *smoking_status* column. You should use
*qof_smoking_status* when interested in QOF definitions only.

### Alcohol[]{.indexref entry="Alcohol"} 

**alcohol**

Alcohol Consumption code (ALC_COD), Alcohol Audit code (AUDIT_COD),
Alcohol Audit-C code (AUDITC_COD), Alcohol FAST code (FAST_COD), Alcohol
Advice code (ALCADV_COD), Alcohol Brief Intervention code
(ALCBRINT_COD), Alcohol Extend Intervention code (ALCEXINT_COD), Alcohol
Referral code (ALCREF_COD), Alcohol Intervention Declined code
(ALCINTDEC_COD)

- latest_date -- latest date of alcohol consumption code, including
  those without a value

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- consume_latest_date -- latest date of alcohol consumption code with a
  value

- consume_latest_code -- SNOMED concept id for latest code

- consume_latest_name -- code term for latest alcohol consumption code

- consume_latest_value -- latest alcohol consumption value recorded

- consume_latest_units -- unit of measure and period for
  consume_latest_value

- consume_latest_units_pw -- alcohol consumption standardised to per
  week. See Appendix 1: Alcohol Units Per Week

- audit_latest_date -- latest, alcohol audit, date of code for register

- audit_latest_code -- SNOMED concept id for latest code

- audit_latest_name -- code term for latest alcohol audit code

- audit_latest_value -- latest alcohol audit value recorded

- auditc_latest_date -- latest, alcohol audit-c, date of code for
  register

- auditc_latest_code -- SNOMED concept id for latest code

- auditc_latest_name -- code term for latest alcohol audit-c code

- auditc_latest_value -- latest alcohol audit-c value recorded

- fast_latest_date -- latest, alcohol FAST, date of code for register

- fast_latest_code -- SNOMED concept id for latest code

- fast_latest_name -- code term for latest alcohol FAST code

- fast_latest_value -- latest alcohol FAST value recorded

- advice_latest_date -- latest, Alcohol Advice, date of code for
  register

- advice_latest_code -- SNOMED concept id for latest code

- advice_latest_name -- code term for latest Alcohol Advice code

- briefint_latest_date -- latest, Alcohol Brief Intervention, date of
  code for register

- briefint_latest_code -- SNOMED concept id for latest code

- briefint_latest_name -- code term for latest Alcohol Brief
  Intervention code

- extendedint_latest_date -- latest, Alcohol Extend Intervention, date
  of code for register

- extendedint_latest_code -- SNOMED concept id for latest code

- extendedint_latest_name -- code term for latest Alcohol Extend
  Intervention code

- referral_latest_date -- latest, Alcohol Referral code, date of code
  for register

- referral_latest_code -- SNOMED concept id for latest code

- referral_latest_name -- code term for latest Alcohol Referral code

- declinedint_latest_date -- atest, Alcohol Intervention Declined, date
  of code for register

- declinedint_latest_code -- SNOMED concept id for latest code

- declinedint_latest_name -- code term for latest Alcohol Intervention
  Declined code

### Substance Misuse[]{.indexref entry="Substance Misuse"}

**substance_misuse**

Illicit Substance Abuse code (ILLSUB_COD) excluding patients with a
latest Non-Substance Misuser code (NONILLSUM_CEG), Illegal Substance Use
Intervention code (ILLSUBINT_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

- int_latest_date -- latest date of code for intervention

- int_latest_code -- SNOMED concept id for latest intervention

- int_latest_name -- code term for latest intervention code

The PCD provided codeset for Illicit Substance Abuse (ILLSUB_COD)
includes codes for non-substance misuse. Patients with these codes as
their latest returned code are removed.

# Sexual Health

### LARC (Long-Acting Reversible Contraception)[]{.indexref entry="LARC (Long-Acting Reversible Contraception)"}

**larc**

IUCD Fitting code (IUCDFIT_CEG) or IUCD Removed code (IUCDREM_CEG) or
Implant Fitting code (IMPFIT_CEG) or Implant Removed code (IMPREM_CEG)

- iucdfit_latest_date -- latest date of code for IUCD fit code

- iucdfit_latest_code -- SNOMED concept id for latest IUCD fit

- iucdfit_latest_name -- code term for latest IUCD fit code

- iucdremoved_latest_date -- latest date of code for IUCD removed code

- iucdremoved_latest_code -- SNOMED concept id for latest IUCD removed
  register

- iucdremoved_latest_name -- code term for latest IUCD removed code

- implantfit_latest_date -- latest date of code for Implant fit code

- implantfit_latest_code -- SNOMED concept id for latest Implant fit
  register

- implantfit_latest_name -- code term for latest Implant fit code

- implantremoved_latest_date -- latest date of code for Implant Removed
  code

- implantremoved_latest_code -- SNOMED concept id for latest Implant
  Removed

- implantremoved_latest_name -- code term for latest Implant Removed
  code

# Lifestyle Status

### Homeless[]{.indexref entry="Homeless"}

**status_homeless**

Homelessness code (HOMELESS_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Housebound[]{.indexref entry="Housebound"}

**status_housebound**

Housebound code (HOUSEBOUND_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Household[]{.indexref entry="Household"}

**status_household**

Calculated using ASSIGN algorithm

- match_status_id -- id of ASSIGN processing outcome

- match_status -- ASSIGN processing outcome

  1.  Residency

  2.  Non-Residential Property

  3.  Imprecise Match

  4.  Multiple Address

  5.  No Match Data

  6.  Improbable

- property_id -- internal database id for property matched by ASSIGN

- patient_count -- count of patients found at the property_id

See ***Data Anaysis and Information: Household*** for more details.

### Carer[]{.indexref entry="Carer"}

**status_carer**

Carer code (ISACARER_COD) excluding patients with a more recent Not A
Carer code (NOTACARER_COD)

- latest_date -- latest date of code for register

- latest_code -- SNOMED concept id for latest code

- latest_name -- code term for latest code

### Interpreter needed[]{.indexref entry="Interpreter needed"}

**status_interpreter**

Requires interpreter codes (REQINTERPRETER_CEG, NOINTERPNEEDED_CEG),
requires spoken language interpreter codes (SPOKENLANGINTERP_CEG),
preferred language codes (SPOKENLANGINTERP_CEG), requires communication
support codes including deafblind, sign language, lip-speaker, speech to
text reporting and advocate codes (COMSSUPPORT_CEG)

- interpreter_latest_date -- latest date of code for interpreter needed
  register

- interpreter_latest_code -- SNOMED concept id for latest interpreter
  needed code

- interpreter_latest_name -- code term for latest interpreter needed
  code

- interpreter_lang_latest_date -- latest date of code for language
  interpreter register

- interpreter_lang_latest_code -- SNOMED concept id for latest language
  interpreter code

- interpreter_lang_latest_name -- code term for latest language
  Interpreter code

- preflang_latest_date -- latest date of code for preferred language
  register

- preflang_latest_code -- SNOMED concept id for latest preferred
  language code

- preflang_latest_name -- code term for latest preferred language code

- coms_support_latest_date -- code term for latest communication support
  code

- coms_support_latest_code -- SNOMED concept id for latest communication
  support code

- coms_support_latest_name -- code term for latest communication support
  code

# Data Analysis and Information

## Mental Health

Mental Health conditions can be difficult to identify within health
data. The conditions can be transitory or episodic, meaning coding does
not necessarily reflect the patient's current health. The experience and
treatment of a mental health issue is also individual to a patient,
meaning the presence of a code, particularly for Common Mental Health
Disorders, does not provide a clear indication of the severity of the
condition, the impact it has on the patient's life and wellbeing, or the
way the condition is being managed. Patients may also exhibit multiple
mental health problems, which a clinician may choose to code and treat
in different ways depending on perceived priorities or causations.
Finally, clinicians and patients may prefer to use or accept particular
diagnoses, which can affect the coding used in the patient's record.

Mental Health data is provided across a series of registers.

### Anxiety

The ***anxiety*** table includes codes associated with the Common Mental
Health Disorders, with the exclusion of Depression, as defined by NICE:

generalised anxiety disorder

panic disorder

obsessive-compulsive disorder (OCD)

post-traumatic stress disorder (PTSD)

social anxiety disorder

depression

Inclusion is for codes recorded in the last 24 months, as a reasonable
timeframe for ensuring patients are currently being managed, to some
level, for their condition.

### Depression

The ***depression*** table contains all patients who have been coded for
depression since 01/04/2006 (QOF definition). The latest code is
provided, as well as the earliest, so it is possible to filter for
patients who have been recently coded with depression eg in the last 12
or 24 months.

Depression codes, however, are not consistently or regularly re-entered
and there are many patients who appear to be receiving ongoing treatment
for depression, but who have no recent depression coding. Conversely,
the 'depression resolved' code is not consistently applied, so the
register will also include patients who are no longer be treated as
depressed.

### Antidepressants

The **prescribed_antidepressant** table contains all patients who have
been prescribed anti-depressant medication (BNF 04:03 excluding
amitriptyline) in the past six months. Amitriptyline is excluded as it
is not recommended for treating depression and is more commonly
prescribed for pain relief. Other drugs within this chapter may also be
prescribed for conditions other than depression, sometimes with
differing dosages:

  --------------------------------------------------------------------------
       BNF VTM   Medication        Depression       Other Conditions +
                                   dosage           dosage
  -------- ----- ----------------- ---------------- ------------------------
    403010 F0    Clomipramine      Depression       Phobic + OCD \>=10mg
                 hydrochloride     \>=10mg          

    403010 L0    Doxepin           Depression       Pruritus in eczema
                                   \>=75mg          3-12mg (cream)

    403010 N0    ﻿﻿﻿Imipramine        Depression       Childhood Bedwetting
                 hydrochloride     \>=75mg          25-75mg

    403010 X0    Trazodone         Depression       Anxiety 75-300mg
                 hydrochloride     \>=100mg         

    403020 K0    Moclobemide       Depression       Anxiety 300-600mg
                                   \>=150mg         

    403030 D0    Citalopram        Depression       Panic 10-40mg
                 hydrobromide      10-40mg          

    403030 Z0    Citalopram        Depression       Panic 40mg/1ml
                 hydrochloride     40mg/1ml         

    403030 X0    Escitalopram      Depression       Anxiety, OCD & Panic
                                   5-20mg           5-20mg

    403030 E0    Fluoxetine        Depression       Bulimia 40-60mg, OCD
                 hydrochloride     20-60mg          20-60mg, Menopause 20mg

    403030 L0    Fluvoxamine       Depression       OCD 50-300mg
                 maleate           50-300mg         

    403030 P0    Paroxetine        Depression       OCD 20-60mg, Panic
                 hydrochloride     20-50mg          10-60mg, Menopause 10mg

    403030 Q0    Sertraline        Depression       OCD 50-200mg, Panic,
                 hydrochloride     50-200mg         PTSD & Anxiety
                                                    25mg-200mg

    403040 Y0    Duloxetine        Depression 60mg  Anxiety 30-120mg, DM
                 hydrochloride                      Neuro 60-120mg, female
                                                    incontinence 20-40mg

    403040 W0    Venlafaxine       Depression       Anxiety 75-225mg, Panic
                                   \>=75mg          37.5mg-225mg, Menopause
                                                    37.5mg-75mg
  --------------------------------------------------------------------------

Patients may be instructed to take multiple tablets per day and may have
concurrent prescriptions for different strength medications. The
particular dosage shown in the latest6m_name field should only be taken
as a rough indicator of the medication dosage that has been advised for
the patient and whether they are being treated for a condition other
than depression.

The prescribed product shown in the latest6m_code and name is the latest
prescription within a prescription course for that medication and
dosage. That prescription course may be a Repeat course (allowing the
patient to re-order the prescription) or an Acute course (a one-off
prescription). The table provides the latest Repeat prescription or, if
no Repeat prescription has occurred in the last six months, the latest
Acute (one-off) prescription. This is shown in the prescription_type
column. The prescription_count gives the number of prescriptions that
have been made within the prescription course to date and the
prescription_earliest_date gives the date of the first prescription
within the course.

### Active Depression

The **prescribed_antidepressants** table can be joined to the
**depression table**, in order to identify patients with both a
depression code and a current anti-depressant medication. As described
above, there is no guarantee however that the patient isn't being
medicated for an alternative condition. Attention may want to be given,
therefore, to the type of prescription, how long the prescription has
been in place and to the dosage.

The **prescribed_antidepressants** table could also be cross-referenced
against the **anxiety** and **eating disorders** registers to further
identify patients that are possibly receiving the medication for these
conditions, rather than depression.

Patients with depression may also follow talking therapies rather than
take medication. It is advisable, therefore, to also include patients
without an anti-depressant prescription but with a recent depression
code.

### Eating Disorder

The ***eating_disorder*** register contains patients with mental health
conditions linked to beliefs about their weight or body shape, such as
Anorexia Nervosa, Bulimia and Binge Eating. These conditions are not
listed by NICE as CMHD.

The register does not include patients with Other Specified Feeding or
Eating Disorder (OSFED), whose condition is linked to other beliefs or
concerns, or patients with Avoidant/Restrictive Food Intake Disorder
(ARFID), who choose to avoid or limit their intake of certain foods. It
is expected that these patients will also have more general codes in
their records that will place them into the ***anxiety*** or
***severe_mental_illness*** registers.

### Severe Mental Illness

The ***severe_mental_illness*** register includes persistent long term
mental health conditions, such as schizophrenia and bipolar disorder. It
also includes anyone currently prescribed lithium.

### Personality Disorder

The ***personality_disorder*** register is a non-QOF register specific
to personality disorders. It uses codes that do not appear in the MH_COD
codeset used for *severe_mental_illness*. Patients may have been coded
however to appear in both tables.

## NHS Health Checks

NHS Health Checks are undertaken on patients who do not have a
pre-existing Long Term Condition and/or have not been prescribed
statins, as these patients will receive regular checkups within their
specific care pathway. On this basis, whilst the GP practice may have
carried out the activity, a NHS Health Check recorded for a patient that
had one or more of the conditions listed below on the date of the NHS
Health Check would not be considered valid for inclusion in the service
and payment.

The inelig_earliest_date provides the earliest date at which a patient
was diagnosed with a LTC or was prescribed statins and so become
ineligible for a NHS Health Check. The **inelig_table** provides the
table from which the inelig_earliest_date was derived. The valid_nhshc
field provides a Y/N definition of the Health Check validity, based on
the inelig_earliest_date compared to the NHS Health Check latest_date.

Conditions that define NHS Health Check ineligibility are:

hypertension, diabetes, ckd, heart failure, pad, familial
hypercholestrolemia, stroke tia, chd, arterial fibrillation and statin
prescription.

## Cancer Screening 

Cancer screening programmes exist for bowel, breast and cervical cancer
for patients in specified age ranges:

> Bowel: all patients aged 56y, 58y, 60y-74y.
>
> Breast: all female patients aged 50y-70y
>
> Cervical: all female patients aged 25y-64y

The cancer screening tables are created from CORE with no age
restriction or any other exclusions, except gender in breast cancer
screening and cervical screening. The age_at_event column shows the age
of the patient when the screening took place in order to assist
identification of patients screened within the national programme.

Although patients who have had a colectomy or mammectomy will not be
included in the respective screening programmes, the only nationally
defined exclusion codeset is for the cervical screening programme. This
covers patients with hysterectomies and similar interventions. The
exclusion columns in the **screen_cervical_cancer** table refer to the
earliest date for this codeset (NOCX_COD). These columns allow for
filtering patients that may not have been included in screening
programmes or for identifying interventions following a screening.

## Blood Pressure

In the Compass data, a blood pressure is represented by a combination of
up to 3 codes:

- The *parent*, or reading, code to indicate a Blood Pressure has been
  taken but with no attached value. This is often SN 163020007 (On
  examination - blood pressure reading (finding))

- A *systolic* code with a value and a link in the data to the parent
  code. This is often SN 72313002 (Systolic arterial pressure
  (observable entity))

- A *diastolic* code with a value and a link in the data to the parent
  code. This is often SN 1091811000000102 (Diastolic arterial pressure
  (observable entity))

Multiple blood pressures can be taken on the same day but, in theory,
every blood pressure reading should have all 3 of these codes, ensuring
the correct systolic and diastolic values can be matched up with
confidence. In practice, the data is not always so neat: systolic and
diastolic codes can exist without a parent code; or without a matching
value code; or without a value; and parent codes can sometimes link to
more than one systolic or diastolic code. Identifying blood pressures
requires, therefore, finding and matching systolic and diastolic records
using combinations of their parent record id, their date and their
database record id. This last element is used as a proxy for time within
a given day, as Compass does not contain the time of code entry onto the
clinical system.

The blood pressure codes are matched, therefore, using 4 algorithms:

1.  Systolic records with a value are matched to diastolic records with
    a value, using their common parent record id.

2.  Where algorithm 1 returns multiple diastolic records for a single
    systolic/parent record, the diastolic record with the nearest record
    id to the systolic record id is chosen

3.  Systolic records not matched by algorithms 1 & 2 are matched with
    the diastolic record on the same date, where there is only 1
    diastolic\* record for that date.

4.  Systolic records not matched by algorithms 1, 2 & 3 are ranked by
    date and record id and matched against the similarly ranked
    remaining diastolic records.

Matched records in which either the systolic or diastolic value is NULL
are removed and the remaining records are ranked by date and the
systolic record id to find the latest record.

The blood pressures in the **measures_heart** table are therefore the
blood pressures readings for which it is possible to define a
systolic/diastolic value. Readings with NULL and missing values have
been filtered out. No validation checks have been carried out though --
checks should still be undertaken to verify that the values are within
expected clinical ranges.

The **measures_heart** table contains bpparent_code and bpparent_name
fields for where a parent code was used in the match. The
match_algorithm column provides the number of the algorithm used for the
match, as shown above.

**Household**

The **status_household** table contains the residency for patients on
01/04/2024, as calculated using the ASSIGN algorithm developed by CEG in
collaboration with the Endeavour Health charity. ASSIGN is a
quality-assured and validated address-matching algorithm with a 98.6%
match rate (based on a population of 1.8million adults registered with a
GP in northeast London) and a high sensitivity and positive predictive
value \[1\]. For any provided address, ASSIGN allocates a UPRN from the
Ordnance Survey Great Britain property gazetteer database AddressBase
Premium. This UPRN is first pseudonymised and then converted into a
*property_id* which is unique solely within the database. The
*property_id* cannot be used therefore for linking with any external
data, but does provide a means to link patients into co-habiting
'households', size of which is shown in the *patient_count* column.

The *property_id* and *patient_count* information is only provided for
successful ASSIGN property matches. The *match_status_id* gives a
breakdown of ASSIGN outcome:

1.  Residency

2.  Non-Residential Property (ie the ASSIGN identified UPRN does not
    have residential classification (see below))

3.  Imprecise Match (ie ASSIGN could not precisely identify a property
    from the patient address details)

4.  Multiple Address (ie the address data shows the patient residing at
    more than 1 property)

5.  No Match Data (ie no address or ASSIGN result found for the patient)

6.  Improbable Household (ie over 10 patients identified as residing at
    the property (see below))

### Non-Residential Property

The AddressBase Premium provides information on each UPRN including a
use classification. Any property without a Residential or Unclassified
classification is excluded from the result. Unclassified properties are
included as these are very often new residential properties. Residential
covers all types of house, flats, caravans, house boats, sheltered
accommodation and HMOs, as well as properties simply classified as
'Residential' or 'Dwelling'. It does not include Residential
Institutions, such as nursing/care homes or halls of residency, nor
hotels and hostels. Some of these classifications may become available
in the future if validated.

### Improbable Household

A household is defined in our analyses as 'a group of residents living
at the same property at the same time'. From our analyses, we have
concluded that it is improbable that a household will consist of more
than 10 people. Where this is found in the data, it is more likely that
the patient's address data is incomplete, or the property is a hostel or
institution of some kind. These properties are therefore excluded from
the results.

1)  Harper, G., Stables, D., Simon, P., Ahmed, Z., Smith, K., Robson, J.
    and Dezateux, C. (2021) "Evaluation of the ASSIGN open-source
    deterministic address-matching algorithm for allocating Unique
    Property Reference Numbers to general practitioner-recorded patient
    addresses", *International Journal of Population Data Science*,
    6(1). doi: <https://doi.org/10.23889/ijpds.v6i1.1674>

# Appendix 1: Alcohol Units Per Week

Units per week calculated from an units value and multiplier, both
derived from latest_units text.

**Find units for value**

latest_units contains \'pint\' - units = value \* 2.3

(assume pint of 4% beer)

latest_units contains \'glass\' - units = value \* 2.3

(assume 175ml glass of medium strength wine)

latest_units contains \'bottle\' - units = value \* 10

otherwise - units = 1

**Find multiplier for value**

latest_code = SN 105542008 (Teetotaller) - multiplier = 0

latest_code = SN 1082641000000106 (Alcohol units per week) - multiplier
= 1

latest_code = SN 266917007 (Trivial drinker - \<1u/day) - multiplier = 1

(Units are sometimes given as \"/day\" but value \> 7. All instances of
code assumed to be for week)

latest_code = SN 442547005 (Alcohol units consumed on heaviest drinking
day) - multiplier = 1.5

(code provides no clear indication for weekly consumption. Estimate as
half again per week)

latest_units contains no indication of time period - multiplier = 1

(assume value is for week)

latest_units contains \'day\' or variation - multiplier = 7

latest_units contains \'week\' or variation - multiplier = 1

latest_units contains \'fortnight\' or variation - multiplier = 1/2

latest_units contains \'3 weeks\' or variation - multiplier = 1/3

latest_units contains \'month\' or variation - multiplier = 1/4

latest_units contains \'2 months\' or variation - multiplier =1/8

latest_units contains \'3 months or variation - multiplier = 1/13

latest_units contains \'4 months\' or variation - multiplier = 1/17

latest_units contains \'6 months\' or variation - multiplier = 1/26

latest_units contains \'year\' or variation - multiplier = 1/52

latest_units contains \'Never\' or variation - multiplier = 0

**latest_units_pw = latest_value \* units \* multiplier**

OR

if latest_units contains \'occassionally\' or variation -
**latest_units_pw = 0.55**

(Estimate consumption, whatever value will be below 1 unit per week)

# Appendix 2: Database Version Log

  --------------------------------------------------------------------------
  **Version 2024.1**         **10/06/2024**
  -------------------------- -----------------------------------------------
                             Database uploaded to ELDB server

  **Version 2024.2**         **17/06/2024**

  measures_heart             added table, with blood pressure and pulse
                             rate.

  db_routines                corrected name of routine_name (previously
                             table_name)

  nhs_healthcheck_elig2023   corrected name of table (previously
                             nhs_healthcheck_elig2024)

  nhs_healthcheck_elig2023   rerun table to ensure correct data is included

  **Version 2024.3**         **31/07/2024**

  lu_lsoa2021                added lookup table for LSOA 2021

  status_homeless            rebuilt table to fix error of patients included
                             with label of \'No longer homeless\'.

  lu_ethnicity_sde           added lookup table for Self Defined Ethnicity
                             (SDE) 5+1 and 18+1 ethnicity categories

  substance_misuse           updated label column to have one label
                             \'Substance Misuse\'

  **Version 2024.4**         **22/11/2024**

  screen_bowel_cancer        Updated bowel cancer screening codeset to Bowel
                             Cancer Screening evidenced results
                             (COLCANSCREV_COD)

  **Version 2024.5**         **23/01/2025**

  lu_ethnicity_sde           corrected sde_18 categorisation for
                             92491000000104 (African) and 92501000000105
                             (Other Black background)

  status_household           added table for linking patients into
                             households based on property_id
  --------------------------------------------------------------------------

# Document Version Log

  ----------------------------------------------------------------------------
  Date         Version   Information
  ------------ --------- -----------------------------------------------------
  13/06/2024   1         Document Created

  17/06/2024   2         

  31/07/2024   3         Added lu_ethnicity_sde

  22/11/2024   4         Updated screen_bowel_cancer

  23/01/2024   5         Added status_household and corrected sde_18
                         categorisation in lu_ethnicity_sde
  ----------------------------------------------------------------------------

[^1]: Names including the words "patient", "testing", "EMIS" etc, as
    well as names unlikely to be found in real life eg "Micky Mouse" or
    "Crisp Doritos".
