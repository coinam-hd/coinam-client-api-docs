## `object` Coin

Param | Type |  Description
--- | --- | --- 
name | string | Full crypto-currency protocol name (i.e. `Bitcoin` or `Bitcoin Testnet`)
code | string | Alphanumeric crypto-currency code (i.e. `BTC`)
sign | string / NULL | Sign/symbol for crypto-currency, normally a multi-byte UTF8 character (i.e. `Ƀ`)
scale | int | Precision for internal processing
decimals | int | Precision acceptable for user input

## `object` Wallet

Param | Type |  Description
--- | --- | --- 
identifier | string | 36-byte wallet identifier
coin | string | Alphanumeric 2-8 digit crypto-currency code
label | string / NULL | User specific wallet name/label
createdOn | int | Timestamp (UTC) of wallet creation
stats | 

## `object` WalletStats

Param | Type |  Description
--- | --- | --- 