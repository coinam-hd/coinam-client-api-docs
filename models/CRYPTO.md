## `object` Coin

Param | Type |  Description
--- | --- | --- 
name | string | Full crypto-currency protocol name (i.e. `Bitcoin` or `Bitcoin Testnet`)
code | string | Alphanumeric crypto-currency code (i.e. `BTC`)
sign | string / NULL | Sign/symbol for crypto-currency, normally a multi-byte UTF8 character (i.e. `Ƀ`)
scale | int | Precision for internal processing
decimals | int | Precision acceptable for user input

## `object` Protocol

Param | Type |  Description
--- | --- | --- 
requiresPayer | bool | Payer address is required to spend transaction?
maximumPayees | int | Maximum number of payees
walletsTypes | array | Indexed array of types of wallets offered; If empty, no selection is necessary
minimumTransfer | string | Minimum transaction amount

## `object` Wallet

Param | Type |  Description
--- | --- | --- 
status | string | One of "active", "frozen" or "disabled"
identifier | string | 36-byte wallet identifier
coin | string | Alphanumeric 2-8 digit crypto-currency code
label | string / NULL | User specific wallet name/label
allowKeysExport | bool | Indicates if owner can export private keys
allowKeysImport | bool | Indicates if owner can import private keys
createdOn | int | Timestamp (UTC) of wallet creation

## `object` Address

Param | Type |  Description
--- | --- | --- 
address | string | Crypto-currency address
label | string / NULL | User specific label (or NULL is none was specified)
isArchived | bool | Flag indicates if address has been marked archived
isImported | bool | Flag indicates if address was imported (rather then derived/generated internally)
isExported | bool | Flag indicates if private key has been exported to user
createOn | int | Timestamp in UTC

## `object` WalletAPIToken

Param | Type |  Description
--- | --- | --- 
id | int | A unique identifier
label | string | User-specified label for this API token
short | string | Initial 20 byte of 64 byte token
whitelist | array | Indexed array containing whitelisted IP addresses
status | bool | Determines if token is enabled or disabled
allowCreateAddr | bool | If token allows created of new addresses
allowCreateSpend | bool | If token allows spending
maxSpendPerTx | string | Maximum amount per transaction that can be spent
maxSpendPerDay | string | Maximum amount per day
createdOn | int | Timestamp in UTC

## `object` CryptoAsset

Param | Type |  Description
--- | --- | --- 
id | string | Asset unique identifier
code | string / NULL | Asset's symbol/code
scale | int | Asset's scaling/decimals value
usd_rate | int | 

## `object` WalletBalance

Param | Type |  Description
--- | --- | --- 
wallet | string | 36 byte wallet identifier
confirmed | string | Confirmed (spendable) balance
unconfirmed | string | Unconfirmed balance

## `object` AddressBalance

Param | Type |  Description
--- | --- | --- 
asset | null/object | `NULL` for native asset, otherwise 
address | string | Crypto-currency address
confirmed | string | Confirmed (spendable) balance
unconfirmed | string | Unconfirmed balance

