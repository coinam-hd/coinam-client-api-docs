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
walletsTypes | array | Indexed array of types of CryptoWalletsType objects (See [**`object` CryptoWalletsType**](#object-cryptowalletstype))
minimumTransfer | string | Minimum transaction amount

## `object` CryptoWalletsType

Param | Type |  Description
--- | --- | --- 
id | string | Primary identifier of wallet type
name | string | Name of wallet type
recoveryOpts | array/NULL | Recovery options available

## `object` Wallet

Param | Type |  Description
--- | --- | --- 
status | string | One of "new", "active", "frozen" or "disabled"
identifier | string | 36-byte wallet identifier
coin | string | Alphanumeric 2-8 digit crypto-currency code
type | string / NULL | Wallet type or NULL
label | string / NULL | User specific wallet name/label
allowKeysExport | bool | Indicates if owner can export private keys
allowKeysImport | bool | Indicates if owner can import private keys
createdOn | int | Timestamp (UTC) of wallet creation
balance | NULL / object | [`object` WalletBalance](#object-walletbalance) (with only NATIVE balance) or NULL

## `object` Address

Param | Type |  Description
--- | --- | --- 
address | string | Crypto-currency address
label | string / NULL | User specific label (or NULL is none was specified)
isArchived | bool | Flag indicates if address has been marked archived
isImported | bool | Flag indicates if address was imported (rather then derived/generated internally)
isExported | bool | Flag indicates if private key has been exported to user
createOn | int | Timestamp in UTC
balance | NULL / object | [`object` AddressBalance](#object-addressbalance) (with only NATIVE balance) or NULL

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

## `object` TransactionEntry

Param | Type |  Description
--- | --- | --- 
status | string | Transaction's current known state (possible values include "OK" and "ORPHANED")
coin | string | Crypto-currency code
tx | string | Transaction ID (64 to 66 characters). This is **NOT** a unique identifier, several entries of having different addresses but same TX id are possible
address | string | Address (owned) that transaction relates to
value | string | Transaction value
valueType | string | It is either "in" or "out", where "in" means value received (positive) and "out" means value spent (negative)
valueAssetId | string / NULL | Asset ID if it is an asset transfer (i.e. Ethereum ERC-20)
valueUsdRate | string / NULL | USD rate at time of transaction was logged. (**NOTE:** rate is according to the time TX is logged, not when it was made, therefore can be inaccurate)
txTimeStamp | int | Transaction time stamp (probably when the transaction was first seen or mined)
timeStamp | int | Transaction time stamp when it was logged

# `object` WebHook

Param | Type |  Description
--- | --- | --- 
id | int | Web hook unique identifier
method | string | "GET" or "POST"
url | string | Web hook URL starting with "http://" or "https://"
verifySSL | bool | If set to FALSE then SSL validation will be ignored when sending payload
httpAuthUsername | string / NULL | Used if web hook URL is protected with "HTTP Basic authorization"
httpAuthPassword | string / NULL | Used if web hook URL is protected with "HTTP Basic authorization"

---

## Pending

## `object` CryptoAsset

Param | Type |  Description
--- | --- | --- 
id | string | Asset unique identifier
name | string / NULL / Asset name
code | string / NULL | Asset symbol/code
scale | int | Asset's scaling/decimals value

## `object` WalletBalance

Param | Type |  Description
--- | --- | --- 
wallet | string | 36 byte wallet identifier
confirmed | string | Confirmed (spendable) balance
confirmed_usd | string/NULL | Confirmed balance in USD equivalent
unconfirmed | string | Unconfirmed balance
unconfirmed_usd | string/NULL | Unconfirmed balance in USD equivalent
usd_rate | string | USD rate

## `object` AddressBalance

Param | Type |  Description
--- | --- | --- 
asset | null/object | `NULL` for native asset, otherwise [`object` CryptoAsset](#object-cryptoasset))
address | string | Crypto-currency address
txs | int / NULL | Number of transactions involving this address
confirmed | string | Confirmed (spendable) balance
confirmed_usd | string/NULL | Confirmed balance in USD equivalent
unconfirmed | string | Unconfirmed balance
unconfirmed_usd | string/NULL | Unconfirmed balance in USD equivalent
usd_rate | string | USD rate

