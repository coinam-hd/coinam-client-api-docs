# Coinam Client API Docs

Coinam Client API documentation.

## Basics

**Base URL:** https://api.coinam.com/client/


## Endpoints

├── Endpoints  
│   ├── `GET` [init_session](endpoints/INIT_SESSION.md) Initiate Session  
│   ├── [session](endpoints/SESSION.md) Get information about current sessions  
│   ├── [register](endpoints/REGISTER.md) Signup / Registration of new user  
│   └── [login](endpoints/LOGIN.md) Authenticate session as a registered user  
└── 

## Global Error Messages

Code | Meaning | Possible Resolution
--- | --- | ---
DB_CONNECTION_ERROR | App fails to connect with appropriate API logs database | n/a
BAD_REMOTE_ADDR | App fails to determine remote IP address | n/a
API_SESSION_NOT_FOUND | No such API session found with given token (and/or in rare cases IP address) | n/a
API_SESSION_RETRIEVE_ERROR | There was an error while retrieving API session | Discard existing session; Start  a new one
SESSION_CHECKSUM_FAIL | Session checksum validation has failed | Discard existing session; Start a new one
SESSION_CREATE_ERROR | Failed to start a new API session | n/a
SESSION_CREATE_TIMEOUT | Request new sessions/tokens too fast from same IP address | Possible abuse detected