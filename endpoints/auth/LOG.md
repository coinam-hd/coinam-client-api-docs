[&laquo; Return to main page](../../README.md)

# Audit Log

* Retrieve account logs

## `GET`  [/auth/profile]()

### Request Params

Param | Type | Required | Description
--- | --- | --- | ---
xsrf | hash32 | yes | XSRF token
page | int | no | Pagination page number. Defaults to `1`.
perPage | int | no | Number of logs per page, select from `25`, `50` or `100`. Defaults to `50`.

### Success Response

Param | Type |  Description
--- | --- | --- 
logs | array | An array of `Log` objects
count | int | Number of rows in current page
totalCount | int | Total number of rows (all pages)
totalPages | int | Total number of pages
page | int | Current page number
nav | object | `CompactNav` object. (See [**Compact Nav**](../PAGINATION.md#compact-navigation)).

#### `object` Log

Param | Type |  Description
--- | --- | --- 
flag | NULL/string | A flag associated with this log, or NULL
flagId | NULL/int | An integer identifier associated with flag or NULL
log | string | Log message
data | NULL/array | Data associated with log or NULL
ipAddress | string | Logged IP address
timeStamp | int | Timestamp of log
dateTime | string | Date time represented as string (`jS M Y H:i`)

### Errors

Code | Description| Possible Resolution
--- | --- | ---

* It is also possible to get one of [**Global Error Messages**](../../README.md#global-error-messages).