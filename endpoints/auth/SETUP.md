[&laquo; Return to main page](../../README.md)

# Account Setup

* Finalisation of registration / reset account

### Errors common on all HTTP methods

Code | Description| Possible Resolution
--- | --- | ---
SETUP_REDUNDANT | Account setup is redundant; Not necessary; Google 2FA seed is already set | Redirect away to dashboard

---

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

Check common errors for this endpoint [**Endpoint common errors codes on all HTTP methods**](#errors-common-on-all-http-methods)
It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/setup?save_2fa]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
suggestedSeed | string | yes | Suggested seed
totpCode | string/integer | yes | 6 digit TOTP code

### Success Response

Param | Type |  Description
--- | --- | --- 
suggestedSeed | string | Google 2FA authenticator seed
country | string | ISO 3166-1 (Alpha-3) user selected country code

### Errors

Code | Description| Possible Resolution
--- | --- | ---
SUGGESTED_SEED_REQ | Suggested seed is required | send same suggested seed as scanned/requested as hidden form param
SUGGESTED_SEED_BAD | Suggested seed does not match | User may have refreshed the window, Suggested seed sent with form does not match with latest suggested one

Check [**2FA Error Messages**](../../README.md#2fa-error-messages).

Check common errors for this endpoint [**Endpoint common errors codes on all HTTP methods**](#errors-common-on-all-http-methods)
It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---