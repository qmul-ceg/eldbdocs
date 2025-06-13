# LSOA and IMD
## LSOA Overview
Lower Super Output Area are geographical areas defined by the ONS based on the UK census.  They contain 400-1200 households with a population of 1000-3000 individuals.  At a higher level, groups of 4-5 LSOAs are designated as Middle Super Output Areas (MSOAs) which fit within local authority boundaries.  At a more granular level, LSOAs contain 4-5 Output Areas (OAs) of around 500 people. As data becomes potentially identifiable at this level, OAs are not generally used in statistical analysis or provided in ELDB.

LSOA 2021 is the update of LSOA 2011 based on the Census 2021 data.  Many of the 2011 geographies have remained the same, but in some areas LSOAs have been either split or merged, to account for changes in housing and population density.  Where this has occurred, the LSOA 2021 has been given a new code, otherwise for unchanged LSOAs, the 2011 codes have passed across to LSOA 2021.  The [`lu_lsoa2021`](../Data/Lookup.md#lu_lsoa2021) lookup table provides a comparison of LSOA 2021 to LSOA 2011, and to local authority, with a `changed` column showing the relationship: U (unchanged), S (split) and M (merged).  
## IMD Overview
Indices of Multiple Deprivation (IMD) are a UK classification of relative deprivation (ie poverty) derived from component scores (unemployment, crime rate, income etc).  They are produced at LSOA level in England and Wales, whilst Scotland and Northern Ireland use Data Zone and Super Output Area.  There are difficulties therefore making comparisons between England and Wales, and the rest of the UK.  

The IMD is available as a score but is more readily usable as a national rank (1 is most deprived).  ONS provide national decile and quintile. For ELDB, quintiles have also been calculated at ICB and and local authority level.  Available in the [`lu_imd2019`](../Data/Lookup.md#lu_imd2019) lookup table.

The most recent IMD calculation provided by ONS was in 2019, with the previous calculation in 2015. An update to English IMD has been announced for late 2025 ([OCSI](https://ocsi.uk/2023/07/10/we-are-updating-the-english-indices-of-deprivation){.new-tab} ), which is expected to use the latest LSOA 2021 geographies.  In the meantime, the available IMD 2019 can only link to LSOA 2011.

## IMD & LSOA by Postcode
For ELDB2025 we have used ONS postcodes-LSOA lookup tables, with the patient's postcode available via Compass, to map each patient's address to a LSOA2021 and a LSOA2011.  This gets round the issue of split or merged LSOA and allows us, in turn, to provide an IMD 2019 score and rank for the patient.  All this information is provide in the [`CORE`](../Data/core.md) table.



