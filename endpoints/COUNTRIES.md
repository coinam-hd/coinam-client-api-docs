[&laquo; Return to main page](../README.md)

# Countries

* Retrieves list of countries that should be visible to users for selection;

## `GET` [/countries]()

### Success Response

Param | Type |  Description
--- | --- | --- 
countries | array | Indexed array of countries as each as JSON object

#### `object` country

Param | Type | Description
--- | --- | ---
name | string | Full country name
status | integer | Can be int 1 or 0; Currently only countries with status 1 are returned
code | string | ISO 3166-1 (Alpha-3)
codeShort | string | Alpha-2
dialCode | int | International dialing code/prefix

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`COUNTRIES_RETRIEVE_FAIL` | Failed to get list of countries | n/a

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).