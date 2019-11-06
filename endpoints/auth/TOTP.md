[&laquo; Return to main page](../../README.md)

# 2FA/TOTP setup

* Finalisation of registration / reset account
---

## `POST`  [/auth/totp?verify]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
totpCode | string/integer | yes | 6 digit TOTP code; User is suppose to enter code after scanning/enter suggested seed

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* Check [**2FA Error Messages**](../../README.md#2fa-error-messages).  
* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `GET`  [/auth/totp]()

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

* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/totp?save_2fa]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
suggestedSeed | string | yes | TOTP that was suggested by previous `GET` request to same endpoint
totpCode | string/integer | yes | 6 digit TOTP code; User is suppose to enter code after scanning/enter suggested seed

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
SUGGESTED_SEED_REQ | Suggested seed is required | send same suggested seed as scanned/requested as hidden form param
SUGGESTED_SEED_BAD | Suggested seed does not match | User may have refreshed the window, Suggested seed sent with form does not match with latest suggested one

* Check [**2FA Error Messages**](../../README.md#2fa-error-messages).  
* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---