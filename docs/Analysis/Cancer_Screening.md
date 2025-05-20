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