# Push API

The Push API will push certain types of transactions to your supplied endpoints. We will send the transactions as soon as they are available and processed by our system.

## Setup

To begin the setup process, you must communicate directly with our support staff who will perform the requisite setup on our systems.  Send an email to LoomisSafePointSupport@us.loomis.com to get started.

The following table represents the data that should be sent to Loomis to configure this service.

Name | Required | More info
---- | -------- | ---------
Endpoints | Yes | Your service endpoint that will accept the POST payload containing transactions.  Multiple endpoints are supported. **NOTE** all data is sent to all the endpoints you provide.
Endpoint Type | No | Specifies type of environment (production, test, development, etc). This is an indicator for our staff to know what type of enviroment the endpoint is.
API Key(s) | Yes | Long-lived bearer token to authenticate with your service.  Should be specified _per Endpoint_.
API Key Name | Yes | What key to use when sending the API key in the payload. Defaults to `Authorization`.
API Key Placement | Yes | Where to place the API Key/Value pair.  Defaults to `header`.  Can be one of `header`, `body`, `query` or `metadata`
Endpoint Metadata | No | Additional payload to send.  Should be key-value pairs.  Keys and values should be strings only.
Notification Recipients | No | Email addresses to send notifications to in the event of a failure. See "Failure Notifications" below for more information.
Transaction Whitelist | No | List of transactions that will be sent (See "Transaction Whitelist" below).
Max Batch Size | No | Maximum number of transactions to send at a time.  Defaults to 1000. Maximum value is 1000.

## Endpoint URLs

You must provide a minimum of one _public_ endpoint for your data to be sent to. The transactions will be sent as an HTTP POST.  Please note that a copy of all transactions will be sent to all the endpoints that you provide.

Also note that the endpoint must be accessible to the internet without any VPN connection.

## Capacity Planning

There may be instances where we are POSTing a large volume of transactions at one time. Your service should be able to handle these bursts of high load.  This can be mitigated by specifying a smaller batch size. However, this will result in more messages.

Loomis will work with you during the setup phase to provide an estimate of the expected load.

## Security

Security should be implemented as a long-lived, unique API token.  We do not support security via OAuth, certificates or username/password.

The token will be passed to your endpoint in the manner you specify (either in the body, query string, or header) with the property name you specify as well.

The provided endpoint(s) must be HTTPS only.

## Transaction Whitelist

You may choose to receive any combination of the following types of transactions:

- ValidatedCashIn
  - Cashin performed by the note validator on the safe
- Servicing
  - A pickup by a Loomis courier
- ChangePurchase
  - A request for an amount of change to be delivered and paid for out of the validated cash already dropped
- ManualCashTransaction
  - A manual, non-validated drop
- CoinDispense
  - Coins that were dispensed
- NoteDispense
  - Notes that were dispensed
- TubeRemoved 
  - Tube removed from safe
- TubeLoaded
  - Tube loaded into safe
- EndOfDay
  - End of the accounting period on the safe

## Failure Notifications

We will attempt to deliver messages in a timely manner.  If we are unable to reach your service, we will notify the email addresses provided by you of that failure, and will continue to attempt to deliver the messages.

## Message Expiration

We will attempt to deliver your data on an interval for a period of 24 hours. If, after the 24-hours, we are still unable to deliever the transactions, we will send a second notification, and the messages will expire and not be retried.

## Message Delivery Order

We will deliver the transactions ordered by date in which they occured on the safe. We will make every attempt to deliver the transactions in the order in which they are processed by our system. However, occasionaly, in the even of a failure, these messages may come in out of order. Your service should take this into account when accepting transactions.