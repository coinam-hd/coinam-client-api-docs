[&laquo; Return to main page](../../../../README.md)

# Sign/Verify a Message

* Available to certain crypto-currency protocols only. 

Coin | Signing | Verification
--- | --- | ---
BTC | ✓ | ✓
TESTBTC | ✓ | ✓

## Sign Message
##### `POST`  [/auth/crypto/wallet/@/@/messages?sign_message]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
address | string | yes | Address to use for signing message
message | string | yes | Message to sign

### Success Response

Param | Type |  Description
--- | --- | --- 
signature | string | Base64 encoded signature
message | string | Message that was signed (whitespaces at beginning/end of strings are trimmed)

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`ADDR_REQ` | Address is required | n/a
`ADDR_INVALID` | Address is invalid or not owned | n/a
`MESSAGE_REQ` | Message is required | n/a
`MESSAGE_LEN` | Message must be between 2 and 512 bytes | n/a
`MESSAGE_INVALID` | Message contains an illegal character | UTF-8 not supported

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).