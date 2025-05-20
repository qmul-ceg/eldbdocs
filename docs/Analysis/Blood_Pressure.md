# Information: Blood Pressure

## Methodology
In the Compass data, a blood pressure is represented by a combination of up to 3 codes:

- The *parent*, or reading, code to indicate a Blood Pressure has been taken but with no attached value. This is often *SN 163020007 (On examination - blood pressure reading (finding))*
- A *systolic* code with a value and a link in the data to the parent code. This is often *SN 72313002 (Systolic arterial pressure (observable entity))*
- A *diastolic* code with a value and a link in the data to the parent code. This is often *SN 1091811000000102 (Diastolic arterial pressure (observable entity))*

Multiple blood pressures can be taken on the same day but, in theory, every blood pressure reading should have all 3 of these codes, ensuring the correct systolic and diastolic values can be matched up with confidence. In practice, the data is not always so neat: systolic and diastolic codes can exist without a parent code; or without a matching value code; or without a value; and parent codes can sometimes link to more than one systolic or diastolic code. Identifying blood pressures requires, therefore, finding and matching systolic and diastolic records using combinations of their parent record id, their date and their database record id. This last element is used as a proxy for time within a given day, as Compass does not contain the time of code entry onto the clinical system.

The blood pressure codes are matched, therefore, using 4 algorithms:

1. Systolic records with a value are matched to diastolic records with a value, using their common parent record id.
2. Where algorithm 1 returns multiple diastolic records for a single systolic/parent record, the diastolic record with the nearest record id to the systolic record id is chosen
3. Systolic records not matched by algorithms 1 & 2 are matched with the diastolic record on the same date, where there is only 1 diastolic\* record for that date.
4. Systolic records not matched by algorithms 1, 2 & 3 are ranked by date and record id and matched against the similarly ranked remaining diastolic records.

Matched records in which either the systolic or diastolic value is NULL are removed and the remaining records are ranked by date and the systolic record id to find the latest record.

The blood pressures in the `measures_blood` table are therefore the blood pressures readings for which it is possible to define a systolic/diastolic value. Readings with NULL and missing values have been filtered out.  The `bpparent_code` and `bpparent_name` fields provide the code where a parent code was used in the match. The `match_algorithm` column provides the number of the algorithm used for the match, as shown above.  Details provided in [Measures: Blood Pressure](/Data/Measures/#Blood-Pressure-BP).

