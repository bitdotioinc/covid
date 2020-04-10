There is API for the tables listed in README.md and shown on https://bit.io/covid. You can `GET` them via:
```
https://covid-api.bit.io/[table_name]
```
Important: You MUST set the `Accept-Profile` header in your request with the schema name (i.e., `Accept-Profile: [schema_name]`)

For example, to query the `ecdc` schema and it `counts` table:
```
curl -H "Accept-Profile: ecdc" https://covid-api.bit.io/counts
```

## Notes ##
* Read only 
* This is in testing mode. Please email covid@bit.io if you have an issue or make a GitHub issue
