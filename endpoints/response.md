# Response format

The response is returned in a JSON format described below.

## MariaDB / PostgreSQL

The request result is an array of objects.

### Row results
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

### Non-row or error results
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

If the query returned an error, the "message" field will contain the error message, and the "code" field will be a negative integer (-1).

## MongoDB

MongoDB queries are returned in the exact format the MongoDB shell would print the result. To ensure the response can be deserialized to JSON format, please ensure that your query returns valid JSON using `JSON.stringify()`, for example:

```javascript
JSON.stringify(db.getCollection('collection').find({}).toArray());
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