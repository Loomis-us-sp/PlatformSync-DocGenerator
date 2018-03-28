# Objects

## Request Objects

### Push API Request Objects

There are no publically exposed endpoints for the Push API, and therefore no request object definitions.  

### Pull API Request Objects

The implementation of the Pull API is still pending.  This documentation will be update when that API is defined.

## Response Objects

The Push and Pull APIs will share object definitions (while we are aware that the payload we send in the Push API is not technically a "response").

Properties with `null` values will be excluded from the payload.
