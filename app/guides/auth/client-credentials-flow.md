---
layout: twoColumn
section: guides
type: guide
guide:
    name: auth
    step: '2'
title: Obtaining an Application Access token
description: An application access token can then be used to make calls to the Dwolla API on behalf of the application.
---

# Overview - Obtaining an application access token

The [client credentials flow](https://tools.ietf.org/html/rfc6749#section-4.1) is used when an application needs to obtain permission to act on its own behalf. An application will exchange it's `client_id`, `client_secret`, and `grant_type=client_credentials` for an [application access token](https://docs.dwolla.com/#application-access-token). An application access token can then be used to make calls to the Dwolla API on behalf of the application, for example, when you create a webhook subscription, retrieve events, and interact with [Customer](https://docs.dwolla.com/#customers) related endpoints.

## Request application authorization
The client credentials flow is the simplest OAuth 2 grant, with a server-to-server exchange of your application's `client_id`, `client_secret` for an OAuth application access token. In order to execute this flow, your application will send a POST requests with the Authorization header that contains the word `Basic` followed by a space and a base64-encoded string `client_id:client_secret`.

`Authorization: Basic Base64(client_id:client_secret)`

##### HTTP request
`POST https://api.dwolla.com/token`

Including the `Content-Type: application/x-www-form-urlencoded` header, the request is sent to the token endpoint with `grant_type=client_credentials` in the body of the request:

##### Request parameters
| Parameter | Required | Type | Description |
|-----------|----------|----------------|-------------|
| client_id | yes | string | Application key. Navigate to `https://www.dwolla.com/applications` (production) or `https://dashboard-sandbox.dwolla.com/applications-legacy` (Sandbox) for your application key |
| client_secret | yes | string | Application secret. Navigate to `https://www.dwolla.com/applications` (production) or `https://dashboard-sandbox.dwolla.com/applications-legacy` (Sandbox) for your application secret. |
| grant_type | yes | string | This must be set to `client_credentials`. |

#### Example request

```raw
POST https://api-sandbox.dwolla.com/token
Authorization: Basic YkVEMGJMaEFhb0pDamplbmFPVjNwMDZSeE9Eb2pyOUNFUzN1dldXcXUyeE9RYk9GeUE6WEZ0bmJIbXR3dXEwNVI1Yk91WmVOWHlqcW9RelNSc21zUU5qelFOZUFZUlRIbmhHRGw=
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
# This example assumes you've already intialized the client. Reference the SDKs page for more information: https://developers.dwolla.com/pages/sdks.html
application_token = client.Auth.client()
```

```javascript
// Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-node
// This example assumes you've already intialized the client. Reference the SDKs page for more information: https://developers.dwolla.com/pages/sdks.html
client.auth.client()
  .then(function(appToken) {
    return appToken.get('webhook-subscriptions');
  })
  .then(function(res) {
    console.log(JSON.stringify(res.body));
  });
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
# This example assumes you've already intialized the client. Reference the SDKs page for more information: https://developers.dwolla.com/pages/sdks.html
application_token = $dwolla.auths.client
# => #<DwollaV2::Token client=#<DwollaV2::Client id="..." secret="..." environment=:sandbox> access_token="..." expires_in=3600 scope="...">
```

```php
/**
 *  No support for this language yet. We recommend using an external REST client for making OAuth requests.
 **/
```

#### Refreshing an application access token
A refresh token is not paired with an application access token, therefore in order to refresh authorization you'll simply request a new application access token by exchanging your client credentials (as shown above).

That's it! You're ready to start [making requests](/guides/auth/using-an-access-token.html) to the [Dwolla API](https://docs.dwolla.com/) on behalf your application.

<nav class="pager-nav">
    <a href="./">Back: Overview</a>
    <a href="using-an-access-token.html">Next step: Using an access token</a>
</nav>
