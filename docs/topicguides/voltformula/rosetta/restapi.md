# RestfulAPI()

## Overview

`RestfulAPI` is a generic RESTful API that enables users to interact with any REST endpoint by providing configurable parameters such as the endpoint URL, HTTP method (for example, GET, POST, PUT, DELETE), headers, request body, and additional request parameters. It acts as a flexible interface for making HTTP requests to external services or APIs, enabling seamless integration without being tied to a specific implementation or service.

`RestfulAPI` is a custom formula API that's not a Notes or OpenFormula function. However, it follows the Notes syntax convention when used as a formula.

## Definition

```
export const RestfulAPI = async (
  url: string,
  method = 'GET',
  headers = '{}',
  body: string | null = null,
  additionalRequestParams: string | null = null
): Promise => {...}
```

**Where**:

- `@param {string} url` - The URL of the REST service.
- `@param {string} method` - The HTTP method, like GET, POST, PUT, DELETE.
- `@param {string} headers` - Optional headers to include in the request as a JSON string.
- `@param {string} body` - Optional body for POST, PUT, or PATCH requests as a JSON string.
- `@param {string} additionalRequestParams` - Optional additional request parameters as a JSON string.
- `@returns {Promise}` - A promise that resolves to the response data or rejects with an error.

## Example

**To call the DRAPI REST API to authorize and return a bearer token**

```
const authUrl = 'https://keep-server/api/v1/auth';\ const authHeaders = '{ "accept": "application/json", "Content-Type": "application/json" }';
let authBody = '{ "username": "abc", "password": "xyz" }';

const authResponse = await RestfulAPI(authUrl, 'POST', authHeaders, authBody);
```

**To call the DRAPI REST API to retrieve a list of views and forms from a database**

!!! note

    In this example, the used database is the *testdiscussions* database.

```
const apiUrl = 'https://keep-server/api/v1/lists?type=all&dataSource=testdiscussions';\ const apiHeaders = '{ "Authorization": "Bearer ' + authResponse.bearer + '" }';

const apiResponse = await rosetta.restfulAPI(apiUrl, 'GET', apiHeaders);
console.log(apiResponse);
```

## Restrictions

- The `RestfulAPI` doesn't automatically refresh authorization tokens when they expire.
- Converters field handling within parameters must be disabled in the configuration settings to allow response values, such as the bearer token, to be used in subsequent calls.
- Setting a string value for the `headers`, `body`, and `additionalRequestParams` must follow a specific convention. The outer quote characters are single quotes and the inner quote characters are double quotes.
