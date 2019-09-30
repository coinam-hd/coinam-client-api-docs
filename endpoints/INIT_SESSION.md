# Initiate Session

* If a session cookie is not set, use this endpoint to request a new session;
* If session cookie is already set, ignore calling this endpoint;
* Sessions are IP address sensitive

# Request

Param | Type | Required | Description
--- | --- | --- | ---
type | string | no | Determined from user-agent for time being; This will change later!
