# WSA (Web Security Analyzer)
WSA (Web Security Analyzer)

WSA is an application to scan a website that aims to find security holes. this is only for documentation API in WSA.
- Admin
- Guests

## Environment
- hercule
- fury
- apiary

## Running
`hercule blueprint/blueprint.apib -o apiary.apib && fury --validate apiary.apib && apiary preview --server --port=8090`

## Basic Flow

### Explanations
1. Admin is role for maintaining all permissions
2. Guests is role for scanning website vulnerabilities

## Authentication
The API uses oAuth2 to authenticate, meaning all access to an API that has authentication must have a header like the following:
```
Authorization: Bearer API_KEY_HERE
```
look this [documentation](https://oauth.net/2/grant-types/password/) Authentication to find out how to get an access token

## Headers
Make sure you have the following content type headers set on each request:
```
Content-Type: application/json
```

## Allowed HTTPs requests:
- `POST` : To create resource
- `PUT/PATCH` : Update resource
- `GET` : Get a resource or list of resources
- `DELETE` : To delete resource

### Status codes
| Status code   | Description  |
|---|---|
| 200  | Success  |
| 400 | Validation error: An accompanying error message will explain further |
| 401  | Authentication error: The oAuth credentials were missing, incorrect or expired  |
| 403  | Authentication error: The current authenticated user has no access to this resource  |
| 404  | Invalid endpoint: The endpoint requested is invalid or the resource requested, such as a meter, does not exists.   |
| 405  | The HTTP method used for this endpoint is invalid. |
| 5xx  | An error has occurred within Metry.io and the request couldn’t be completed. Metry.io has been notified about the problem |
| 503 | We're experiencing temporary server issues. Please try again |