## Export an address
##### `GET`  [/auth/crypto/wallet/@/@/export?address]()

**NOT ALL CRYPTO-CURRENCY PROTOCOLS SUPPORT IMPORT/EXPORT METHODS**

* Bitcoin and all bitcoin-family coins will return **WIF** export keys.

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
address | string  | Crypto-currency address

### Success Response

Param | Type |  Description
--- | --- | --- 
address | string | Crypto-currency address (same as request)
format | string | Format of private key export
data | string | Exported private key

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`ADDR_EXPORT_NA` | Crypto-currency protocol does not support private key exporting | n/a
`ADDR_EXPORT_DISABLED` | Wallet does not have permission to export an address | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).