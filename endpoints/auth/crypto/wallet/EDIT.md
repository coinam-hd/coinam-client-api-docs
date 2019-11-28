[&laquo; Return to main page](../../../../README.md)

# Edit Wallets

* Edit wallet information

## Modify Label
##### `POST`  [/auth/crypto/wallet/@/@/edit?label]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
label | string | yes | Send new label parameter

### Success Response

Param | Type |  Description
--- | --- | --- 

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`LABEL_REQ` | Wallet label param is required | n/a
`LABEL_LEN` | Wallet label length must be between 3 and 32 digits | n/a
`LABEL_INVALID` | Wallet label contains an illegal character | n/a
`LABEL_SAME` | No changes were detected | n/a

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).