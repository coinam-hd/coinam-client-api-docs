# Coinam Client API Docs

Coinam Client API documentation.

## Basics

**Base URL:** https://api.coinam.com/client/  
**Charset:** All are from **ASCII** (from index 32 to 126), unless other charset is mentioned specifically;  


## Endpoints

├── Endpoints  
│   ├── [**/session**](endpoints/SESSION.md) *(Initiate a new session OR retrieve information of existing)*  
│   ├── [**/countries**](endpoints/COUNTRIES.md) *(Get list of countries)*  
│   ├── [**/register**](endpoints/REGISTER.md) *(Signup / Registration of new user)*  
│   └── [**/login**](endpoints/LOGIN.md) *(Authenticate session as a registered user)*  
│   
├── **Authenticated Session** Endpoints  
│   ├── [**/auth/recovery**](endpoints/auth/RECOVERY.md) *(Account Recovery Setup)*  
│   ├── [**/auth/totp**](endpoints/auth/TOTP.md) *(Account 2FA/TOTP Setup)*  
│   ├── [**/auth/profile**](endpoints/auth/PROFILE.md) *(Account profile & E-mail verifications)*  
│   ├── [**/auth/dashboard**](endpoints/auth/DASHBOARD.md) *(Dashboard)*  
│   ├── [**/auth/log**](endpoints/auth/LOG.md) *(Account Log Audit)*  
│   ├── [**/auth/dev**](endpoints/auth/DEV.md) *(Developers setup)*  
│   ├── [**/auth/dev/webhooks**](endpoints/auth/dev/WEBHOOKS.md) *(Web Hooks setup)*  
│   └── [**/auth/logout**](endpoints/auth/LOGOUT.md) *(Clears an authenticated session)*  
│   │   
│   └── **Crypto** Endpoints  
│       └── [**/auth/crypto/available_coins**](endpoints/auth/crypto/AVAILABLE-COINS.md) *(List of available crypto-currencies)*  
│       ├── [**/auth/crypto/wallets**](endpoints/auth/crypto/WALLETS.md) *(List existing OR create a wallet)*  
│       ├── [**/auth/crypto/wallet/@/@/addresses**](endpoints/auth/crypto/wallet/ADDRESSES.md) *(List or generate payment addresses)*  
│       ├── [**/auth/crypto/wallet/@/@/export**](endpoints/auth/crypto/wallet/EXPORT.md) *(Export a private key or wallet)*  
│       ├── [**/auth/crypto/wallet/@/@/messages**](endpoints/auth/crypto/wallet/MESSAGES.md) *(Sign or verify messages)*  
│       ├── [**/auth/crypto/wallet/@/@/transactions**](endpoints/auth/crypto/wallet/TRANSACTIONS.md) *(Retrieve transactions history)*  
│       ├── [**/auth/crypto/wallet/@/@/tx/spend**](endpoints/auth/crypto/wallet/transaction/SPEND.md) *(Submit a payment transaction)*  
│       ├── [**/auth/crypto/wallet/@/@/dev/tokens**](endpoints/auth/crypto/wallet/dev/TOKENS.md) *(Wallet API tokens)*  
│       └── [**/auth/crypto/wallet/@/@/info**](endpoints/auth/crypto/wallet/INFO.md) *(Retrieve information about wallet)*  
│   
└──  

## XHR Requests

### Headers

Header | Description
--- | ---
Coinam-Client-Token | Required for all endpoints except [**`POST` /session**](endpoints/SESSION.md) endpoint
Coinam-Client-Timestamp | Timestamp in UTC (GMT+0:00) timezone

* Params can be sent as `application/json` or `application/x-www-form-urlencoded`
* Response is always sent as `application/json; charset=utf8`

## Global Response Params

Param | Type | Description
--- | --- | ---
`status` | boolean | Determines if request was successful; On `false` response object MAY include `error` param
`error` | string | An error message/code, included in response if there is an error; Can sometimes be an empty string or NULL; In such cases it can be reported as "Failed without an error code"
`param` | string/NULL | Indicates which form field/param caused an error, if present, focus should be given to that field/param for better UX

## Global Error Messages

