# Push API

The Push API will push certain types of transactions to your supplied REST endpoints. We will send the transactions as soon as they occur on the safe and are processed by our system.

## Setup

Right now, the setup for thie service is a manual process.  We have plans to integrate this into Loomis Direct, but at this time, we are not there yet.  To begin the setup process, you must communicate directly with our development teams who will perform the requisite setup on our systems.

The following table represents the data that should be sent to Loomis to configure this service.

Name | Required | More info
---- | -------- | ---------
Enpoints | Yes | Your service endpoint that will accept the POST payload containing transactions.  Multiple endpoints supported.
ApiKeys | Yes | Long-lived bearer token to authenticate with your service.  will be passed in the `Authorization` header.  Can be specified _per Endpoint_.
EndpointMetadata | No | Additional payload to send.  Should be key-value pairs
NotificationRecipients | No | Email addresses to send notifications to
ExpectedFormat | No | Only JSON datatypes are supported at this time.
TransactionWhitelist | No | List of transactions that will be sent (See "Interested Transactions" below)
TransactionTriggers | No | List of transactions that will trigger sending other data.  See "Transaction Triggers" below for more information.
MaxBatchSize | No | Maximum number of transactions to send at a time.  Defaults to 1000
DefaultMessageTTL | No | Exipration of messages. Defaults to 24 Hours

## URLs

You must provide a minimum of one REST endpoint for your data to be posted to.  The transactions will be sent as an HTTP POST.  Please note that all transactions will be sent to all the URL endpoints that you specify

## Security

Security should be implemented as a long-lived, unique API token.  We do not yet support security via OAuth or username/password.

The token will be passed to your REST endpoint either in the body or as an `Authorization` header as a bearer token.

## Interested Transactions

You may choose to receive any of the following types of transactions:

* End of Day
* End of Shift
* Validated Drop
* Change Purchase
* Servicing

In addition, you may choose certain "buffer" points, where transactions are not sent to you until a certain type of transaction occurs.  For example, you may hold validated drops and servicings until an End of Day occurs, at which point all transactions that have not yet been sent will be sent along with the EOD transaction.

## Transaction Triggers

Coming soon... 

## Payload

```json
    {
        count: 1000,
        remaining: 2322,
        start: 0,
        transactions: [
            { /* Transaction object */ }
        ]
    }
```

We will POST transactionsThe transactions will come in JSON format, and will follow consistent patterns.

You should supply us with a desired size (in transaction count) of your payload.  We will default to 1,000 transactions at a time.

## Failure Notifications

If we are unable to deliever your data after a predefined number of retries, we will notifiy the defined email addresses of the failure.  It will then be your responsiblity to get these failed transactions from the Pull API.

## Message Expiration

We will attempt to deliver your data on an interval for a period of 24 hours.

## Caveats

In the event of a failure, we will do our best to deliver recovered transactions in the same order in which they occured. However, your system should be resilient enough to handle out-of-order transactions.