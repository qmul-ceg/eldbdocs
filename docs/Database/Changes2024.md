# Changes from ELDB 2024
## Data
All data has been rerun from 01/04/2025.
## Core
Updated to include the new ethnicity and IMD fields (see below)
LSOA has calculated from patient's postcode to ensure a precise definition for `lsoa2021`

- Removed column `ceg_16`  
- Removed column `nhs_5`  
- Added column `ethnic_5` - ethnicity 5+1 (2011) categorisation  
- Added column `ethnic_16` - ethnicity 16+1 categorisation  
- Added column `ethnic_18` - ethnicity 18+1 categorisation  
- Added column `ethnic_19` - ethnicity 19+1 categorisation
- Added column `pt_lad2023` - LAD ONS code (2023) based on patient's identified current address    
- Added column `imd2019` - Indices of Multiple Deprivation score calculated by ONS in 2019 (England only)
- Added column `imd2019_rank` - IMD rank by country calculated by ONS
- Added column `lsoa2021` - ONS (e-code) for LSOA 2021
## Database Info
- Added table  [`db_clusters`](../Data/Structure_Info.md#db_clusters-code-clusters-in-tables) - NHS and CEG code clusters used to build tables  
- Added table [`db_codeset_ceg`](../Data/Structure_Info.md#db_codeset_ceg-ceg-code-clusters) - CEG code clusters used in ELDB  
## Ethnicity
Updated ethnicity tables to improve consistency and quality of groupings and incorporate the 2021 census categorisations.

- Removed table `lu_ethnicity`  
- Removed table `lu_ethnicity_key`  
- Removed table `lu_ethnicity_sde`  
- Added table [`lu_ethnicity2`](../Data/Lookup.md#lu_ethnicity2)  
- Added table [`lu_ethnicity2_map`](../Data/Lookup.md#lu_ethnicity2_map)  

## LSOA and IMD
Updated LSOA and IMD tables to provide better incorporation of LSOA 2021 and greater information on LSOAs outside NEL.

- Removed table `lu_lsoa`  
- Removed table `lu_deprivation`  
- Added table [`lu_imd2019`](../Data/Lookup.md#lu_imd2019) - IMD ranking and quintiles
- Added table [`lu_localauthority`](../Data/Lookup.md#lu_localauthority) - Local Authorities for UK
- Added table [`lu_ons`](../Data/Lookup.md#lu_ons) - ONS codes for UK geographies (Local Authorities, ICBs, Regions etc) 


