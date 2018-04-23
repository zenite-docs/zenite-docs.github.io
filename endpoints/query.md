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

## Query parameter mapping

The request query parameters are mapped to the database query parameters by prefixing a $ (a dollar symbol), such as:

| Request query parameter | Database parameter  |
| ----------------------- | ------------------- |
| name                    | $name               |
| age                     | $age                |

You can use these database parameters directly in the query, as described below.

### Request query parameters

##### GET

GET requests will map to the database query parameters from the URL query parameters, for example:
```
https://your-server-name.zenite.io/users?name=John&age=30
```

##### POST

POST requests will map to the database query parameters from a JSON object in the request body, for example:

```json
{
    "name": "John",
    "age": 30
}
```

### Database query parameters

Database query parameters are read directly from the request query parameters:

##### MariaDB / PostgreSQL

```sql
SELECT * FROM Users WHERE name = $name AND age = $age
```

##### MongoDB
```javascript
db.users.find({ $and: [{ name: $name }, { age: $age }] })
```

You can issue a GET or POST request (as configured in the [General configuration](endpoints/general.md)) to execute the query and return the result (in JSON format).

## Response format

The response is returned in a JSON format described below.

##### MariaDB / PostgreSQL

The request result is an array of objects.

###### Row results
```json
[
    {
        "rows": [
            [
                "Row 1, Column Value 1",
                "Row 1, Column Value 2",
                "Row 1, Column Value 3",
            ],
            [
                "Row 2, Column Value 1",
                "Row 2, Column Value 2",
                "Row 2, Column Value 3",
            ]
        ],
        "code": (code)
    }
]
```

If the query returned any rows, the result array will contain an object with fields "rows" and "code".

The "rows" field is an array containing column values (per row), and the "code" field indicates if the query returned an error (if the query returned any results, the code will be 0).

###### Non-row or error results
```json
[
    {
        "message": "(result or error message)",
        "code": (code)
    }
]
```

If the query did not returned any rows (for example, INSERT or UPDATE commands), the result array will contain an object with fields "message" and "code".

The "message" field contains the string with the result of the query, and the "code" field indicates if the query executed successfully.

If the query returned an error, the "message" field will contain the error message, and the "code" field will be a negative integer (typically -1).

##### MongoDB

MongoDB queries are returned in the exact format the MongoDB shell would print the result. To ensure the response can be deserialized to JSON format, please ensure that your query returns valid JSON using `JSON.stringify()`, for example:

```json
JSON.stringify(db.getCollection('collection').find({}).toArray())
```

If an error or a message is returned, it will have the following format:

```json
{
    "message": "(error or info message)",
    "code": (error or info code)
}
```

## Response HTTP statuses
If the transaction is executed without errors, the response HTTP status will be 200 (OK). If the transaction returns an error, the response HTTP status will be 500 (Internal Server Error)

## Limits

Endpoints and in-application query results are limited to 10000 rows per single request. Any query returning more rows will be executed, but the results will not be visible. Instead, the following will be returned:

```json
{
    "message": "Script executed successfully, but the query returned more than 10000 rows. Please refine your query.",
    "code": -100
}
```