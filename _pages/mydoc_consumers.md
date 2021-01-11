---
title: Consumers
sidebar: mydoc_sidebar
permalink: consumers.html
folder: pages
---

The top level entity in our hub are consumers. Each consumer represents one company which has credentials to use NDC with one or many airlines (providers).

---

These [consumers](https://hub.airgateway.net/api/static/swagger-ui/#!/Consumers/post_consumers) will have one or many agencies, depending on their size. And each of these agencies will have one or many agents.

You'll need to setup some information about consumer like:

- Country code
- City code
- City name
- Currency code
- Contact email
- IATA Number

Here you can save the default values for payment like BSP.

A very important part of this step is adding providers to every single consumer they want (each consumer can have agreements with one or many airlines). You can retrieve all the available providers with [providers request](https://hub.airgateway.net/api/static/swagger-ui/#!/Providers).

Once you have added one or many providers, you can retrieve their [providers fields](https://hub.airgateway.net/api/static/swagger-ui/#!/Provider_Fields/get_provider_fields) (each provider needs different credentials, you'll get a list of these fields like "key" or "secret" which will be named after the documents airlines will send your consumers).

> All these steps can be done via our own hub application which you'll have access to
