# Initiate Session

* If a session cookie is not set, use this endpoint to request a new session;
* If session cookie is already set, ignore calling this endpoint;
* Sessions are IP address sensitive

## Request

Param | Type | Required | Description
--- | --- | --- | ---
type | string | no | Determined from user-agent for time being; This will change later!

## Success Response

Param | Type |  Description
--- | --- | --- 
token | hash64 | 32 byte token ID in hexadecimal representation; Store this internally or in a cookie for web applications
xsrf | hash32 | 16 byte XSRF token, This **MUST NOT** be stored in a cookie;

## Errors

Code | Description| Possible Resolution
--- | --- | ---
`SESSION_CREATE_ERROR` | Failed to start a new API session | n/a
`SESSION_CREATE_TIMEOUT` | Request new sessions/tokens too fast from same IP address | Possible abuse detected

It is also possible to get one of [**Global Error Messages**](../README.md)