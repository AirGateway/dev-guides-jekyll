---
title: Keys
sidebar: mydoc_sidebar
permalink: keys.html
folder: mydoc
---

This is the last step you need before you start sending requests to our JSON API. Every agent can have a key for each of our offered plans. For example, we offer a plan for our JSON API v1.0 and another for JSON API v1.1, so one agent could have a token for each of these.

---

Each [Key](https://hub.airgateway.net/api/static/swagger-ui/#!/Agent_Keys/post_keys) will be created with some information, including:

- [Plan id](https://hub.airgateway.net/api/static/swagger-ui/#!/Plans/get_plans)
- Agent id

Once you have a token for an agent, you can start calling the JSON API using it impersonating your agents as it's explained [here](https://dev-guides.airgateway.net/getting_started/authentication/).

> All these steps can be done via our own hub application which you'll have access to
