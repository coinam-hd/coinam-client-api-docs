# Coinam Client API Docs

Coinam Client API documentation.

## Basics

**Base URL:** https://api.coinam.com/client/  
**Charset:** All are from **ASCII** (from index 32 to 126), unless other charset is mentioned specifically;  


## Endpoints

├── Endpoints  
│   ├── `GET` [**/init_session**](endpoints/INIT_SESSION.md#get-init_session) *(Initiate a new session)*  
│   ├── `GET` [**/session**](endpoints/SESSION.md) *(Get information about current session)*  
│   ├── `GET` [**/countries**](endpoints/COUNTRIES.md) *(Get list of countries)*  
│   ├── `POST` [**/register**](endpoints/REGISTER.md) *(Signup / Registration of new user)*  
│   └── `POST` [**/login**](endpoints/LOGIN.md) *(Authenticate session as a registered user)*  
│              ├── `GET` [**/auth/logout**](endpoints/auth/LOGOUT.md) *(Clears an authenticated session)*  
│              └── `GET` | `POST` | `DELETE` [**/auth/logout**](endpoints/auth/LOGOUT.md) *(Clears an authenticated session)*
└── 

## XHR Requests

### Headers

Header | Description
--- | ---
Coinam-Client-Token | Required for all endpoints except [**init_session**](endpoints/INIT_SESSION.md#get-init_session) endpoint
Coinam-Client-Timestamp | Timestamp in UTC (GMT+0:00) timezone

* Params can be sent as `application/json` or `application/x-www-form-urlencoded`
* Response is always sent as `application/json; charset=utf8`

## Global Response Params

Param | Type | Description
--- | --- | ---
`status` | boolean | Determines if request was successful; On `false` response object MAY include `error` param
`error` | string | An error message/code, included in response if there is an error; Can sometimes be an empty string or NULL; In such cases it can be reported as "Failed without an error code"
`param` | string/NULL | Indicates which form field/param caused an error, if present, focus should be given to that field/param for better UX

## Global Error Messages

Code | Meaning | Possible Resolution
--- | --- | ---
`API_DISABLED` | Client API is globally disabled | n/a
`API_CONTROLLER_DISABLED` | Requested endpoint/controller is currently disabled | n/a
`INTERNAL_ERROR` | An internal error has occurred | n/a
`PLATFORM_CONFIG_ERROR` | Failed to retrieves platform configuration | n/a
`PLATFORM_ACCESS_ERROR` | Failed to retrieves platform accessibility config | n/a
`DB_CONNECTION_ERROR` | App fails to connect with appropriate API logs database | n/a
`DB_QUERY_ERROR` | DB query critical to execution was failed | n/a
`BAD_REMOTE_ADDR` | App fails to determine remote IP address | n/a
`SESSION_ID_HEADER` | API session id not sent as HTTP request header | Send API session ID
`SESSION_ID_HEADER_INVALID` | API session id sent as header is invalid (does not match hash64) | Send a valid API session ID
`SESSION_NOT_FOUND` | No such API session found with given token (and/or in rare cases IP address) | n/a
`SESSION_RETRIEVE_ERROR` | There was an error while retrieving API session | Discard existing session; Start  a new one
`SESSION_IP_ERROR` | Session was not initiated with current IP address | Discard existing session; Start a new one; **Notify user that their IP address has changed**
`SESSION_CHECKSUM_FAIL` | Session checksum validation has failed | Discard existing session; Start a new one
`XSRF_ERROR` | XSRF/CSRF error | n/a

### Authentication Errors

Code | Meaning | Possible Resolution
--- | --- | ---
`AUTH_NOT_LOGGED_IN` | User is not logged in; Attempting to access authenticated only controller | Redirect users to login screen
`AUTH_USER_RETRIEVE_ERROR` | There was an internal error while retrieving user account | n/a
`AUTH_TOKEN_MISMATCH` | User has logged in again using different device/browser | Redirect user to login screen; **Tell them they have their session has been overridden**
`AUTH_USER_DISABLED` | User account has been DISABLED | n/a