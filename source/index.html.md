---
title: PlatformSync API Reference

language_tabs:
  - http
  - curl

toc_footers:
  - <a href='https://github.com/Loomis-us-sp/PlatformSync/issues'>Issues</a>

includes:
  # - errors

search: true
---

**Early Development Warning**

Note that this API (and associated documentation) is in VERY early stages of development.  It should be expected that, as long as you see this message, that the API can, and will, change. You have been warned!

# Introduction

Welcome to the Loomis PlatformSync API!

Our API comes in 2 flavors, Push API, and Pull API.

## Push API

As its name implies, the Push API will push data into your API via REST endpoints provided by you.  This will enable near-real-time transactional data.

## Pull API

The Pull API will enable you to connect to our API REST service to query for transactional data.  You will also use this service to get data that was missed from the Push Service

