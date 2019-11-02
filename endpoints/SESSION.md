[&laquo; Return to main page](../README.md)

# Session

* Create a new session OR  
* Retrieve all necessary information about existing session;

## `GET` [/session]() *– (Retrieve an existing session)*

### Success Response

Param | Type |  Description
--- | --- | --- 
type | string | Possibly one of "web", "desktop" or "mobile"
xsrf | hash32 | 16 byte XSRF/CSRF token
authUser | NULL/object | If a registered user is authenticated a user object is returned otherwise NULL
reCaptcha | object | ReCaptcha object (see below)
issuedOn | integer | Timestamp when this session was initiated
lastUsedOn | integer | Timestamp when this session was last used

#### `object` reCaptcha

Param | Type |  Description
--- | --- | --- 
required | boolean | if `true` then reCaptcha should be displayed at necessary forms, i.e. login/register; Otherwise there is no need to display reCaptcha
lastVerified | NULL/integer | Timestamp of last reCaptcha validation or NULL
publicKey | NULL/string | ReCaptcha public key or NULL (if none configured)

### Errors

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).

---

## `POST` [/session]() *– (Initialize a new session)*

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
type | string | no | Determined from user-agent for time being; This will change later!

### Success Response

Param | Type |  Description
--- | --- | --- 
token | hash64 | 32 byte token ID in hexadecimal representation; Store this internally or in a cookie for web applications
xsrf | hash32 | 16 byte XSRF token, This **MUST NOT** be stored in a cookie;

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`TOKEN_ALREADY_SUPPLIED` | A valid session token was already supplied in header | No need to use this endpoint
`SESSION_CREATE_ERROR` | Failed to start a new API session | n/a
`SESSION_CREATE_TIMEOUT` | Request new sessions/tokens too fast from same IP address | Possible abuse detected

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).