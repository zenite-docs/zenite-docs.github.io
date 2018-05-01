# Query parameter mapping

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