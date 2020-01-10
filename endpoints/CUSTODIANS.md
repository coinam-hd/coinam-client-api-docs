[&laquo; Return to main page](../README.md)

# Custodians

* Retrieves list of partner custodians
* Retrieves information of a partner custodian

## `GET` [/custodian]()

### Success Response

Param | Type |  Description
--- | --- | --- 
list | array | Indexed array of a custodian partner

#### `object` Custodian

Param | Type | Description
--- | --- | ---
id | string | Custodian id
name | string | Custodian name/title
descr | string | Custodian description
website | string | Link to custodian's website

### Errors

Code | Description| Possible Resolution
--- | --- | ---

It is also possible to get one of [**Global Error Messages**](../README.md#global-error-messages).