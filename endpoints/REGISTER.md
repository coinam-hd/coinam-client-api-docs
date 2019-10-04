[&laquo; Return to main page](../README.md)

# Registration

* Registers a new user account

## `POST` [/register]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
firstName | string | yes | User first name
lastName | string | yes | User last name
email | string | yes | Valid e-mail address
country | string | yes | ISO 3166-1 (Alpha-3) country code; See [Countries](COUNTRIES.md) endpoint;
password | string | yes | Expects alphanumeric string with special characters
confirmPassword | string | yes | Expects user to retype same password
terms | string/integer | yes | "1" to acknowledge acceptance of terms and other policies

### Success Response

Param | Type |  Description
--- | --- | --- 
userId | integer | Newly registered user ID

* Session token will now be authenticated with this user;

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`ALREADY_LOGGED_IN` | This session is already authenticated with registered user | Redirect away from registration page to dashboard
`FIRST_NAME_REQ` | First name is required | n/a
`FIRST_NAME_LEN` | Length issue with First name | Valid values must be between 3-16 chars
`FIRST_NAME_INVALID` | First name param contains an illegal character or is invalid | n/a
`LAST_NAME_REQ` | Last name is required | n/a
`LAST_NAME_LEN` | Length issue with Last name | Valid values must be between 3-16 chars 
`LAST_NAME_INVALID` | Last name param contains an illegal character or is invalid | n/a
`EMAIL_ADDR_REQ` | E-mail address is required | n/a
`EMAIL_ADDR_INVALID` | Invalid e-mail address | n/a
`EMAIL_ADDR_DUP` | This e-mail address is already registered | Suggest user to login or recover password
`PASSWORD_REQ` | Password field is required | n/a
`PASSWORD_WEAK` | Entered password is weak | Suggest user to use strong password, length should be between 8-32 characters, alphanumeric with special characters
`PASSWORD_INVALID` | Entered password contains an illegal character | n/a
`PASSWORD_MATCH` | Retyped password does not match | n/a
`COUNTRY_INVALID` | Country code is invalid or not one of the listed countries | n/a
`TERMS_UNCHECKED` | User has not acknowledged to TOS | n/a

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).