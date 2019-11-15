[&laquo; Return to main page](../../../README.md)

# Wallets

* List all existing wallets
* Create a new wallet

## List all wallets
##### `GET`  [/auth/crypto/wallets]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
coin | string | yes | Crypto-currency code (2-8 alphanumeric digits)

### Success Response

Param | Type |  Description
--- | --- | --- 
count | integer | Number of coins available to users
coin | **`object` Coin**](../../../models/CRYPTO.md#object-coin) | Coin object
wallets | array | Indexed array of `Wallet` objects. (See [**`object` Wallet**](../../../models/CRYPTO.md#object-wallet)).

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../../README.md#global-error-messages).