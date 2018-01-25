# Create an endpoint

## Overview

endpoints are basic API definitions that allow users to access or modify the database data through HTTPS using JWT authentication. The endpoint host is running on the database server.

The endpoint has the following format:

https://server.zenite.io/myendpoint

Data can be passed to the endpoint as query (for GET) or body (for POST) parameters, for example:

#### GET
```
URL: https://server.zenite.io/myendpoint?firstname=John
```

#### POST
```
URL: https://server.zenite.io/myendpoint
Body: { "firstname": "John" }
```

The parameter firstname maps to the SQL query as $firstname, such as:

```sql
SELECT * FROM Users WHERE firstname = $firstname
```

In this example, URL will return all users named John in JSON format.
