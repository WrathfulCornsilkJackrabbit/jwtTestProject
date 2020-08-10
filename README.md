# jwtTestProject

## Instalation

[postman](https://www.postman.com/downloads/)

## Project configuration

1. Create a `.env` file in the rood directory
2. Declare a `ACCESS_TOKEN_SECRET` and `REFRESH_TOKEN_SECRET` variables in `.env`
3. Generate a secret string:

```bash
node
```

then

```bash
require('crypto').randomBytes(64).toString('hex')
```

Assign the result string value to the `ACCESS_TOKEN_SECRET` and do the same thing for the `REFRESH_TOKEN_SECRET`.

## How to run the project

### Backend running

Run the Data server

```bash
node run devStart
```

Run the Auth server

```bash
node run devStartAuth
```

### Get user posts

1. Create a new `POST` request on postman to `http://127.0.0.1:4000/login`

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

4. Press send. Should return the `access token` and the `refresh token`:

```json
{
  "accessToken": "<Access token here :D>",
  "refreshToken": "<Refresh token here :D>"
}
```

5. Currently the token is valid for 60 seconds. After that both `access` and `refresh tokens` will be invalid.

6. Create a new `POST` request on postman to `http://127.0.0.1:4000/token`

7. On `Headers` add:

```
KEY: Content-Type
```

```
VALUE: application/json
```

```
DESCRIPTION: <No description needed>
```

8. On `Body` -> `raw` add:

```json
{
  "token": "<Place your refresh token here>"
}
```

7. Press send. If `refresh token` was older than 60 seconds, it will return `403 Forbidden`. Should return the `access token`:

```json
{
  "accessToken": "<Access token here :D>"
}
```

8. Create a new `GET` request on postman to `http://127.0.0.1:4000/token`

9. On `Headers` add:

```
KEY: Authorization
```

```
VALUE: Bearer <Access token here :D>
```

```
DESCRIPTION: <No description needed>
```

7. Press send. If `refresh token` was older than 60 seconds, it will return `403 Forbidden`. Should return the actual post title of that user:

```json
[
  {
    "username": "Kyle",
    "title": "Post 1"
  }
]
```
