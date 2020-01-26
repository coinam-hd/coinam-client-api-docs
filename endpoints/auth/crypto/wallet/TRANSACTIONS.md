[&laquo; Return to main page](../../../../README.md)

# Transactions

* Retrieve all relevant transactions

## Retrieve List of Addresses
##### `GET`  [/auth/crypto/wallet/@/@/transactions]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
page | int | no | Pagination page number. Defaults to `1`.
perPage | int | no | Number of logs per page, select from `50`, `100` or `250`. Defaults to `50`.
match | string / NULL | no | A clause to match transaction hash or address

### Success Response

Param | Type |  Description
--- | --- | --- 
transactions | array | An indexed array of (See [**`object` TransactionEntry**](../../../../models/CRYPTO.md#object-transactionentry)) objects.
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
