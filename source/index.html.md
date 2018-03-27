---
title: PlatformSync API Reference

language_tabs:
  - json

toc_footers:
  - <a href='https://github.com/Loomis-us-sp/PlatformSync/issues'>Issues</a>

includes:
  - push

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

<aside class="notice">
<strong>Early Development Warning</strong> Note that this API (and associated documentation) is in VERY early stages of development.  It should be expected that, as long as you see this message, that the API can, and will, change. You have been warned!
</aside>

## PlatformSync Push API

As its name implies, the Push API will push data into your API via REST endpoints provided by you.  This will enable near-real-time transactional data.

## PlatformSync Pull API

The Pull API will enable you to connect to our API REST service to query for transactional data.  You will also use this service to get data that was missed from the Push Service

## Missing Data

There may be instances where you would expect data to be coming to you, but it is not there.  In _most_ cases, this is due to a data quality alert that halts processing until someone can take action on the alert.  

In other instances, we may have been unable to deliver messages to your endpoints (in the case that you're using the Push API).  In these instances, you will want to use the Pull API to fill in the missing information.
