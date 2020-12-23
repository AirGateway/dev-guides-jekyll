---
title: Multi-provider requests
sidebar: mydoc_sidebar
permalink: mydoc_multi_provider_requests.html
folder: mydoc
---

This requests are basically restricted to one single NDC method call (**AirShopping**) since it's the only NDC method that makes sense to be concurrently requested to multiple NDC providers.

To execute a MPR you only need send a valid standard NDC **AirShopping** request including an HTTP header like this:

> **AG-Providers:** \*
> This is interpreted by the **NDC Gateway** like a send to all available NDC providers for the consumer.

Alternatively, you can define a list of providers using a list of comma-separated standard [IATA airline designators](https://en.wikipedia.org/wiki/List_of_airline_codes).

> **AG-Providers:** BA, AA, LH

**MPR Responses**

Multi-Provider responses

MPRs behave asynchronously when used this HTTP headers:

> **Connection:** keep-alive

MPR response formats:

Our MPR responses (only applies to AirShopping seraches) has two modes: **Streaming** or **Standard HTTP**.

To enabled streaming mode (strongly recommended for GUI Applications) it's required to send the following HTTP header:

- **AG-Connection**: keep-alive

And optionally, for the streaming mode a timeout in the server-side can be set upon request of the client.

- **Keep-Alive:** timeout=xx (where xx is an integer number in seconds)

**Important note**

> Please, keep in mind streaming mode responses use a non-standard JSON notation wrapping called [JSON Streaming](https://en.wikipedia.org/wiki/JSON_streaming) used to streamline a collection of valid JSON objects instead of a resulting JSON-valid notation.
