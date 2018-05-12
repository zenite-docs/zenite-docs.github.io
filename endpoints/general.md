# General configuration

> (server) > Endpoints > (endpoint) > General

## Endpoint name

Choose an endpoint name to access your endpoint. This will affect your endpoint URL, for example, endpoint named "users" will have an URL in the format:

```
https://your-server-name.zenite.io/users
```

## Options

### Endpoint enabled

Check or uncheck this option to enable or disable your endpoint. Disabled endpoints will return the following error:

```json
{
    "error": "Endpoint is disabled.",
    "status": 400
}
```

### Return error message text on internal endpoint errors

If this option is checked, endpoints will return descriptive JSON body on internal endpoint errors (for example, when the endpoint is disabled like in the above example) along with the corresponding HTTP status code.

The endpoint errors are returned in the following format:

```json
{
    "error": "(error message)",
    "status": (error code)
}
```

If this option is unchecked, an empty body will be returned along with the corresponding HTTP status code.

### HTTP method

Choose a HTTP method to access your endpoint. This will affect how you access your endpoint and how you pass the the database query parameters.

For more information on passing database query parameters, visit [Query parameter mapping](endpoints/mapping.md).