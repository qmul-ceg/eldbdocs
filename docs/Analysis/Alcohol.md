# Alcohol
## Alcohol Units Per Week
The `consume_latest_units_per_week` is a calculated units value derived from the text of `consume_latest_units`.  The text is parsed in the following manner:

**Find units for value**  (units)  
if `consume_latest_units` contains "pint" - units = value \* 2.3 (assuming 1 pint of 4% ABV)    
if `consume_latest_units` contains "glass" - units = value \* 2.3 (assuming 175ml glass of 13% ABV)  
if `consume_latest_units` contains "bottle" - units = value \* 10  
otherwise - units = 1

**Find multiplier for value** (multiplier)  
if `consume_latest_code` = SN 105542008 (Teetotaller) - multiplier = 0  
if `consume_latest_code` = SN 1082641000000106 (Alcohol units per week) - multiplier = 1  
if `consume_latest_code` = SN 266917007 (Trivial drinker - \<1u/day) - multiplier = 1  
(Units are sometimes given as \"/day\" but with a value \> 7.  All instances assumed to be for week.)  
if `consume_latest_code` = SN 442547005 (Alcohol units consumed on heaviest drinking day) - multiplier = 1.5  
(This code provides no clear indication for weekly consumption. Estimated as half again per week.)  
if `consume_latest_code` = contains no indication of time period - multiplier = 1  
(Assuming value is for a week)  

if `consume_latest_units` contains \'day\' or variation - multiplier = 7  
if `consume_latest_units` contains \'week\' or variation - multiplier = 1  
if `consume_latest_units` contains \'fortnight\' or variation - multiplier = 1/2  
if `consume_latest_units` contains \'3 weeks\' or variation - multiplier = 1/3  
if `consume_latest_units` contains \'month\' or variation - multiplier = 1/4  
if `consume_latest_units` contains \'2 months\' or variation - multiplier =1/8  
if `consume_latest_units` contains \'3 months or variation - multiplier = 1/13  
if `consume_latest_units` contains \'4 months\' or variation - multiplier = 1/17  
if `consume_latest_units` contains \'6 months\' or variation - multiplier = 1/26  
if `consume_latest_units` contains \'year\' or variation - multiplier = 1/52  
if `consume_latest_units` contains \'Never\' or variation - multiplier = 0  

Creating a calculation:  
**latest_units_pw = latest_value \* units \* multiplier**  
OR  
if `consume_latest_units` contains "occasionally" or a variation - **latest_units_pw = 0.55**  
(Estimating consumption, whatever value, will be below 1 unit per week)