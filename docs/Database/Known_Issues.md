# Known Issues

## ELDB2025 Data Issues
### Missing Practices
The data for three practices was not initially available in the Compass data for the ELDB build,
due to an issue with the data streamed from Optum (EMIS). 

- Forest Surgery (F86026)
- Waltham Forest Community & Family Health Services Ltd (F86644)
- Beam Park Medical Practice (Y08371)

The data has now filed into Compass and a separate data extract has been run for these three practices.  ELDB2025 was regenerated in July 2025 using the now complete ELDB2025 data extract (eldb2025.2.0).

## General Data Issues
### Patient Registration
A patient’s current practice registration and date, as shown in the CORE table, is calculated using the available registration data in Compass.  The EMIS API to DDS does not contain the full detailed registration process history which EMIS uses to refine its GP Practice Currently Registered list, particularly in relation to patients moving to or from a practice.  The practice lists in ELDB can therefore include patients that EMIS would define as having moved to another practice.  Listsizes with EMIS may differ by ±2%.
### Code Episode
EMIS uses the Episode field for an entered clinical code in its QOF syntax to identify patients and diagnosis dates for Depression and Epilepsy. This field indicates whether an entered code relates to a new or first episode of the condition, or an ongoing review.  The EMIS API however does not pass this field to DDS.  Without this field, the registers derived from Compass can only find the initial diagnosis date of the condition.  Furthermore, it means patients with a resolved code followed by a code with a Review or End Episode flag are excluded from EMIS reports but included in Compass based reports.
