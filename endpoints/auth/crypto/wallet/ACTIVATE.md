[&laquo; Return to main page](../../../../README.md)

# Activate a new wallet

* If wallet status is "new", wallet may be activated from this endpoint
* User must download activation code and enter it to activate

## Get activation data
##### `POST`  [/auth/crypto/wallet/@/@/addresses?create]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token

### Success Response

Param | Type |  Description
--- | --- | --- 
activationCode | int | The activation code that user must enter
recoveryKeys | array | Indexed array of String dumped private (encrypted) or public keys

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`WALLET_NOT_NEW` | This is not a new wallet | Redirect to one of other wallet pages

* It is also possible to get one of [**Global Error Messages**](../../../../README.md#global-error-messages).

---