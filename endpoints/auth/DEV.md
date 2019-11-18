[&laquo; Return to main page](../../README.md)

# Development / Developers Tools

* Setup a "Shared encryption secret" for wallet API service

---

## `GET`  [/auth/dev?ses]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
sharedEncryptionSecret | string / NULL | Current "shared encryption secret" (if set) otherwise NULL

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/dev?ses]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
newSecret | string | yes | New shared encryption secret

### Success Response

Param | Type |  Description
--- | --- | --- 
newSecret | string | New encryption secret (should be same as req param unless whitespaces are trimmed)

### Errors

Code | Description| Possible Resolution
--- | --- | ---
SES_REQ | Param "newSecret" is required | n/a
SES_INVALID | New shared secret value contains an illegal character | Allowed are alphanumeric digits (`a-z0-9`), `spaces` and `-._$!#@` ; Note that spaces at start or end of the string are trimmed
SES_LEN | Length of new encryption secret must be between 8 and 32 bytes | n/a
SES_SAME | New and existing SES values are the same | n/a

* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).