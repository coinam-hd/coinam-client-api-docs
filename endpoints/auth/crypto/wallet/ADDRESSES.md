[&laquo; Return to main page](../../../../README.md)

# Addresses

* Get list of all addresses (paginated)
* Get most recent wallet address
* Create a new address

## Create a new address
##### `POST`  [/auth/crypto/wallet/@/@/addresses?create]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
label | string / NULL | no | An optional label for this address (max length 16)
import | string / NULL | no | Entropy (i.e. WIF key, etc...) if importing an address; Subject to import related permissions.

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`LABEL_INVALID` | Label contains an illegal character | n/a
`LABEL_LEN` | Label length must be between 2 and 16 characters | n/a
`ADDR_CREATE_TIMEOUT` | You are creating addresses too fast | Suggest user to wait at least 10 seconds
`WALLET_LIMIT_REACHED` | Wallet has reached its limit of maximum addresses | Check for `count` and `limit` param in response for more information
`ADDR_IMPORT_NA` | Crypto-currency protocol does not support private key imports | n/a
`ADDR_IMPORT_DISABLED` | Wallet does not have permission to import an address | This wallet cannot import an outside address

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).

---

## Retrieve List of Addresses
##### `GET`  [/auth/crypto/wallet/@/@/addresses]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
page | int | no | Pagination page number. Defaults to `1`.
perPage | int | no | Number of logs per page, select from `25`, `50` or `100`. Defaults to `50`.
match | string / NULL | no | A clause to match address or label with

### Success Response

Param | Type |  Description
--- | --- | --- 
addresses | array | An indexed array of (See [**`object` Address**](../../../../models/CRYPTO.md#object-address)) objects.
count | int | Number of rows in current page
totalCount | int | Total number of rows (all pages)
totalPages | int | Total number of pages
page | int | Current page number
nav | object | `CompactNav` object. (See [**Compact Nav**](../../../../models/PAGINATION.md#object-compactnav)).

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`INVALID_MATCH_PARAM` | Invalid value for match parameter | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).

---

## Get information on an address
##### `GET`  [/auth/crypto/wallet/@/@/addresses?info]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
address | string | yes | Crypto-currency address

### Success Response

Param | Type |  Description
--- | --- | --- 
address | object | [**`object` Address**](../../../../models/CRYPTO.md#object-address)

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`ADDRESS_NOT_FOUND` | No such address was found | n/a
`ADDRESS_INVALID` | Address param sent in request contains an illegal character | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).

---

## Get most recent address
##### `GET`  [/auth/crypto/wallet/@/@/addresses?last]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
address | object | [**`object` Address**](../../../../models/CRYPTO.md#object-address)

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`NO_ADDRESSES` | Wallet does not have any addresses generated | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).