# **IN PROGRESS**

First you need send a `POST` request to `/api/v2/auth/login` which should return the API key which will be needed for all future requests. This will be changed eventually to a JWT so make sure to check the response. The response should also contain the header `x-medusa-server` with a value of the current install version. If this header is missing the server is out of date or isn't actually a Medusa install, this can happen if the user provides an incorrect server address.

Once you have the API key you should save it securely as it can be used to change and access all server settings. The API key should be sent to all new requests via the `x-api-key` header or if needed via the `api_key` query string.

Medusa supports the `OPTIONS` method to return all allowed methods on a route. CORS is also enabled on all `/api/v2` routes.