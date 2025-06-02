---
publish: "true"
---
# Smoking, Alcohol & Drug Use

## `smoking`
*Smoking codes (SMOK_COD and NDASMOK_COD).*

fieldname         | description
----------------- |------------
latest_date       | latest code date
latest_code       | latest code
latest_name       | latest code name
smoking_status    | provides smoking status according to latest code (from either SMOK_COD or NDASMOK_COD)
qof_latest_date   | latest QOF code date
qof_latest_code   | latest QOF code
qof_latest_name   | latest QOF code name
qof_smoking_status | latest smoking status according to latest QOF code (SMOK_COD)  
                   | *Use this column when analysing smoking status by QOF definition only.*

> **Note:**  
> QOF-only columns contain codes from SMOK_COD only and may include NULLs.  
> Use `smoking_status` for all current smoking codes.  
> Use `qof_smoking_status` only when interested in QOF definitions.

## `alcohol`
*Alcohol consumption and intervention-related codes:  
(ALC_COD, AUDIT_COD, AUDITC_COD, FAST_COD, ALCADV_COD, ALCBRINT_COD, ALCEXINT_COD, ALCREF_COD, ALCINTDEC_COD).*

fieldname                  | description
-------------------------- |------------
latest_date                | latest date of any alcohol consumption code, including codes without a value
latest_code                | SNOMED concept id for latest code
latest_name                | code term for latest code
consume_latest_date        | latest date of alcohol consumption code with a value
consume_latest_code        | SNOMED concept id for latest alcohol consumption code
consume_latest_name        | code term for latest alcohol consumption code
consume_latest_value       | latest alcohol consumption value recorded
consume_latest_units       | unit of measure and time period for consume_latest_value
consume_latest_units_pw    | standardised alcohol consumption (units per week)  
                           | *See Appendix 1: Alcohol Units Per Week*
audit_latest_date          | latest alcohol audit code date
audit_latest_code          | SNOMED concept id for latest alcohol audit code
audit_latest_name          | code term for latest alcohol audit code
audit_latest_value         | latest alcohol audit value recorded
auditc_latest_date         | latest Alcohol Audit-C code date
auditc_latest_code         | SNOMED concept id for latest Alcohol Audit-C code
auditc_latest_name         | code term for latest Alcohol Audit-C code
auditc_latest_value        | latest Alcohol Audit-C value recorded
fast_latest_date           | latest Alcohol FAST code date
fast_latest_code           | SNOMED concept id for latest Alcohol FAST code
fast_latest_name           | code term for latest Alcohol FAST code
fast_latest_value          | latest Alcohol FAST value recorded
advice_latest_date         | latest Alcohol Advice code date
advice_latest_code         | SNOMED concept id for latest Alcohol Advice code
advice_latest_name         | code term for latest Alcohol Advice code
briefint_latest_date       | latest Alcohol Brief Intervention code date
briefint_latest_code       | SNOMED concept id for latest Alcohol Brief Intervention code
briefint_latest_name       | code term for latest Alcohol Brief Intervention code
extendedint_latest_date    | latest Alcohol Extended Intervention code date
extendedint_latest_code    | SNOMED concept id for latest Alcohol Extended Intervention code
extendedint_latest_name    | code term for latest Alcohol Extended Intervention code
referral_latest_date       | latest Alcohol Referral code date
referral_latest_code       | SNOMED concept id for latest Alcohol Referral code
referral_latest_name       | code term for latest Alcohol Referral code
declinedint_latest_date    | latest Alcohol Intervention Declined code date
declinedint_latest_code    | SNOMED concept id for latest Alcohol Intervention Declined code
declinedint_latest_name    | code term for latest Alcohol Intervention Declined code

## `substance_misuse`
*Illicit Substance Abuse code (ILLSUB_COD), excluding patients with a more recent  
Non-Substance Misuser code (NONILLSUM_CEG).  
Includes Illegal Substance Use Intervention code (ILLSUBINT_COD).*

fieldname         | description
----------------- |------------
latest_date       | latest date of code for register
latest_code       | SNOMED concept id for latest code
latest_name       | code term for latest code
int_latest_date   | latest date of intervention code
int_latest_code   | SNOMED concept id for latest intervention code
int_latest_name   | code term for latest intervention code

> **Note:**  
> The ILLSUB_COD code set includes codes for non-substance misuse.  
> Patients whose latest code indicates non-substance misuse are excluded.
