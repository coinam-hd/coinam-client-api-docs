[&laquo; Return to main page](../../../README.md)

# Available Crypto-currencies

* In backend on Login event, a list is generated for crypto-currencies available to this user
* Ideally, request to this endpoint should be made only ONCE and list can be stored in local / frontend app level storage
* Use this list to generate navigation menus
* List is destroyed in backend when a user logs out

## `GET`  [/auth/crypto/available_coins]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
count | integer | Number of coins available to users
coins | array | Indexed array of Coin objects. (See [**`object` Coin**](../../../models/COINS.md)).

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../../README.md#global-error-messages).