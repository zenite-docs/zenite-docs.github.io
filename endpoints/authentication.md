# Authentication

> Navigation: server.zenite.io > Endpoints > your-endpoint-name > Authentication

Endpoints are authorized using JSON Web Tokens (JWT). For more information, check the official JWT site:

https://jwt.io/

### Modes

##### Anonymous authentication

Anonymous authentication disables the authentication and allows any client to execute a query configured in the endpoint. This mode is not recommended in production environments since it opens up the endpoint to the public and can lead to unintentional security leaks. Use with caution and only for reading the data.

##### JWT Bearer Token

JWT Bearer Token enables the default authentication mode using JWT Bearer Token. To authorize an endpoint HTTP request, use an Authorization header with the Bearer token generated in the input field:

```
Authorization: Bearer <token>
```

To generate a new token, click "Generate new Token". This will generate a completely new access token and invalidate any existing tokens.

Save the settings by clicking "Save".