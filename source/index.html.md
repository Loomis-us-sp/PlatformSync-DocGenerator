---
title: PlatformSync API Reference

language_tabs:
  - json

toc_footers:
  - <a href='https://github.com/Loomis-us-sp/PlatformSync/issues'>Issues</a>
  - <a href='https://github.com/Loomis-us-sp/PlatformSync#loomis-safepoint-platformsync'>Why PlatformSync?</a>

includes:
  - push
  # - common
  - transactions

search: true
---

# Introduction

```json
{
  code_samples: "Will be over here"
}
```

Welcome to the Loomis PlatformSync API!

Our API comes in 2 flavors, Push API, and Pull API.

## PlatformSync Push API

As its name implies, the Push API will push transactions into your endpoints provided by you. The transactions will be sent as soon as they are available and processed by our systems.

## PlatformSync Pull API

The Pull API will enable you to connect to our API REST service to query for transactional data.  In the event of a failure, you can also use this service to get data that was missed from the Push API.

<aside class="warning">
<strong>This API has not available at this time.</strong>
</aside>

## Transaction Delivery and Exceptions

Transactions flow from the safe into our system (the timing of this depends on a number of factors). In most cases, if we have connectivity to the safe and there is no issue with the quality of the data, then the transactions will flow through our system very quickly.

However, there are some exceptions that could impact delivery of transactions.

First, our system performs a series of checks to ensure that the transactions are genuine and trustworthy. If our system determines that there is a potential issue, then processing is halted until our staff can ensure data quality.

Second, we may have problems communicating with your service. In this case, we will attempt to redeliver the messages on an interval for 24 hours. See "Message Expiration" below for additional information. 
