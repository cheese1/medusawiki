# **IN PROGRESS**

First you need send a POST request to /api/v2/auth/login and you should get an a response back containing the apiKey which will be needed for all future requests. This will be changed eventually to a JWT so make sure to check the response. The response should also contain the header `x-medusa-server` with a value of the current install version. If this header is missing the server is out of date or isn't actually a Medusa install, this can happen if the user provides an incorrect server address.

Once you have the apiKey you should save it securely as it can be used to change and access all server settings. The apiKey should be sent to all new requests via the `x-api-key` header or if needed via the `apiKey` query string.

Medusa supports the OPTIONS method to return all allowed methods on a route. CORS is also enabled on all `/api/v2` routes.