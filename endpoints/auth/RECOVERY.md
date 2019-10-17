[&laquo; Return to main page](../../README.md)

# Account Recovery Setup

* Account recovery setup

## `GET`  [/auth/recovery]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
country | string | Currently select country code for recovery phone
phone | string/NULL | Phone number without country code prefix

### Errors

Code | Description| Possible Resolution
--- | --- | ---

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/recovery?send_sms]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
country | string | yes | ISO 3166-1 (Alpha-3) user selected country code; Form should pre-select currently selected OR  user's country from profile BUT IT IS POSSIBLE TO SELECT OTHER COUNTRY;
phone | string/integer | yes | Phone/mobile number to send SMS code to, without country code/prefix

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`COUNTRY_INVALID` | Country code is invalid or not one of the listed countries | n/a
`PHONE_REQ` | Phone number is required | n/a
`PHONE_INVALID` | Phone number is in invalid format | n/a
`PHONE_SAME` | Phone number is same as currently set one | n/a
`SMS_SEND_FAIL` | Failed to send SMS code | n/a

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/recovery?verify]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
code | string | yes | 8 digit SMS verification code (alphanumeric)

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`SMS_CODE_REQ` | SMS verification code is required | n/a
`SMS_CODE_BAD` | SMS verification code is invalid or incorrect | n/a

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---