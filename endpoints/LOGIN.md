[&laquo; Return to main page](../README.md)

# Login

* Authenticate as a registered user

## `POST` [/login]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
email | string | yes | Registered e-mail address
password | string | yes | Password

### Success Response

Param | Type |  Description
--- | --- | --- 
userId | integer | Newly registered user ID

* Session token will now be authenticated with this user;

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`EMAIL_ADDR_REQ` | E-mail address is required | n/a
`EMAIL_ADDR_INVALID` | Invalid e-mail address | n/a
`EMAIL_ADDR_UNREG` | E-mail address is not registered | n/a
`PASSWORD_REQ` | Password is required | n/a
`PASSWORD_INCORRECT` | Incorrect password | n/a
`USER_STATUS_DISABLED` | User account is DISABLED | n/a 

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).