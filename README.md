# covid
Documentation for [bit.io's covid repo](https://bit.io/covid)

__For version and last refreshed information, see `_ingest_version` and `_ingest_timestamp` fields in each table__

| Schema                         | Table                               | Description                                              | Transforms                                                                                                           | Documentation Link                                                                    | Source                                                                                                                 |
|--------------------------------|-------------------------------------|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| `covidtracking`                  | `state_daily`                         | Daily case reports combined from many sources by state   | `pandas.to_datetime` on `date` and `dateChecked`                                                                               | https://covidtracking.com/api/                                                        | https://covidtracking.com/api/states/daily                                                                             |
| `covidtracking`                  | `state_info`                          | Documentation on gathering approach for each state         | None                                                                                                                 | https://covidtracking.com/api/                                                        | https://covidtracking.com/api/states/info                                                                              |
| `covidtracking`                  | `us_daily`                            | Daily case reports combined from many sources for all US | `pandas.to_datetime` on `date` and `dateChecked`                                                                               | https://covidtracking.com/api/                                                        | https://covidtracking.com/api/us/daily                                                                                 |
| `csse_covid_19_data`             | `csse_covid_19_daily_reports`         | JHU daily case reports                                   | Merge `Last Update` and `Last_Update` <br><br> Merge `Longtitude` and `Long_` <br><br> Merge `Latitude` and `Lat` <br><br> `pandas.to_datetime` on `Last_Update` | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_daily_reports                  |
| `csse_covid_19_data`             | `timeseries_covid19_confirmed_global` | JHU aggregate confirmed cases                            | None                                                                                                                     | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| `csse_covid_19_data`             | `timeseries_covid19_deaths_global`    | JHU aggregate confirmed deaths                           | None                                                                                                                     | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| `csse_covid_19_data`             | `timeseries_covid19_recovered_global` | JHU aggregate                                            | None                                                                                                                 | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data             | https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series                    |
| `who_covid_19_situation_reports` | `who_covid_19_sit_rep_time_series`    | WHO confirmed cases                                      | None                                                                                                                 | https://github.com/CSSEGISandData/COVID-19/tree/master/who_covid_19_situation_reports | https://github.com/CSSEGISandData/COVID-19/tree/master/who_covid_19_situation_reports/who_covid_19_sit_rep_time_series |
| `nytimes`                        | `us-counties`                         | NYTimes case data by county                              | `pandas.to_datetime` on `date`                                                                                               | https://github.com/nytimes/covid-19-data                                              | https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-counties.csv                                         |
| `nytimes`                        | `us-states`                           | NYTimes case data by state                               | `pandas.to_datetime` on `date`                                                                                               | https://github.com/nytimes/covid-19-data                                              | https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-states.csv                                           |
| `nextstrain`                     | `metadata`                            | Nextstrain genome metadata                           | replace all `"?"` with `NULL` <br><br> replace `"*-XX"` days in `date` with month only <br><br> `pandas.to_datetime` on `date` and `date_submitted`  | https://github.com/nextstrain/ncov                                                    | https://github.com/nextstrain/ncov/blob/master/data/metadata.tsv                                                       |

For issues or questions, please submit a pull request, file an issue, or email us!