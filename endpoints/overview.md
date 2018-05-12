# Overview

endpoints are basic REST API definitions that allow users to access or modify the database through defined database query. Data is secured using HTTPS and JWT authentication. The endpoint host is running on the database server.

The endpoint has the following format:

```
https://your-server-name.zenite.io/your-endpoint-name
```

Data can be passed to the endpoint as query or body (JSON) parameters, for GET or POST requests respectively. For more info on passing parameters to endpoints, read [General configuration](endpoints/general.md) and [Query parameter mapping](endpoints/mapping).