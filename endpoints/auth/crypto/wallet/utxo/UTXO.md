[&laquo; Return to main page](../../../../../README.md)

# UTXO

* Retrieves list of all UTXOs
* Validates a wallet transaction/UTXO

## Retrieve UTXOs
##### `GET`  [/auth/crypto/wallet/@/@/utxo/utxo]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
page | int | no | Pagination page number. Defaults to `1`.
perPage | int | no | Number of logs per page, select from `50` or `100`. Defaults to `50`.
type | string / NULL | no | Possible arguments are `all`, `unspent`, `spent`; Defaults to `all`
match | string / NULL | no | A clause to match address or transaction hash with

### Success Response

Param | Type |  Description
--- | --- | --- 
list | array | An indexed array of (See [**`object` UTXO**](../../../../../models/CRYPTO.md#object-utxo)) objects.
count | int | Number of rows in current page
totalCount | int | Total number of rows (all pages)
totalPages | int | Total number of pages
page | int | Current page number
nav | object | `CompactNav` object. (See [**Compact Nav**](../../../../../models/PAGINATION.md#object-compactnav)).

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`INVALID_TYPE_PARAM` | Invalid value for type parameter | n/a
`INVALID_MATCH_PARAM` | Invalid value for match parameter | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).
