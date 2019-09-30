[&laquo; Return to main page](../README.md)

# Countries

* Retrieves list of countries that should be visible to users for selection;

## `GET` [/countries]()

### Success Response

Param | Type |  Description
--- | --- | --- 
countries | object | List of countries as JSON object

### Errors

Code | Description| Possible Resolution
--- | --- | ---
`SESSION_CREATE_ERROR` | Failed to start a new API session | n/a
`SESSION_CREATE_TIMEOUT` | Request new sessions/tokens too fast from same IP address | Possible abuse detected

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).