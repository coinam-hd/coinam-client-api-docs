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
phone | string/NULL | Phone number in format +1.234567 (where +1 is dialCode and 234567 is the actual phone number)

### Errors

Code | Description| Possible Resolution
--- | --- | ---

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/recovery?request_code]()

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
`SMS_RESEND_WAIT` | Last SMS code was sent less then 5 minutes ago | Response now contains an object prop "sms"; Look for "retryIn" key in this object which indicates number of seconds before a retry is possible
`SMS_SEND_FAIL` | Failed to send SMS code | n/a

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---

## `POST`  [/auth/recovery?verify_code]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
smsCode | string | yes | 8 digit SMS verification code (alphanumeric)

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`SMS_CODE_REQ` | SMS verification code is required | n/a
`SMS_CODE_BAD` | SMS verification code is invalid or incorrect | n/a
`SMS_CODE_EXP` | SMS verification code has expired; Each code is valid for a small period of 15 minutes only | n/a

It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).

---