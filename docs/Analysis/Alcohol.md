# Alcohol
## Alcohol Units Per Week

Units per week calculated from an units value and multiplier, both
derived from latest_units text.

**Find units for value**

latest_units contains \'pint\' - units = value \* 2.3

(assume pint of 4% beer)

latest_units contains \'glass\' - units = value \* 2.3

(assume 175ml glass of medium strength wine)

latest_units contains \'bottle\' - units = value \* 10

otherwise - units = 1

**Find multiplier for value**

latest_code = SN 105542008 (Teetotaller) - multiplier = 0

latest_code = SN 1082641000000106 (Alcohol units per week) - multiplier
= 1

latest_code = SN 266917007 (Trivial drinker - \<1u/day) - multiplier = 1

(Units are sometimes given as \"/day\" but value \> 7. All instances of
code assumed to be for week)

latest_code = SN 442547005 (Alcohol units consumed on heaviest drinking
day) - multiplier = 1.5

(code provides no clear indication for weekly consumption. Estimate as
half again per week)

latest_units contains no indication of time period - multiplier = 1

(assume value is for week)

latest_units contains \'day\' or variation - multiplier = 7

latest_units contains \'week\' or variation - multiplier = 1

latest_units contains \'fortnight\' or variation - multiplier = 1/2

latest_units contains \'3 weeks\' or variation - multiplier = 1/3

latest_units contains \'month\' or variation - multiplier = 1/4

latest_units contains \'2 months\' or variation - multiplier =1/8

latest_units contains \'3 months or variation - multiplier = 1/13

latest_units contains \'4 months\' or variation - multiplier = 1/17

latest_units contains \'6 months\' or variation - multiplier = 1/26

latest_units contains \'year\' or variation - multiplier = 1/52

latest_units contains \'Never\' or variation - multiplier = 0

**latest_units_pw = latest_value \* units \* multiplier**

OR

if latest_units contains \'occassionally\' or variation -
**latest_units_pw = 0.55**

(Estimate consumption, whatever value will be below 1 unit per week)