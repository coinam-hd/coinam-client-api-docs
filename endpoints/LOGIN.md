[&laquo; Return to main page](../README.md)

# Login

* Authenticate as a registered user

### Recommended Flow:

* Show login form with e-mail address and password fields.

## `POST` [/login]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
email | string | yes | Registered e-mail address
password | string | yes | Password
reCaptchaRes | string | no | If `GET /session` indicates that reCaptcha is required (`reCaptcha.required` is `TRUE`) then send reCaptcha response in this param

### Success Response

Param | Type |  Description
--- | --- | --- 
userId | integer | Authenticated user ID

* Session token will now be authenticated with this user;
* Users will have to verify TOTP code once

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`EMAIL_ADDR_REQ` | E-mail address is required | n/a
`EMAIL_ADDR_INVALID` | Invalid e-mail address | n/a
`EMAIL_ADDR_UNREG` | E-mail address is not registered | n/a
`PASSWORD_REQ` | Password is required | n/a
`PASSWORD_INCORRECT` | Incorrect password | n/a
`USER_STATUS_DISABLED` | User account is DISABLED | n/a 

* Check [**2FA Error Messages**](../README.md#2fa-error-messages).  
* It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).
