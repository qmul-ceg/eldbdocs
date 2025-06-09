# Known Issues

## ELDB2025 Data Issues
### Missing Practices
Two Waltham Forest practices were not available in the Compass data at the time of the data extract in April 2025 due to issue with the data streamed from Optum (EMIS).
- Forest Surgery (F86026)
- WF Community & Family Health Services Ltd (F86644)
This data has now been filed into Compass and we plan to extract and merge the data for these two practices into the current ELDB2025 during July 2025.

## General Data Issues
### Patient Registration
A patient’s current practice registration and date, as shown in the CORE table, is calculated using the available registration data in Compass.  The EMIS API to DDS does not contain the full detailed registration process history which EMIS uses to refine its GP Practice Currently Registered list, particularly in relation to patients moving to or from a practice.  The practice lists in ELDB can therefore include patients that EMIS would define as having moved to another practice.  Listsizes with EMIS may differ by ±2%.
### Code Episode
EMIS uses the Episode field for an entered clinical code in its QOF syntax to identify patients and diagnosis dates for Depression and Epilepsy. This field indicates whether an entered code relates to a new or first episode of the condition, or an ongoing review.  The EMIS API however does not pass this field to DDS.  Without this field, the registers derived from Compass can only find the initial diagnosis date of the condition.  Furthermore, it means patients with a resolved code followed by a code with a Review or End Episode flag are excluded from EMIS reports but included in Compass based reports.
