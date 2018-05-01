# Database query

> (server) > Endpoints > (endpoint) > Database query

Configure the query that will be used to access or modify your database data.

1. Choose a database from the drop-down on which the query will be executed.
2. Write your query, for example:

```sql
SELECT * FROM Users
```

You can pass parameters to your database query from the HTTP request parameters.

The queries configured in an endpoint are executed as a single database transaction.

## Limits

Endpoints and in-application query results are limited to 10000 rows per single request. Any query returning more rows will be executed, but the results will not be visible. Instead, the following will be returned:

```json
{
    "message": "Script executed successfully, but the query returned more than 10000 rows. Please refine your query.",
    "code": -100
}
```