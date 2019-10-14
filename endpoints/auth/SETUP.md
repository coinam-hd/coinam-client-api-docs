[&laquo; Return to main page](../../README.md)

# Account Setup

* Finalisation of registration / reset account

## `GET`  [/auth/setup]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
suggestedSeed | string | Google 2FA authenticator seed
country | string | ISO 3166-1 (Alpha-3) user selected country code


### Errors

Code | Description| Possible Resolution
--- | --- | ---
SETUP_REDUNDANT | Account setup is redundant; Not necessary; Google 2FA seed is already set | Redirect away to dashboard



It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).