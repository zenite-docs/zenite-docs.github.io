# Overview

endpoints are basic API definitions that allow users to access or modify the database data through HTTPS using JWT authentication. The endpoint host is running on the database server.

The endpoint has the following format:

https://server.zenite.io/getusers

Data can be passed to the endpoint as query (for GET) or body (for POST) parameters, for example:

#### GET
```
URL: https://server.zenite.io/getusers?firstname=John
```

#### POST
```
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

# Creating a endpoint

1. Click server.zenite.io (your server name).
2. Click "Endpoints".
3. Click "New endpoint...".
4. Choose an endpoint name. This will affect your URL name.
5. Your endpoint is now created. You can configure it by clicking on the item that appeared in the navigation. For instructions on how to configure the endpoint further, read the Endpoint section in the docs.
