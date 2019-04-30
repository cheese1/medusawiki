# Intro

**Documentation:** [API V2](http://docs.medusaapi.apiary.io/#)

First you need send a `POST` request to `/api/v2/authenticate` to get a JWT token, which will be needed for all future requests. The response should also contain the header `x-medusa-server` with a value of the current install version. If this header is missing the server is out of date or isn't actually a Medusa install, this can happen if the user provides an incorrect server address.

The JWT can be passed with requests using the "Authentication" header. Pass the token as follows: "Authentication": "Bearer [your jwt]".

An alternative way of authenticating is by using the api key. You can retrieve by checking your config.ini. It's stored using the 'api_key' key. It's a static api key. So make sure to store it in a secure place. The API key should be sent to all new requests via the `x-api-key` header or if needed via the `api_key` query string.

Medusa supports the `OPTIONS` method to return all allowed methods on a route. CORS is also enabled on all `/api/v2` routes.


## For developers

### Conventions
* Responses should be json and follow the camelCase convention
* URLs and parameters should be lowercase and use dash-separation convention
* Resources should be nouns (not verbs). Use it in the singular form:

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

## Result filtering, sorting & searching

### Filtering
`GET /ticket?state=open`

### Sorting
`GET /ticket?sort=priority&order=asc`

### Searching
`GET /ticket?q=return&state=open&sort=priority`

### Pagination
The HTTP Response Header should contain a link header for the first, previous, next and last page:

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
* HTTP Response: (Optional) Body of the newly created resource. 
* HTTP Response Header: `Location: http://medusa-server/api/v2/ticket/12`
* Return `HTTP 400 Bad Request` if request is invalid
* Return `HTTP 409 Conflict` if unable to create resource due to a conflict

### PUT
* Idempotent and not Safe
* Return: `HTTP 204 No Content`
* HTTP Response: No content
* Return `HTTP 404 Not Found` if resource doesn't exist
* Return `HTTP 400 Bad Request` resource identifier is invalid

### DELETE
* Idempotent and not Safe
* Return: `HTTP 204 No Content`
* HTTP Response: No body
* Return `HTTP 404 Not Found` if resource doesn't exist
* Return `HTTP 400 Bad Request` resource identifier is invalid

### PATCH
* Return: `HTTP 200 OK`
* HTTP Response: Modified resource fields (only accepted fields)
* Return `HTTP 404 Not Found` if resource doesn't exist
* Return `HTTP 400 Bad Request` resource identifier is invalid
