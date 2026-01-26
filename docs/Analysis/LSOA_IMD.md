# LSOA and IMD
## LSOA Overview
Lower Super Output Area are geographical areas defined by the ONS based on the UK census.  They contain 400-1200 households with a population of 1000-3000 individuals.  At a higher level, groups of 4-5 LSOAs are designated as Middle Super Output Areas (MSOAs) which fit within local authority boundaries.  At a more granular level, LSOAs contain 4-5 Output Areas (OAs) of around 500 people. As data becomes potentially identifiable at this level, OAs are not generally used in statistical analysis or provided in ELDB.

LSOA 2021 is the update of LSOA 2011 based on the Census 2021 data.  Many of the 2011 geographies have remained the same, but in some areas LSOAs have been either split or merged, to account for changes in housing and population density.  Where this has occurred, the LSOA 2021 has been given a new code, otherwise for unchanged LSOAs, the 2011 codes have passed across to LSOA 2021.  The [`lu_lsoa2021`](../Data/Lookup.md#lu_lsoa2021) lookup table provides a comparison of LSOA 2021 to LSOA 2011, and to local authority, with a `changed` column showing the relationship: U (unchanged), S (split) and M (merged).  
## Indices of Multiple Deprivation Overview
Each nation within the UK calculates an indices of deprivation score from a series of localised socio-economic scores and rankings (unemployment, crime rate, income etc).  The calculation differs, however, between nations depending on available statistics, as well as the geographical unit and data time point:

* **England** and **Wales** both use LSOA (1000-3000 individuals) and have recently created IMD2025 and WIMD2025 based on LSOA2021 from the 2021 census.  The previous IMD2019 used LSOA2011.
* **Scotland** uses a SIMD score and ranking based on Data Zones (500-1000 residents), a sub-division of Local Authority boundaries.  The current ranking is SIMD2020 based on DZ2011. DZ2022 has been published, using the 2022 Scottish census data, and the updated SIMD is expected in 2026.  
* **Northern Ireland** has the NIMDM (*Northern Ireland Multiple Deprivation Measures*) score, the latest being NIMDM2017.  This used SOA2011 (Super Output Area) of around 2100 people. This has been superseded however by the Super Data Zone (avg 2200 residents) and the Data Zone (100-625 people). An updated NIMDM ranking based on SDZ2021 is still being planned.

Due to these variances, it is not safe to combine or compare deprivation scores to create a UK, or even an England & Wales, ranking.

The IMD is provided as a score but is more readily usable as a national rank (1 is most deprived), which is grouped by the ONS into national deciles and quintiles. For ELDB, CEG have also calculated quintiles at ICB and and local authority level.  Available in the [`lu_imd2025`](../Data/Lookup.md#lu_imd2025) and  [`lu_imd2019`](../Data/Lookup.md#lu_imd2019) lookup tables.

## IMD & LSOA by Postcode
For ELDB2025 we have used ONS postcodes-LSOA lookup tables, with the patient's postcode available via Compass, to map each patient's address to a LSOA2021 and a LSOA2011.  This gets round the issue of split or merged LSOA and allows us, in turn, to provide an IMD 2019 score and rank for the patient.  All this information is provide in the [`CORE`](../Data/Core.md) table.