Code | Meaning | Possible Resolution
--- | --- | ---
`API_DISABLED` | Client API is globally disabled | n/a
`API_CONTROLLER_DISABLED` | Requested endpoint/controller is currently disabled | n/a
`INTERNAL_ERROR` | An internal error has occurred | n/a
`PLATFORM_CONFIG_ERROR` | Failed to retrieves platform configuration | n/a
`PLATFORM_ACCESS_ERROR` | Failed to retrieves platform accessibility config | n/a
`DB_CONNECTION_ERROR` | App fails to connect with appropriate API logs database | n/a
`DB_QUERY_ERROR` | DB query critical to execution was failed | n/a
`BAD_REMOTE_ADDR` | App fails to determine remote IP address | n/a
`SESSION_ID_HEADER` | API session id not sent as HTTP request header | Send API session ID
`SESSION_ID_HEADER_INVALID` | API session id sent as header is invalid (does not match hash64) | Send a valid API session ID
`SESSION_NOT_FOUND` | No such API session found with given token (and/or in rare cases IP address) | n/a
`SESSION_RETRIEVE_ERROR` | There was an error while retrieving API session | Discard existing session; Start  a new one
`SESSION_IP_ERROR` | Session was not initiated with current IP address | Discard existing session; Start a new one; **Notify user that their IP address has changed**
`SESSION_CHECKSUM_FAIL` | Session checksum validation has failed | Discard existing session; Start a new one
`SESSION_IS_ARCHIVED` | Session has been archived; A user with same authenticated ID has created/logged on to a newer token/session | Discard existing session; Start a new one
`XSRF_ERROR` | XSRF/CSRF error | n/a
`RECAPTCHA_REQ` | ReCaptcha validation is required | Send `reCaptchaRes` param
`RECAPTCHA_FAILED` | ReCaptcha validation has failed | Reload reCaptcha so user may try again
`PAGINATION_INVALID_LIMIT` | Invalid number of rows/entries limit per page | Send a appropriate value
`CRYPTO_INVALID` | Crypto-currency code is invalid | Send a valid crypto-currency code (alphanumeric 2-8 digits)
`CRYPTO_RESTRICTED` | Crypto-currency access is restricted | User is not allowed to create/use wallets in this crypto-currency

## Wallet Endpoints

Code | Meaning | Possible Resolution
--- | --- | ---
`WALLET_INVALID_COIN` | Invalid URL coin code | Send a valid crypto-currency code
`WALLET_INVALID_IDENTIFIER` |  Wallet identifier sent via URL is invalid | Send a valid wallet identifier string
`WALLET_NOT_FOUND` | No such wallet exists or is not owned by authenticated user | n/a
`WALLET_COIN_MISMATCH` | Wallet coin does not match with crypto-currency code sent via URL | n/a
`WALLET_STATUS` | Wallet is inaccessible because of its status | Contact support

### Authentication Errors

Code | Meaning | Possible Resolution
--- | --- | ---
`AUTH_NOT_LOGGED_IN` | User is not logged in; Attempting to access authenticated only controller | Redirect users to login screen
`AUTH_USER_RETRIEVE_ERROR` | There was an internal error while retrieving user account | n/a
`AUTH_TOKEN_MISMATCH` | User has logged in again using different device/browser | Redirect user to login screen; **Tell them they have their session has been overridden**
`AUTH_USER_TIMEOUT` | Authenticated session has timed out | User needs to login again
`AUTH_USER_DISABLED` | User account has been DISABLED | n/a
`AUTH_USER_2FA_NOT_SETUP` | 2FA has not been setup for this account | Always force users to [**Finish TOTP setup**](endpoints/auth/TOTP.md) right after Registration

### 2FA Error Messages

Code | Meaning | Possible Resolution
--- | --- | ---
`2FA_TOTP_AUTH_REQ` | last 2FA TOTP authentication has had expired since, user needs to re-validate session with TOTP |  
`2FA_TOTP_REQ` | 2FA TOTP code is required | Enter 2FA code from Google Authenticator app
`2FA_TOTP_INVALID` | 2FA TOTP code is invalid; Does not match pattern | Invalid 2FA TOTP code
`2FA_TOTP_INCORRECT` | 2FA TOTP code is incorrect | You have entered incorrect 2FA code
`2FA_TOTP_USED` | 2FA TOTP code has already been used | Same code may not be used more then once