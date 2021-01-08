---
title: Sending Requests
sidebar: mydoc_sidebar
permalink: sending_requests.html
folder: mydoc
---

We use **HTTP/1.1** as communication protocol to accept requests to the gateway. All NDC requests are sent using the **POST** HTTP method.

The public endpoint to our **NDC Gateway** remains immutable for all NDC requests and it is:

- **Version 1**: (deprecated)
- **Version 1.1**: https://proxy.airgateway.net/v1.1/

We require some mandatory basic HTTP headers intended for message formatting:

- **Content-Type**: application/json
- **Accept**: application/json
- **Authorization**: XXXXXXXXXXXXX. You'll have to send your API token here or you won't be able to use AirGateway.

We accept some extra headers to change default behaviour:

- **AG-Providers**: value. Check multi-provider and single-provider requests pages for more information. You'll use "\*" to request all your providers offers and the IATA code to select specific airlines (BA, IB, AA, LH...).
- **AG-Connection**: keep-alive. This will return data streamed as soon as we receive the response from the airlines instead of waiting to have all airlines responses before returning data.
- **AG-Session-ID**: XXXXX-XXXXX-XXXXXX. With the first request for a session (usually, an AirShopping) you'll receive a **AG-Session-ID** header in response. You should use this header to allow us track full sessions combined with next header.
- **AG-Trace**: true. This is only accepted in sandbox environment and should only be used for debug purposes. If you experience any issue, please send your example requests with this header and using the same **AG-Session-ID** header. Then please, share the **AG-Session-ID** with us when reporting issue.
- **AG-Per-Provider-Limit**: max number of offers received for each provider.

It's very relevant to distinguish between two types of requests to send to the **NDC Gateway**. Attending to the architecture, we have two types of requests with significant differences between them:

- **MPR** (Multiple provider requests)
- **SPR** (Single provider requests)
