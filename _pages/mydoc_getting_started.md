---
title: Getting Started
sidebar: mydoc_sidebar
permalink: getting_started.html
folder: pages
---

# AirGateway Platform

Our platform offers many services to consume NDC content and adapts to different company needs.

The main products we offer for third-party developers are:
* NDC JSON API
* Partners API
 
## NDC JSON API Introduction

Our **NDC JSON API** is a software solution to allow third parties consume NDC APIs from airlines in an easy way.

It's completely JSON based and homogenizes every provider NDC implementation so that new developers only need to focus in their own app and forget about painful integrations with each new airline they need connecting to.

Once you obtain your Key, you can start using [our API](/NDC_API_Docs.html).


## Partners API Introduction

This [**Partners API**](/Hub_API_Docs.html) is intented to be used by companies who want to offer our services to other agencies.

With this API, once your Partner account is created, you can create new Agencies and Agents. Probably the most important method here is the [Issue Token method](https://hub.airgateway.net/api/static/swagger-ui/#/Agents/post_agents__agentID__issue_token), which you can use to get a token to call our NDC JSON API impersonating that given agent.