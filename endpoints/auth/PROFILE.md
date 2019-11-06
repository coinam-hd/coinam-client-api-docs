[&laquo; Return to main page](../../README.md)

# Account Profile

* Account profile & e-mail verification methods

## `GET`  [/auth/profile]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/profile?request_verify_email]()

* Resend verification e-mail code

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/profile?verify_email]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
code | string | yes | E-mail verification code

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`VERIFY_CODE_REQ` | E-mail verification code is required | n/a
`VERIFY_CODE_BAD` | SMS verification code is invalid or incorrect | n/a

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---