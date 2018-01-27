# Overview

endpoints are basic API definitions that allow users to access or modify the database data through HTTPS using JWT authentication. The endpoint host is running on the database server.

The endpoint has the following format:

https://server.zenite.io/getusers

Data can be passed to the endpoint as query (for GET) or body (for POST) parameters, for example:

#### GET
```javascript
URL: https://server.zenite.io/getusers?firstname=John
```

#### POST
```javascript
URL: https://server.zenite.io/getusers
Body (JSON): { "firstname": "John" }
```

The URL parameter **firstname** maps to the SQL query as **$firstname**, such as:

#### MariaDB / PostgreSQL
```sql
SELECT * FROM Users WHERE firstname = $firstname
```

#### MongoDB
```javascript
db.users.find({ firstname: $firstname })
```

In this example, URL will return all users named John in JSON format.