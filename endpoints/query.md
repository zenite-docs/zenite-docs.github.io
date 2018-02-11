# Database query

> Navigation: server.zenite.io > Endpoints > endpoint-name > Database query

Configure the query that will be used to access or modify your database data.

1. Choose a database from the drop-down on which the query will be executed.
2. Write your query, for example:

```sql
SELECT * FROM Users
```

You can pass parameters to your database query from the HTTP request parameters.

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