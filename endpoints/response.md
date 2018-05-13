# Response format

The response is returned in a JSON format described below.

## MariaDB / PostgreSQL

The request result is an array of objects representing the result of the each query configured in the endpoint.

### Row results
```json
[
    /* query 1 result */
    {
        "rows": [
            /* row 1 */
            {
                "(Column 1 Name)": "(Column 1 Value)",
                "(Column 2 Name)": "(Column 2 Value)",
                "(Column 3 Name)": "(Column 3 Value)"
            },
            /* row 2 */
            {
                "(Column 1 Name)": "(Column 1 Value)",
                "(Column 2 Name)": "(Column 2 Value)",
                "(Column 3 Name)": "(Column 3 Value)"
            },
            /* row 3 */
            {
                "(Column 1 Name)": "(Column 1 Value)",
                "(Column 2 Name)": "(Column 2 Value)",
                "(Column 3 Name)": "(Column 3 Value)"
            },
            /* continued rows ... */
        ],
        "code": (code)
    },
    /* continued queries ... */
]
```

For each query, if the query should return rows and was executed successfully, the query result object will contain a field `rows`.

The `rows` field is an array containing row objects, with key-value pairs, where key is the column name and value is the column value for that row.

The `code` field indicates whether the query returned an error. If the query returned an error, `code` will be set to a non-zero value, otherwise it will be set to `0`. Typically, if the query returned any rows, the code will always be set to `0`, otherwise an error message will be contained in the `message` field, as described below.

### Non-row or error results
```json
[
    {
        "message": "(result or error message)",
        "code": (code)
    }
]
```

If the query did not returned any rows (for example, INSERT or UPDATE commands) or returned an error, the result array will contain an object with fields `message` and `code`.

The `message` field contains the string with the result of the query or an error message, and the `code` field indicates if the query executed successfully.

If the query returned an error, the `message` field will contain the error message, and the `code` field will be set to `-1`.

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
If the transaction is executed without errors, the response HTTP status will be `200 (OK)`. If the transaction returns an error, the response HTTP status will be `500 (Internal Server Error)`