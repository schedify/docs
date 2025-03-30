---
sidebar_position: 2
---

# Authentication


The Schedify API uses API Key to authenticate requests.

You can view your api key in the [Settings](https://schedify.dev/settings) of your Schedify dashboard.

API requests are authenticated using the Bearer Auth scheme. To authenticate a request, provide the token in the Authorization header of the request:

```
curl -H "Authorization: <api_key>" https://api.schedify.dev/v1/me
```

:::warning

Please be sure to keep your API key secure! Do not share them in emails, chat messages, client-side code or publicly accessible sites.

If you have accidentally shared an API access token publicly, you can revoke it in the [Settings](https://schedify.dev/settings)

:::
