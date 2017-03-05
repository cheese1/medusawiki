# **IN PROGRESS**

First you need send a `POST` request to `/api/v2/auth/login` which should return the API key which will be needed for all future requests. This will be changed eventually to a JWT so make sure to check the response. The response should also contain the header `x-medusa-server` with a value of the current install version. If this header is missing the server is out of date or isn't actually a Medusa install, this can happen if the user provides an incorrect server address.

Once you have the API key you should save it securely as it can be used to change and access all server settings. The API key should be sent to all new requests via the `x-api-key` header or if needed via the `api_key` query string.

Medusa supports the `OPTIONS` method to return all allowed methods on a route. CORS is also enabled on all `/api/v2` routes.

## Conventions

Resources should be nouns (not verbs). Use it in the singular form:

```
GET /ticket - Retrieves a list of tickets
GET /ticket/12 - Retrieves a specific ticket
POST /ticket - Creates a new ticket
PUT /ticket/12 - Updates ticket #12
PATCH /ticket/12 - Partially updates ticket #12
DELETE /ticket/12 - Deletes ticket #12
```
```
GET /ticket/12/message - Retrieves list of messages for ticket #12
GET /ticket/12/message/5 - Retrieves message #5 for ticket #12
POST /ticket/12/message - Creates a new message in ticket #12
PUT /ticket/12/message/5 - Updates message #5 for ticket #12
PATCH /ticket/12/message/5 - Partially updates message #5 for ticket #12
DELETE /ticket/12/message/5 - Deletes message #5 for ticket #12
```
Responses should be json and follow the camelCase convention

## Result filtering, sorting & searching

### Filtering
`GET /ticket?state=open`

### Sorting
`GET /ticket?sort=-priority`

### Searching
`GET /ticket?q=return&state=open&sort=-priority,created_at`

### Pagination
The HTTP Response Header should contain a link header for the previous and next page:

`Link: <https://api.github.com/user/repos?page=3&per_page=100>; rel="next", <https://api.github.com/user/repos?page=50&per_page=100>; rel="last"`


### GET
* Idempotent and Safe
* Return: `HTTP 200 OK`
* HTTP Response: resource (json format)
* HTTP Response Header: `Etag: "a48092717311c68fe766a46458e0a0a35f3817ba"`
* Return `HTTP 404 Not Found` if resource doesn't exist
* Return `HTTP 400 Bad Request` resource identifier is invalid


### POST
* Return: `HTTP 201 Created`
* HTTP Response: No body
* HTTP Response Header: `Location: http://medusa-server/api/v2/ticket/12`


### PUT
* Idempotent and not Safe
* Return: `HTTP 200`
* HTTP Response: resource (json format)

### DELETE
* Idempotent and not Safe
* Return: `HTTP 204 No Content`
* HTTP Response: No body

### PATCH
* Return: `HTTP 200`
* HTTP Response: resource (json format)

## Other status
* `400 Bad Request`
* `404 Not Found (GET, PUT, PATCH)`

### JSON
All json properties should be camelCase

TODO: ETag, Last-Modified...