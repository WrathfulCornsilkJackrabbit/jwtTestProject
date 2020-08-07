# jwtTestProject

## Instalation

### postman

## Run project

### Project configuration

1. Create a `.env` file in the rood directory
2. Declare a `ACCESS_TOKEN_SECRET` variable in `.env`
3. Generate a secret string:

```bash
node
```

then

```bash
require('crypto').randomBytes(64).toString('hex')
```

Assign the result string value to the `ACCESS_TOKEN_SECRET`

### Make a request through postman

Let's do an example for the login.

1. Create a new `POST` request on postman to `http://127.0.0.1:3000/login`
2. On `Headers` add:

```
KEY: Content-Type
```

```
VALUE: application/json
```

```
DESCRIPTION: <No description needed>
```

3. On `Body` -> `raw` add:

```json
{
  "username": "Kyle"
}
```

4. Press send. Should return the access token:

```json
{
  "accessToken": "<Access token here :D>"
}
```
