# Changes from ELDB 2024
## Data
All data has been rerun from 01/04/2025.
## Database Info
Added [`db_clusters`](../Data/Structure_Info.md#db_clusters-code-clusters-in-tables) - NHS and CEG code clusters used to build tables  
Added [`db_codeset_ceg`](../Data/Structure_Info.md#db_codeset_ceg-ceg-code-clusters) - CEG code clusters used in ELDB  

## Ethnicity
Updated ethnicity tables to improve consistency and quality of groupings and incorporate the 2021 census categorisations.
Removed `lu_ethnicity`  
Removed `lu_ethnicity_key`  
Removed `lu_ethnicity_sde`  
Added [`lu_ethnicity2`](../Data/Lookup.md#lu_ethnicity2)  
Added [`lu_ethnicity2_map`](../Data/Lookup.md#lu_ethnicity2_map)  

## LSOA and IMD
Updated LSOA and IMD tables to provide better incorporation of LSOA 2021 and greater information on LSOAs outside NEL.
Removed `lu_lsoa`  
Removed `lu_deprivation`  
Added [`lu_imd2019`](../Data/Lookup.md#lu_imd2019) - IMD ranking and quintiles
Added [`lu_localauthority`](../Data/Lookup.md#lu_localauthority) - Local Authorities for UK
Added [`lu_ons`](../Data/Lookup.md#lu_ons) - ONS codes for UK geographies (Local Authorities, ICBs, Regions etc) 


