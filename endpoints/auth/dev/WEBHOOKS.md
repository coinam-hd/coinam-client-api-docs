[&laquo; Return to main page](../../../README.md)

# Web Hooks

* List all existing web hooks entries
* Create a web hook
* Modify a web hook
* Delete a web hook

## List all web hooks
##### `GET`  [/auth/dev/web_hooks]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
webHooks | array | Indexed array of `WebHook` objects. (See [**`object` WebHook**](../../../models/CRYPTO.md#object-webhook)).

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../../README.md#global-error-messages).

---

## Create new OR modify existing web hook
##### `POST`  [/auth/dev/web_hooks?setup]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
webHookId | int | **depends** | If this parameter is not sent, a NEW web hook will be created as result
method | string | yes | Can be either of "GET" or "POST"
url | string | yes | URL starting with "http://" or "https://"
verifySSL | int | yes | Send 1 for TRUE otherwise FALSE
httpAuthUsername | string | no | If URL is protected with Basic HTTP auth. send username otherwise blank
httpAuthPassword | string | no | If URL is protected with Basic HTTP auth. send password otherwise blank

### Success Response

Param | Type |  Description
--- | --- | --- 
webHook | object | See [**`object` WebHook**](../../../models/CRYPTO.md#object-webhook)
newWebHookId | int | This param is only sent when a new web hook was added

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`WEBHOOK_NOT_FOUND` | Web hook not found in user account | n/a
`INVALID_HTTP_METHOD` |  Invalid HTTP method | Send a method "GET" or "POST"
`URL_REQ` | URL param is required | n/a
`URL_LEN` | URL length exceeds 128 bytes | n/a
`URL_INVALID` | Invalid URL | Send a valid URL starting with "http://" or "https://"
`AUTH_USER_LEN` | HTTP auth username exceeds 40 bytes | n/a
`AUTH_USER_INVALID` | HTTP auth username contains an illegal char | n/a
`AUTH_PASS_LEN` | HTTP auth username exceeds 40 bytes | n/a
`AUTH_PASS_INVALID` | HTTP auth username contains an illegal char | n/a
`WEBHOOKS_HARD_LIMIT` | User has reached limit for web hooks | Cannot add new web hooks

* It is also possible to get one of [**Global Error Messages**](../../../README.md#global-error-messages).


---

## Delete a web hook
##### `DELETE`  [/auth/dev/web_hooks]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
webHookId | int | yes | Web hook ID to delete

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`WEBHOOK_ID_REQ` | Param "webHookId" is required | n/a

* It is also possible to get one of [**Global Error Messages**](../../../README.md#global-error-messages).