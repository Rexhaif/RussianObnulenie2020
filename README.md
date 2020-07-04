# RussianObnulenie2020
- CSV formatted data from Russian Constitutional Voting 2020 (Obnulenie aka Putin's presidential terms zeroing)
- Based on Sergey Shpilkin raw data, exported from Russian election control system (ГАС "Выборы")

#### This is the first version with non-final results, i'll update it as new data comes.
#### Raw data can be obtained here: https://t.me/RUElectionData

## Preamble
- Obnulenie 2020 is country-wide voting on russian constitutional amendments, proposed by Vladimir Putin
- Amendments includes major imbalancing for Separation of powers principle, as well as "zeroing" of Putin's presidential terms, which allows him to stay in power up to the year of 2036
- Also, these amendments includes some "constitutional sugar" of social guarantees, forbidding separatism and even homophobic defention of marriage as union of man and women
- This voting was implemented without framework of any Federal Regualtions, procedure was declared in a set of internal docs of Central Election Commitee
- There was, reportedly, enourmous amount of election fraud, up to 22 million votes was faked. However, some local pooling station has adequate procedures, with no fraud. This was enforced by independent commitee members.

## Data format
_uiks-sig.csv and uiks-utf8.csv differs only be encoding, utf-8-sig for *-sig and plain utf-8 for *-utf8, this is for compatibility with russian language and Microsoft Excel_
-----------------------------
Each row represents data from single "Local Election Commitee". Such commitee can be uniquely identified by concatenation of **region_name**, **tik_name**, **uik_name**. Also, there may be duplicate latitude\longitude for two or three rows, that's completely ok, because several pooling station can be located in the same building, but on different floors.
### Columns
- **region_name** - name of state of Russian Federation, where particular election site is located, unique countrywide
- **tik_name** - name of "Territorial Election Commitee" - middle level of russian election system, which controls and collects data from several "Local Election Commitees", located in particular district
- **uik_name** - name of "Local Election Commitee" - lowest level of russian election system, single pooling station, typically has 1000-3000 people registered by default(via permanent residence), unique state-wide
- **registered_voters** - number of people, registered at particular "Local Election Commitee".
- **used_ballots** - number of ballots, which were given to voters, must be lower or equal to **registered_voters**.
- **found_ballots** - number of ballots, which were found in voting boxes at the end of day, must be lower or equal to **used_ballots**.
- **incorrect_ballots** - number of ballots, which were recognized as incorrect(multiple or none checkboxex marked, misused ballots, etc.)
- **yes_votes** - number of ballots, which has any mark in checkbox for "YES" option, must be equal to: 
                  ![formula](https://render.githubusercontent.com/render/math?math=found\_ballots-no\_votes-incorrect\_ballots)
- **no_votes** - number of ballots, which has any mark in checkbox for "NO" option, must be equal to:
                  ![formula](https://render.githubusercontent.com/render/math?math=found\_ballots-yes\_votes-incorrect\_ballots)
- **latitude** - latitude of "Local Election Commitee"
- **longitude** - longitude of "Local Election Commitee"
#### currently i have lat\lon for approx 80% of records, data obtained from [here](https://wiki.gis-lab.info/w/%D0%94%D0%B0%D0%BD%D0%BD%D1%8B%D0%B5_%D0%BF%D0%BE_%D0%B8%D0%B7%D0%B1%D0%B8%D1%80%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC_%D0%BA%D0%BE%D0%BC%D0%B8%D1%81%D1%81%D0%B8%D1%8F%D0%BC_%D0%A0%D0%A4_%D0%B8%D0%B7_%D0%93%D0%90%D0%A1_%D0%92%D1%8B%D0%B1%D0%BE%D1%80%D1%8B)
