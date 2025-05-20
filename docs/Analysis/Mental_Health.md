## Mental Health

Mental Health conditions can be difficult to identify within health
data. The conditions can be transitory or episodic, meaning coding does
not necessarily reflect the patient's current health. The experience and
treatment of a mental health issue is also individual to a patient,
meaning the presence of a code, particularly for Common Mental Health
Disorders, does not provide a clear indication of the severity of the
condition, the impact it has on the patient's life and wellbeing, or the
way the condition is being managed. Patients may also exhibit multiple
mental health problems, which a clinician may choose to code and treat
in different ways depending on perceived priorities or causations.
Finally, clinicians and patients may prefer to use or accept particular
diagnoses, which can affect the coding used in the patient's record.

Mental Health data is provided across a series of registers.

### Anxiety

The ***anxiety*** table includes codes associated with the Common Mental
Health Disorders, with the exclusion of Depression, as defined by NICE:

generalised anxiety disorder

panic disorder

obsessive-compulsive disorder (OCD)

post-traumatic stress disorder (PTSD)

social anxiety disorder

depression

Inclusion is for codes recorded in the last 24 months, as a reasonable
timeframe for ensuring patients are currently being managed, to some
level, for their condition.

### Depression

The ***depression*** table contains all patients who have been coded for
depression since 01/04/2006 (QOF definition). The latest code is
provided, as well as the earliest, so it is possible to filter for
patients who have been recently coded with depression eg in the last 12
or 24 months.

Depression codes, however, are not consistently or regularly re-entered
and there are many patients who appear to be receiving ongoing treatment
for depression, but who have no recent depression coding. Conversely,
the 'depression resolved' code is not consistently applied, so the
register will also include patients who are no longer be treated as
depressed.

### Antidepressants

The **prescribed_antidepressant** table contains all patients who have
been prescribed anti-depressant medication (BNF 04:03 excluding
amitriptyline) in the past six months. Amitriptyline is excluded as it
is not recommended for treating depression and is more commonly
prescribed for pain relief. Other drugs within this chapter may also be
prescribed for conditions other than depression, sometimes with
differing dosages:

  --------------------------------------------------------------------------
       BNF VTM   Medication        Depression       Other Conditions +
                                   dosage           dosage
  -------- ----- ----------------- ---------------- ------------------------
    403010 F0    Clomipramine      Depression       Phobic + OCD \>=10mg
                 hydrochloride     \>=10mg          

    403010 L0    Doxepin           Depression       Pruritus in eczema
                                   \>=75mg          3-12mg (cream)

    403010 N0    ﻿﻿﻿Imipramine        Depression       Childhood Bedwetting
                 hydrochloride     \>=75mg          25-75mg

    403010 X0    Trazodone         Depression       Anxiety 75-300mg
                 hydrochloride     \>=100mg         

    403020 K0    Moclobemide       Depression       Anxiety 300-600mg
                                   \>=150mg         

    403030 D0    Citalopram        Depression       Panic 10-40mg
                 hydrobromide      10-40mg          

    403030 Z0    Citalopram        Depression       Panic 40mg/1ml
                 hydrochloride     40mg/1ml         

    403030 X0    Escitalopram      Depression       Anxiety, OCD & Panic
                                   5-20mg           5-20mg

    403030 E0    Fluoxetine        Depression       Bulimia 40-60mg, OCD
                 hydrochloride     20-60mg          20-60mg, Menopause 20mg

    403030 L0    Fluvoxamine       Depression       OCD 50-300mg
                 maleate           50-300mg         

    403030 P0    Paroxetine        Depression       OCD 20-60mg, Panic
                 hydrochloride     20-50mg          10-60mg, Menopause 10mg

    403030 Q0    Sertraline        Depression       OCD 50-200mg, Panic,
                 hydrochloride     50-200mg         PTSD & Anxiety
                                                    25mg-200mg

    403040 Y0    Duloxetine        Depression 60mg  Anxiety 30-120mg, DM
                 hydrochloride                      Neuro 60-120mg, female
                                                    incontinence 20-40mg

    403040 W0    Venlafaxine       Depression       Anxiety 75-225mg, Panic
                                   \>=75mg          37.5mg-225mg, Menopause
                                                    37.5mg-75mg
  --------------------------------------------------------------------------

Patients may be instructed to take multiple tablets per day and may have
concurrent prescriptions for different strength medications. The
particular dosage shown in the latest6m_name field should only be taken
as a rough indicator of the medication dosage that has been advised for
the patient and whether they are being treated for a condition other
than depression.

The prescribed product shown in the latest6m_code and name is the latest
prescription within a prescription course for that medication and
dosage. That prescription course may be a Repeat course (allowing the
patient to re-order the prescription) or an Acute course (a one-off
prescription). The table provides the latest Repeat prescription or, if
no Repeat prescription has occurred in the last six months, the latest
Acute (one-off) prescription. This is shown in the prescription_type
column. The prescription_count gives the number of prescriptions that
have been made within the prescription course to date and the
prescription_earliest_date gives the date of the first prescription
within the course.

### Active Depression

The **prescribed_antidepressants** table can be joined to the
**depression table**, in order to identify patients with both a
depression code and a current anti-depressant medication. As described
above, there is no guarantee however that the patient isn't being
medicated for an alternative condition. Attention may want to be given,
therefore, to the type of prescription, how long the prescription has
been in place and to the dosage.

The **prescribed_antidepressants** table could also be cross-referenced
against the **anxiety** and **eating disorders** registers to further
identify patients that are possibly receiving the medication for these
conditions, rather than depression.

Patients with depression may also follow talking therapies rather than
take medication. It is advisable, therefore, to also include patients
without an anti-depressant prescription but with a recent depression
code.

### Eating Disorder

The ***eating_disorder*** register contains patients with mental health
conditions linked to beliefs about their weight or body shape, such as
Anorexia Nervosa, Bulimia and Binge Eating. These conditions are not
listed by NICE as CMHD.

The register does not include patients with Other Specified Feeding or
Eating Disorder (OSFED), whose condition is linked to other beliefs or
concerns, or patients with Avoidant/Restrictive Food Intake Disorder
(ARFID), who choose to avoid or limit their intake of certain foods. It
is expected that these patients will also have more general codes in
their records that will place them into the ***anxiety*** or
***severe_mental_illness*** registers.

### Severe Mental Illness

The ***severe_mental_illness*** register includes persistent long term
mental health conditions, such as schizophrenia and bipolar disorder. It
also includes anyone currently prescribed lithium.

### Personality Disorder

The ***personality_disorder*** register is a non-QOF register specific
to personality disorders. It uses codes that do not appear in the MH_COD
codeset used for *severe_mental_illness*. Patients may have been coded
however to appear in both tables.
