# covid
Documentation for [bit.io's covid repo](https://bit.io/covid)

Do you need to learn SQL? Checkout:<br>
https://www.sohamkamani.com/blog/2016/07/07/a-beginners-guide-to-sql/<br>
https://www.khanacademy.org/computing/computer-programming/sql<br>
https://sqlbolt.com/

* __For version and last refreshed information, see `_ingest_version` and `_ingest_timestamp` fields in each table__
* __All schema, table, and column names are converted to lowercase and underscores__

## COVID Data

UPDATE FREQUENCY: At least daily at 5pm Pacific

Dataset | Schema Name                        | Table Name                              | Description                                              | Transforms                                                                                                           | Documentation Link                                                                    | Source                                                                                                                 |
|-----------|--------------------------------|-------------------------------------|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| The COVID Tracking Project| `covidtracking`                  | `state_daily`                         | Daily case reports combined from many sources by state   | `pandas.to_datetime` on `date` and `dateChecked`                                                                               | https://covidtracking.com/api/                                                        | https://covidtracking.com/api/states/daily                                                                             |
| The COVID Tracking Project| `covidtracking`                  | `state_info`                          | Documentation on gathering approach for each state       | None                                                                                                                 | https://covidtracking.com/api/                                                        | https://covidtracking.com/api/states/info                                                                              |
| The COVID Tracking Project| `covidtracking`                  | `us_daily`                            | Daily case reports combined from many sources for all US | `pandas.to_datetime` on `date` and `dateChecked`                                                                               | https://covidtracking.com/api/                                                        | https://covidtracking.com/api/us/daily                                                                                 |
| JHU COVID Case Records| `csse_covid_19_data`             | `csse_covid_19_daily_reports`         | JHU daily case reports                                   | Merge `Last Update` and `Last_Update` <br><br> Merge `Longtitude` and `Long_` <br><br> Merge `Latitude` and `Lat` <br><br> Merge `Province/State` and `Province_State` <br><br> Merge `Country/Region` and `Country_Region` <br><br> `pandas.to_datetime` on `Last_Update` | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_daily_reports                  |
| JHU COVID Case Records| `csse_covid_19_data`             | `timeseries_covid19_confirmed_us`     | JHU aggregate confirmed US cases                         | None                                                                                                                     | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| JHU COVID Case Records| `csse_covid_19_data`             | `timeseries_covid19_confirmed_global` | JHU aggregate confirmed global cases                     | None                                                                                                                     | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| JHU COVID Case Records| `csse_covid_19_data`             | `timeseries_covid19_deaths_us`        | JHU aggregate confirmed US deaths                        | None                                                                                                                     | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| JHU COVID Case Records| `csse_covid_19_data`             | `timeseries_covid19_deaths_global`    | JHU aggregate confirmed US deaths                        | None                                                                                                                 | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| JHU COVID Case Records| `csse_covid_19_data`             | `timeseries_covid19_recovered_global` | JHU aggregate                                            | None                                                                                                                 | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| JHU COVID Case Records| `csse_covid_19_data`             | `uid_iso_fips_look_up_table`           | FIPS lookup reference table                              | Rename `Lat` to `Latitude` <br><br> Rename `Long_` to `Longtitude`                                                                                                                 | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data                   |
| JHU COVID Case Records| `who_covid_19_situation_reports` | `who_covid_19_sit_rep_time_series`    | WHO confirmed cases                                      | None                                                                                                                 | https://github.com/CSSEGISandData/COVID-19/tree/master/who_covid_19_situation_reports | https://github.com/CSSEGISandData/COVID-19/tree/master/who_covid_19_situation_reports/who_covid_19_sit_rep_time_series |
| NY Times Case Data| `nytimes`                        | `us-counties`                         | NYTimes case data by county                              | `pandas.to_datetime` on `date`                                                                                               | https://github.com/nytimes/covid-19-data                                              | https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-counties.csv                                         |
| NY Times Case Data| `nytimes`                        | `us-states`                           | NYTimes case data by state                               | `pandas.to_datetime` on `date`                                                                                               | https://github.com/nytimes/covid-19-data                                              | https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-states.csv                                           |
| Nextrain Genome Metadata| `nextstrain`                     | `metadata`                            | Nextstrain genome metadata                               | replace all `"?"` with `NULL` <br><br> replace `"*-XX"` days in `date` with month only <br><br> `pandas.to_datetime` on `date` and `date_submitted`  | https://github.com/nextstrain/ncov                                                    | https://github.com/nextstrain/ncov/blob/master/data/metadata.tsv                                                       |
| Oxford Coronavirus Government Response Tracking| `oxcgrt`                         | `data`                                | Record of each government's response measures over time  | `pandas.to_datetime` on `Date`                                                                                                                                                  | https://www.bsg.ox.ac.uk/research/research-projects/oxford-covid-19-government-response-tracker | https://www.bsg.ox.ac.uk/sites/default/files/OxCGRT_Download_latest_data.xlsx |
| European CDC Cases | `ecdc`                           | `counts`                              | European CDC's worldwide distribution records            | `pandas.to_datetime` on `dateRep`                                                                                                                                                  | https://www.ecdc.europa.eu/en/publications-data/download-todays-data-geographic-distribution-covid-19-cases-worldwide | https://opendata.ecdc.europa.eu/covid19/casedistribution/csv | 
| Edweek School Closure| `schools`                        | `closures`                            | Edweek school closure information                        | None                                                                                                                                        | https://www.edweek.org/ew/section/multimedia/map-coronavirus-and-school-closures.html | https://editproj.sharepoint.com/:x:/g/Ea32XJl_g9VBreFAia_zMmEBY6FW2ZWh8F4VeJ1Rt5Z4YA?e=rpUKYv |
| Stanford Bay Area Case Information| `stanford`                        | `bay_area`                            | Daily data of the total number of COVID-19 cases in the six Bay Area counties under "shelter in place" orders (3/3/2020-present)| `pandas.to_datetime on `date`                                                                                                                                        | https://opendata.stanforddaily.com/#/datasets/covid19_bayarea_counties | https://s3.us-east-2.amazonaws.com/open-data-portal/covid19_bayarea_counties.csv |
| Stanford Bay Area Case Information| `stanford`                        | `santa_clara`                            | Daily data of the causes and outcomes of COVID-19 cases in Santa Clara County (1/31/2020-present)| `pandas.to_datetime on `date`                                                                                                                                        | https://opendata.stanforddaily.com/#/datasets/covid19_sccph | https://s3.us-east-2.amazonaws.com/open-data-portal/covid19_sccph.csv |
| Our World in Data cases| `owind`                        | `full_data`                            | All four metrics | `pandas.to_datetime on `date`                                                                                                                                        | https://ourworldindata.org/coronavirus-source-data | https://covid.ourworldindata.org/data/ecdc/full_data.csv |
| Our World in Data cases| `owind`                        | `total_cases`                            | Total confirmed cases | `pandas.to_datetime on `date`                                                                                                                                        | https://ourworldindata.org/coronavirus-source-data | https://covid.ourworldindata.org/data/ecdc/total_cases.csv |
| Our World in Data cases| `owind`                        | `total_deaths`                            | Total deaths | `pandas.to_datetime on `date`                                                                                                                                        | https://ourworldindata.org/coronavirus-source-data | https://covid.ourworldindata.org/data/ecdc/total_deaths.csv |
| Our World in Data cases| `owind`                        | `new_cases`                            | New confirmed cases | `pandas.to_datetime on `date`                                                                                                                                        | https://ourworldindata.org/coronavirus-source-data | https://covid.ourworldindata.org/data/ecdc/new_cases.csv |
| Our World in Data cases| `owind`                        | `new_deaths`                            | New deaths | `pandas.to_datetime on `date`                                                                                                                                        | https://ourworldindata.org/coronavirus-source-data | https://covid.ourworldindata.org/data/ecdc/new_deaths.csv |
| Our World in Data cases| `owind`                        | `locations`                            | Population data | `pandas.to_datetime on `date`                                                                                                                                        | https://ourworldindata.org/coronavirus-source-data | https://covid.ourworldindata.org/data/ecdc/locations.csv |



## Reference Data

UPDATE FREQUENCY: As needed

Dataset | Schema Name                        | Table Name                              | Description                                              | Transforms                                                                                                           | Documentation Link                                                                    | Source                                                                                                                 |
|-----------|--------------------------------|-------------------------------------|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| CDC Social Vulnerability| `cdc_social_vulnerability`       | `counties_2018`                       | The social vulnerability by county                       | None                                                                                                                                                      | https://svi.cdc.gov/Documents/Data/2018_SVI_Data/SVI2018Documentation.pdf | https://svi.cdc.gov/data-and-tools-download.html |
| CDC Social Vulnerability| `cdc_social_vulnerability`       | `census_tract_2018`                   | The social vulnerability by every census tract           | None                                                                                                                                                 | https://svi.cdc.gov/Documents/Data/2018_SVI_Data/SVI2018Documentation.pdf | https://svi.cdc.gov/data-and-tools-download.html |
| UN World Data            | `un`                       | `pop_total`         | world population                               | None | https://data.un.org/_Docs/SYB/PDFs/SYB62_1_201907_Population,%20Surface%20Area%20and%20Density.pdf                                | https://data.un.org/default.aspx                 |
| UN World Data            | `un`                       | `pop_growth`        | world population growth                        | None | https://data.un.org/_Docs/SYB/PDFs/SYB62_246_201907_Population%20growth%20and%20indicators%20of%20fertility%20and%20mortality.pdf | https://data.un.org/default.aspx                 |
| UN World Data            | `un`                       | `pop_distribution`  | world population by city vs rural              | None | https://data.un.org/_Docs/SYB/PDFs/SYB61_253_Population%20Growth%20Rates%20in%20Urban%20areas%20and%20Capital%20cities.pdf        | https://data.un.org/default.aspx                 |
| UN World Data            | `un`                       | `gdp`               | world gdp statistics                           | None | https://data.un.org/_Docs/SYB/PDFs/SYB62_230_201904_GDP%20and%20GDP%20Per%20Capita.pdf                                            | https://data.un.org/default.aspx                 |
| UN World Data            | `un`                       | `gva`               | world gross value add statistics               | None | https://data.un.org/_Docs/SYB/PDFs/SYB62_153_201906_Gross%20value%20added%20by%20kind%20of%20economic%20activity.pdf              | https://data.un.org/default.aspx                 |
| UN World Data            | `un`                       | `health_personnel`  | world health personnel counts                  | None | https://data.un.org/_Docs/SYB/PDFs/SYB62_154_201906_Health%20Personnel.pdf                                                        | https://data.un.org/default.aspx                 |
| UN World Data            | `un`                       | `health_spend`      | world health spending                          | None | https://data.un.org/_Docs/SYB/PDFs/SYB62_325_201906_Expenditure%20on%20Health.pdf                                                 | https://data.un.org/default.aspx                 |

For issues or questions, please submit a pull request, file an issue, or email us!
