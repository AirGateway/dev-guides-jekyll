---
title: Agents
sidebar: mydoc_sidebar
permalink: agents.html
folder: pages
---

Finally, each agency can have many agents working there. We use this entity you trace the whole selling process to every user involved. When a user logs into your system, you'll have to send his/her key (token) credential so we can know who's performing the action and what consumer he/she belongs to (check Authentication in NDC JSON API chapter).

---

[Agents](https://hub.airgateway.net/api/static/swagger-ui/#/Agents) have some specific information about the user, but these are the most relevant:

- Username
- Email
- Agency id
- Password

If you ever want your users to login in our Bookingpad app directly, you'll have to share with them their username, agency name and password.

> All these steps can be done via our own hub application if you prefer, you can request access to this tool if needed.

## Impersonating agents

Once you have created an Agent, you can call the [Issue Token method](https://hub.airgateway.net/api/static/swagger-ui/#/Agents/post_partner_agents__agentID__issue_token) to get an [NDC JSON API](/NDC_API_Docs.html) Token.

With that token, you can start calling the NDC JSON API and everything will be logged to that Agent.

## Authenticating agents in BookingPad

In our bookingpad tool, agents can login using their username, agency and password. But sometimes, your needs include your users login only on your own app (which uses our JSON API) and you want them to use bookingpad only for something that your own app doesn't support (check https://dev-guides.airgateway.net/hub_api_docs to know how to create agents in your organization, you'll need to store all the agents information in your app). You can use our own bookingpad or a different instance you have in your servers, in this case we'll use our own bookingpad instance domain.
You can achieve this by using following process:

- Obtain access token for the user you want to auto-authenticate

  1. Call https://app.airgateway.net/api/login
  2. Send username, agencyID and password of the user you want to get the access token as data-binary
  3. Example: `curl 'https://web.bookingpad.net/api/login' -H 'pragma: no-cache' -H 'origin: https://yourdomain.com' -H 'accept-encoding: gzip, deflate, br' -H 'accept-language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7,de;q=0.6,it;q=0.5' -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36' -H 'content-type: application/json;charset=UTF-8' -H 'accept: application/json, text/plain, */*' -H 'cache-control: no-cache' -H 'authority: app.airgateway.net' -H 'referer: https://yourdomain.com' --data-binary '{"username":"agent", "agency":"agency", "password":"XXXXXXX"}' --compressed`
  4. In order to make this work, please let us know the domain you'll call us from

- You'll receive an access token in the response which you'll have to add to the url you'll redirect your user to:

  - https://app.airgateway.net/login?access_token=XXXXXXXXXXXXXX

- If you want to send your users to our bookingpad once they have finished creating an order, so they can add ancillaries or seats, you can use "redirect_url" so once they are auto-logged they will be redirected to the page with the order they created:

  - https://app.airgateway.net/login?access_token=XXXXXXXXXXXXXX&redirect_url=https://app.airgateway.net/orders/LH/AGW-XXXXXXX
