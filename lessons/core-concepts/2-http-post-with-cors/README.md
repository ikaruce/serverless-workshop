# Deploying an http POST endpoint with CORS support

This lesson will walk you through creating a basic http functions triggered by a http POST endpoint with CORS support.

`cors` is needed for interacting with service endpoints from frontend applications

## Steps

1. First write your code in `handler.js`
2. Then `sls deploy`
3. Then update `serverless.yml` with the http event
4. Then deploy again

Run `sls info` in your terminal to get your live endpoint information