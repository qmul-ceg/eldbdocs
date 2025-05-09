# Data Overview
The East London Database is a series of annual databases containing data from the 1st April for patients registered with GP practices within north east London on that date. The coverage has expanded over the years to now include all practices in the North East London ICB area (City & Hackney, Newham, Tower Hamlets, Waltham Forest, Redbridge, Barking & Dagenham, and Havering).

- eldb2014 – eldb2019: contain data obtained from EMIS for inner east London. Hosted in MS Access and not currently available to external analysts.
- eldb2020: contains data from EMIS for inner east London. It is hosted and available to external analysts on our ELDB SQL Server.
- eldb2021 – onwards: contains data from our copy of the Discovery Data Service for all North East London. It is hosted and available to external analysts on our ELDB SQL Server.

Each year contains tables providing the earliest and/or latest codes for the standard QOF registers and clinical measures (Blood Pressure, HbA1c etc) as well as additional register, activity, and status tables. We have made changes and improvements to the schema and included tables for the database each year.

## Data Flow
ELDB contains data derived from the Discovery Data Service (DDS), via the CEG Compass database, for all practices within the North East London ICB area (City & Hackney, Newham, Tower Hamlets, Waltham Forest, Redbridge, Barking & Dagenham, and Havering).  
Voror, the company managing DDS, receive data on a daily basis from Optum(EMIS) and TTP(SystmOne), the two clinical system providers in the area, which they process into the DDS.  CEG maintain an API to file and update a copy of this data each night into our Compass database.  From eldb2021 onwards, the annual ELDB database has been created from Compass, using purpose built SQL scripts, as a one-off snapshot of the data at 1st April each year.

The ELDB data is not an exact copy, therefore, of the patient records held on the GP clinical systems.  Not all data fields are passed to Voror and the data undergoes a series of transformations on its path to the ELDB database.  The clinical systems are also designed for managing the healthcare of currently registered patients and so the data they contain is constantly being updated and is not always in sync with DDS and Compass.  Compass has been validated as providing results close to those pulled from clinical systems and further validation checks are carried out when building each annual database.  Reports derived from ELDB should not be compared, however, with reports derived directly from EMIS Web and SystmOne clinial systems.

Prior to eldb2024, additions and updates to the data were drawn from Compass. Because of the changing nature of the clinical system data, this process could introduce some anomalies of patient inclusion, age-at-event and code changes.  From eldb2024 onwards, we have instead taken a snapshot of the full Compass data for the 1st April and used this to build the registers and other tables.  This means that the data is consistent throughout the database. 
