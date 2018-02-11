# Database query

> Navigation: server.zenite.io > Endpoints > your-endpoint-name > Database query

Configure the query that will be used to access or modify your database data.

1. Choose a database from the drop-down on which the query will be executed.
2. Write your query, for example:

```sql
SELECT * FROM Users
```

You can pass parameters to your database query from the HTTP request parameters.

## Query parameter mapping

The request query parameters are mapped to database query parameters by prefixing a $ (a dollar symbol), such as $name. You can use these variables directly in the query, as described below.

### Database query parameters

In this example, the URL parameter "name" maps to the SQL/MongoDB query as $name, and parameter "age" maps to SQL/MongoDB query as $age, such as:

##### MariaDB / PostgreSQL

```sql
SELECT * FROM Users WHERE name = $name AND age = $age
```

##### MongoDB
```javascript
db.users.find({ $and: [{ name: $name }, { age: $age }] })
```

You can issue a GET or POST request (as configured in the [General configuration](endpoints/general.md)) to execute the query and return the result (in JSON format).

### Request query parameters

##### GET

GET requests will read database query parameters from the URL query parameters, for example:
```
https://your-server-name.zenite.io/users?name=John&age=30
```

##### POST

POST requests will read database query parameters from a JSON object in the request body, for example:

```json
{
    "name": "John",
    "age": 30
}
```

## Response format

The response is returned in a JSON format described below.

##### MariaDB / PostgreSQL

Row results:
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
        ]
    }
]
```

Non-row or error results:
```json
[
    {
        "message": "(result or error message)"
    }
]
```

##### MongoDB

MongoDB queries are returned in the exact format the MongoDB shell would print the result. To ensure the response can be deserialized to JSON format, please ensure that your query returns valid JSON.