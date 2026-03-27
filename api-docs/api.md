# Login API Documentation

## Overview
The Login API is used to authenticate users and generate an access token.  
This token can be used to access protected resources in the system.

---

## Endpoint
POST /api/login

---

## Base URL
https://example.com

---

## Headers

| Key          | Value              |
|--------------|--------------------|
| Content-Type | application/json   |

---

## Request Body

The request body must be sent in JSON format.

```json
{
  "email": "user@example.com",
  "password": "123456"
}
```

## Success Response
### Status Code: 200 OK

This response is returned when the user provides valid credentials.

``` json
{
  "status": "success",
  "token": "abc123xyz"
}
```
## Response Fields

| Field    | Type    | Response                      |
|----------|---------|-------------------------------|
| status   | string  | Indicates success of request  |
| token    | string  | Authentication token for user |

## Error Responses
### 400 Bad Request
``` json
{
  "error": "Missing email or password"
}
```

### 401 Unauthorized
Returned when the provided credentials are incorrect.

``` json
{
  "error": "Invalid email or password"
}
```
### 500 Internal Server Error
Returned when something fails on the server side

``` json
{
  "error": "Internal server error"
}
```
### Example Request (cURL)

``` bash
curl -X POST https://example.com/api/login \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "123456"
}'
```
## Notes
- Ensure the email is in a valid format
- Password is case-sensitive
- Keep the token secure after login
- Use HTTPS for all API requests

## Conclusion

> This API enables secure user authentication by validating credentials and returning an access token for further interactions. 
