# API #
There is a REST API for the tables listed in [README.md](README.md) and shown on [bit.io/covid](https://bit.io/covid). You can `GET` them via:
```
https://covid-api.bit.io/[table_name]
```
IMPORTANT: You MUST set the `Accept-Profile` header with the schema name (i.e., `Accept-Profile: [schema_name]`)

For example, to query the `ecdc` schema and the `counts` table:
```
curl -H "Accept-Profile: ecdc" https://covid-api.bit.io/counts
```

To filter columns, follow the syntax at http://postgrest.org/en/v6.0/api.html#vertical-filtering-columns

To filter rows, follow the syntax at http://postgrest.org/en/v6.0/api.html#horizontal-filtering-rows

To get the OpenAPI spec for each schema, visit the root https://covid-api.bit.io/ with the `Accept-Profile` header set to the schema name

## Notes ##
* Read only 
* This API is in beta. If you have an questions, need help, or get errors, please email covid@bit.io  or make a GitHub issue.
