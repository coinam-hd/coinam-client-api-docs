
## Retrieve List of Tokens
##### `GET`  [/auth/crypto/wallet/@/@/dev/tokens?list]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
tokens | array | Indexed array of [**`object` WalletAPIToken**](../../../../../models/CRYPTO.md#object-walletapitoken) objects.

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).

---

## Retrieve Info on single API token
##### `GET`  [/auth/crypto/wallet/@/@/dev/tokens?info]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
tokenId | int | yes | Token identifier

### Success Response

Param | Type |  Description
--- | --- | --- 
token | object | See [**`object` WalletAPIToken**](../../../../../models/CRYPTO.md#object-walletapitoken).

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`TOKEN_ID_REQ` | A token ID is required | Send "tokenId" param
`TOKEN_NOT_FOUND` | No such API token exists | send a correct token ID

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).

---

## Token Setup
##### `POST`  [/auth/crypto/wallet/@/@/dev/tokens?setup]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
tokenId | int | **Depends** | **Important:** if param "tokenId" is NOT provided, a new wallet API token shall be created otherwise existing object will be updated!
label | string | no | A label for this API token
status | string | no | If value sent is "on" then its considered TRUE otherwise FALSE
allowCreateAddr | string | no | If value sent is "on" then its considered TRUE otherwise FALSE
allowSpend | string | no | If value sent is "on" then its considered TRUE otherwise FALSE
maxSpendPerTx | string | yes | Amount value as string; If NULL is sent, then a value of "0" is considered
maxSpendPerDay | string | yes | Amount value as string; If NULL is sent, then a value of "0" is considered
whitelist | string | yes | Comma separated IPv4 addresses, minimum 1, maximum 10;

* **NOTE:** IP addresses may use "%" in place of a subnet as a wildcard character

### Success Response

Param | Type |  Description
--- | --- | --- 
token | object | See [**`object` WalletAPIToken**](../../../../../models/CRYPTO.md#object-walletapitoken).
newTokenEntropy | hash64 | If a new token was created, a 64 byte hexadecimal string is returned

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`TOKEN_ID_REQ` | A token ID is required | Send "tokenId" param
`TOKEN_NOT_FOUND` | No such API token exists | send a correct token ID
`LABEL_REQ` | Label is required | Send a label for API token 
`LABEL_LEN` | Label length error | Label must be 3-16 characters long
`LABEL_INVALID` | Label contains an illegal character | n/a
`NO_CHANGES` | There are no changes to be saved | n/a
`AMOUNT_INVALID` | Amount is invalid | Send a correct amount; Check `param` value of response
`AMOUNT_MIN_ERR` | Amount is lower then least possible | Send a correct amount; Check `param` value of response
`IP_WHITELIST_REQ` | IP addresses whitelist is required | Send at least one IP address to whitelist
`IP_WHITELIST_INVALID` | One of the IP addresses is invalid | Check response param `invalidIPNum` 
`WALLET_TOKENS_LIMIT` | Wallet has reached limit of API tokens | No new tokens may be created

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).

---

## Delete a token
##### `DELETE`  [/auth/crypto/wallet/@/@/dev/tokens]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
tokenId | int | yes | Token ID to delete

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`TOKEN_ID_REQ` | A token ID is required | Send "tokenId" param
`TOKEN_NOT_FOUND` | No such API token exists | send a correct token ID

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).