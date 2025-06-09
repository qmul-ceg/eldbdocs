# NHS Health Checks
## NHS Health Checks Overview
NHS Health Checks are undertaken on patients who do not have a pre-existing Long Term Condition and/or have not been prescribed statins, as these patients will receive regular checkups within their
specific care pathway. On this basis, whilst the GP practice may have carried out the activity, a NHS Health Check recorded for a patient that had one or more of the conditions listed below on the date of the NHS Health Check would not be considered valid for inclusion in the service and payment.

## NHS Health Check Ineligibility
The [`nhs_healthcheck`](../Data/NHS_Health_Checks.md#nhs_healthcheck-nhs-health-check-done-nhs-hc) table provides information on recorded NHS Health Checks.  The `inelig_earliest_date` provides the earliest date at which a patient was diagnosed with a LTC or was prescribed statins and so become ineligible for a NHS Health Check. The `inelig_table` column provides the table name from which the `inelig_earliest_date` was derived. The `valid_nhshc` field provides a Y/N definition of the Health Check validity, based on the `inelig_earliest_date` compared to the NHS Health Check `latest_date`.

Conditions that define NHS Health Check ineligibility are:

- Hypertension ([`hypertension`](../Data/Registers.md#hypertension-ht))
- Diabetes ([`diabetes`](../Data/Registers.md#diabetes-diabetes-mellitus-dm))
- CKD ([`ckd`](../Data/Registers.md#ckd-chronic-kidney-disease))
- Heart Failure ([`heart_failure`](../Data/Registers.md#heart_failure-hf))
- PAD ([`pad`](../Data/Registers.md#pad-peripheral-arterial-disease))
- Familial Hypercholesterolemia ([`f_hypercholesterolemia`](../Data/Registers.md#f_hypercholesterolemia-familial-hypercholesteremia-fh))
- Stroke TIA ([`stroke_tia`](../Data/Registers.md#stroke_tia-stroke-transient-ischaemia-attack))
- CHD ([`chd`](../Data/Registers.md#chd-chronic-heart-disease))
- Arterial Fibrillation ([`atrial_fibrillation`](../Data/Registers.md#atrial_fibrillation-af))
- Statin Prescription. ([`prescribed_statins`](../Data/Prescriptions.md#prescribed_statins))
