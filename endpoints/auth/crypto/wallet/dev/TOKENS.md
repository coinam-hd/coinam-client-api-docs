
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
`TOKEN_NOT_FOUND` | No such API token exists | send a correct token ID

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).