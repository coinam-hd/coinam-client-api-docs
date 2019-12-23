## Retrieve List of Addresses
##### `GET`  [/auth/crypto/wallet/@/@/info]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
coin | object | See [**`object` Coin**](../../../../models/CRYPTO.md#object-coin)
protocol | object | See [**`object` Protocol**](../../../../models/CRYPTO.md#object-protocol)
wallet | object | See [**`object` Wallet**](../../../../models/CRYPTO.md#object-wallet)

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).