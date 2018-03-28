# Push API

The Push API will push certain types of transactions to your supplied REST endpoints. We will send the transactions as soon as they occur on the safe and are processed by our system.

## Setup

Right now, the setup for thie service is a manual process.  We have plans to integrate this into Loomis Direct, but at this time, we are not there yet.  To begin the setup process, you must communicate directly with our development teams who will perform the requisite setup on our systems.

The following table represents the data that should be sent to Loomis to configure this service.

Name | Required | More info
---- | -------- | ---------
Endpoints | Yes | Your service endpoint that will accept the POST payload containing transactions.  Multiple endpoints supported.
Endpoint Type | No | Specifies type of environment (production, test, development, etc). Defaults to our service value (PlatformSync in `test` will default this value to `test`.)
API Key(s) | Yes | Long-lived bearer token to authenticate with your service.  Should be specified _per Endpoint_.
API Key Property | Yes | What key to use when sending the API key in the payload. Defaults to `Authorization`
API Key Placement | Yes | Where to place the API Key/Value pair.  Defaults to `header`
Endpoint Metadata | No | Additional payload to send.  Should be key-value pairs
Notification Recipients | No | Email addresses to send notifications to
Expected Format | No | Only JSON datatypes are supported at this time.
Transaction Whitelist | No | List of transactions that will be sent (See "Transaction Whitelist" below)
Transaction Triggers | No | List of transactions that will trigger sending other data.  See "Transaction Triggers" below for more information.
Max Batc hSize | No | Maximum number of transactions to send at a time.  Defaults to 1000
Default Message TTL | No | Exipration of messages. Defaults to 24 Hours

## Endpoint URLs

You must provide a minimum of one REST endpoint for your data to be posted to.  The transactions will be sent as an HTTP POST.  Please note that all transactions will be sent to all the URL endpoints that you specify

## Security

Security should be implemented as a long-lived, unique API token.  We do not yet support security via OAuth, certificates or username/password.

The token will be passed to your REST endpoint in the manner you specify (either in the body, query string, or header) with the property name you specify as well.

## Transaction Whitelist

You may choose to receive any of the following types of transactions:

* Validated Drop = 1
* Change Purchase = 2
* End of Day = 3
* End of Shift = 4
* Servicing = 5

## Transaction Triggers

You may choose certain "buffer" points, where transactions are not sent to you until a certain type of transaction occurs.  For example, you may hold validated drops and servicings until an End of Day occurs, at which point all transactions that have not yet been sent will be sent along with the EOD transaction.

## Payload

```json
{
    count: 1000,
    total: 2322,
    start: 0,
    transactions: [
        { /* Transaction object */ }
    ]
}
```

We will send transactions as a POST. The transactions will come in JSON format, and will follow consistent patterns.

You should supply us with a desired size (in transaction count) of your payload.  We will default to 1,000 transactions at a time.

## Failure Notifications

If we are unable to deliever your data after a predefined number of retries, we will notifiy the defined email addresses of the failure.  It will then be your responsiblity to get these failed transactions from the Pull API.

## Message Expiration

We will attempt to deliver your data on an interval for a period of 24 hours.

## Caveats

In the event of a failure, we will do our best to deliver recovered transactions in the same order in which they occured. However, your system should be resilient enough to handle out-of-order transactions.