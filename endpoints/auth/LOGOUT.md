[&laquo; Return to main page](../../README.md)

# Logout

* Logs out of authenticated session

## `GET` | `POST` | `DELETE` [/auth/logout]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 

* Session is now un-authenticated;

### Errors

Code | Description| Possible Resolution
--- | --- | ---

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).