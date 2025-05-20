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