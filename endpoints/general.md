# General configuration

### Endpoint name

Choose an endpoint name to access your endpoint. This will affect your endpoint URL, for example, endpoint named "users" will have an URL in the format:

```
https://your-server-name.zenite.io/users
```

### Options

##### Endpoint enabled

Check or uncheck this option to enable or disable your endpoint. Disabled endpoints will return the following error:

```json
{
    "error": "Endpoint is disabled.",
    "status": 400
}
```

##### Return error message text on failed HTTP requests

If this option is checked, endpoints will return descriptive JSON body on why the request failed (for example, when the endpoint is disabled like in the above example) along with the corresponding HTTP status code.

If this option is unchecked, an empty body will be returned along with the corresponding HTTP status code.

### HTTP method

Choose a HTTP method to access your endpoint.

#### GET

GET requests will receive database query parameters as URL query parameters, for example:

```
https://your-server-name.zenite.io/users?name=John&age=30
```

#### POST

POST request will receive database query parameters as JSON object, for example:

```json
{
    "name": "John",
    "age": 30
}
```

### Query parameter mapping

The URL parameter **name** maps to the SQL/MongoDB query as **$name**, and parameter **age** maps to SQL/MongoDB query as **$age**, such as:

#### MariaDB / PostgreSQL
```sql
SELECT * FROM Users WHERE name = $name AND age = $age
```

#### MongoDB
```javascript
db.users.find({ $and: [{ name: $name }, { age: $age }] })

```

In this example, URL will return all users named John aged 30 years, in JSON format.