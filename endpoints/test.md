# Test

> (server) > Endpoints > (endpoint) > Test

You can test your endpoint directly from the web interface. If you are using CORS, make sure you have added `https://portal.zenite.io` to the list of allowed origins before you execute the test.

Please note that the test will affect your database data as it normally would be affected if the endpoint was accessed normally.

## GET

Click `GET`. The response will be displayed as formatted JSON.

## POST

Enter the POST parameters, for example:

```json
{
    "name": "John",
    "age": 30
}
```

Click `POST`. The response will be displayed as formatted JSON.