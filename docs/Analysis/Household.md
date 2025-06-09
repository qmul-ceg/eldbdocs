# Household
## Household Methodology
The [`status_household`](../Data/Accommodation.md#status_household) table contains the residency for patients on 01/04/2024, as calculated using the ASSIGN algorithm developed by CEG in collaboration with the Endeavour Health charity. ASSIGN is a  quality-assured and validated address-matching algorithm with a 98.6% match rate (based on a population of 1.8 million adults registered with a GP in northeast London) and a high sensitivity and positive predictive value [1]. For any provided address, ASSIGN allocates a UPRN from the Ordnance Survey Great Britain property gazetteer database AddressBase Premium. This UPRN is first pseudonymised and then converted into a *property_id* which is unique solely within the database. The  
*property_id* cannot be used therefore for linking with any external data, but does provide a means to link patients into co-habiting 'households', size of which is shown in the `patient_count` column.

The `property_id` and `patient_count` information is only provided for successful ASSIGN property matches. The `match_status_id` gives a breakdown of ASSIGN outcome:

1. Residency  
2. Non-Residential Property (ie the ASSIGN identified UPRN does not have residential classification (see below))  
3. Imprecise Match (ie ASSIGN could not precisely identify a property from the patient address details)  
4. Multiple Address (ie the address data shows the patient residing at more than 1 property)  
5. No Match Data (ie no address or ASSIGN result found for the patient)  
6. Improbable Household (ie over 10 patients identified as residing at the property (see below))  
## Non-Residential Properties
The AddressBase Premium provides information on each UPRN including a use classification. Any property without a Residential or Unclassified classification is excluded from the result. Unclassified properties are included as these are very often new residential properties. Residential covers all types of house, flats, caravans, house boats, sheltered accommodation and HMOs, as well as properties simply classified as 'Residential' or 'Dwelling'. It does not include Residential Institutions, such as nursing/care homes or halls of residency, nor hotels and hostels. Some of these classifications may become available in the future if validated.
## Improbable Households
A household is defined in our analyses as 'a group of residents living at the same property at the same time'. From our analyses, we have concluded that it is improbable that a household will consist of more 
than 10 people. Where this is found in the data, it is more likely that the patient's address data is incomplete, or the property is a hostel or institution of some kind. These properties are therefore excluded from the results.

[1] Harper, G., Stables, D., Simon, P., Ahmed, Z., Smith, K., Robson, J. and Dezateux, C. (2021) 'Evaluation of the ASSIGN open-source deterministic address-matching algorithm for allocating Unique Property Reference Numbers to general practitioner-recorded patient addresses", *International Journal of Population Data Science*, 6(1). doi: <https://doi.org/10.23889/ijpds.v6i1.1674>
