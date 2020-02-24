[&laquo; Return to main page](../../../../../README.md)

# Spend UTXO

* Get suggested fee
* Send a UTXO transaction

## Suggested UTXO Fee
##### `GET`  [/auth/crypto/wallet/@/@/utxo/spend?suggested_network_fee]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
utxoFee | object | [**`object` UTXOFee**](../../../../../models/CRYPTO.md#object-utxofee)

### Errors

Code | Description| Possible Resolution
--- | --- | ---


* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).

## Spend a transaction
##### `POST`  [/auth/crypto/wallet/@/@/utxo/spend?send_tx]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
payee_1 | string | yes | Payee address # 1
value_1 | string | yes | Value/amount to spend to payee # 1
payee_`n` | string | no | Payee address # `n` ; Must have corresponding `value_n` param; Maximum 10 payees;
value_`n` | string | no | Value/amount to send to payee # `n` ; Values must be > 0
memo | string | no | Arbitrary ASCII message; Maximum length 20
priority | string | yes | One of `low`, `normal` or `high`
utxo_policy | string | no | One of `NONE`, `BIG_FIRST` OR `SMALL_FIRST`; Defaults to `NONE`
broadcast | int | yes | Send `1` to broadcast transaction on network, `0` to only create transaction (Only works in development mode)

### Success Response

Param | Type |  Description
--- | --- | --- 
txId | string | Transaction hash that has been created
rawTx | string / NULL | Only in development mode, Raw transaction in hexadecimal format

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`CONCURRENT_SPEND_REQ` | Possible concurrent spend requests received | Try again in a second or 2
`PAYEE_REQ` | At least 1 payee is required | n/a
`PAYEE_ADDR_INVALID` | Invalid payee address | n/a
`PAYEE_VALUE_INVALID` | Invalid value/amount to payee | n/a
`MEMO_INVALID` | Memo field contains an illegal character | n/a
`MEMO_LEN` | Memo len exceeds 20 bytes | n/a
`PRIORITY_INVALID` | Invalid priority selection | n/a
`UTXO_POLICY_INVALID` | Invalid UTXO selection policy | n/a
`INSUFFICIENT_UTXO` | Insufficient balance | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../../README.md#global-error-messages).