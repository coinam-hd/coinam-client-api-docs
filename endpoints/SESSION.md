[&laquo; Return to main page](../README.md)

# Session Info

* Retrieves all necessary information about current session;

## `GET` [/session]()

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