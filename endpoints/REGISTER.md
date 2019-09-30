[&laquo; Return to main page](../README.md)

# Registration

* Registers a new user account

## `POST` [/register]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
firstName | string | yes | User first name,  **UTF8MB4 supported**
lastName | string | yes | User last name,  **UTF8MB4 supported**
email | string | yes | Valid e-mail address
country | string | yes | ISO 3166-1 (Alpha-3) country code; See [Countries](COUNTRIES.md) endpoint;

### Success Response

Param | Type |  Description
--- | --- | --- 
userId | integer | Newly registered user ID

* Session token will now be authenticated with this user;

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`FIRST_NAME_LEN` | Length issue with First name | Valid values must be between 3-16 chars (**utf8mb4** charset)
`FIRST_NAME_INVALID` | First name param contains an illegal character or is invalid | n/a
`LAST_NAME_LEN` | Length issue with Last name | Valid values must be between 3-16 chars (**utf8mb4** charset)
`LAST_NAME_INVALID` | Last name param contains an illegal character or is invalid | n/a
`EMAIL_ADDR_INVALID` | Invalid e-mail address | n/a
`COUNTRY_INVALID` | Country code is invalid or not one of the listed countries | n/a

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).