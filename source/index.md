---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='https://console.cloud-elements.com/elements/jsp/signup.jsp'>Sign Up for a free Developer Account</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Cloud Elements API Documentation.  Integrate entire categories of services through uniform APIs.

This page provides in-depth documentation on Cloud Elements integrations (e.g. Salesforce, HubSpot, QuickBooks, Dropbox). This documentation is meant to be a guide for developers integrating these services into applications.

View example API calls and responses right from the documentation.  If you have any questions, feel free to [contact](mailto:support@cloud-elements.com) us.

# Base URL

```
https://api.cloud-elements.com/elements/api-v2
```

# Authentication

To call our APIs, you will need an account with Cloud Elements. To get an account, you must sign up using our console. When you create an account with us, we assign you an Organization secret and a User secret. An Organization is a customer of Cloud Elements (/organizations).
An Organization secret and User secret are needed to call our Platform APIs, to do things like:
* learn about our Catalog of endpoints (/elements)
* create connections to an endpoint (/instances) e.g. Dropbox or Salesforce

When you create a new connection to an endpoint, you will receive an Element token.
An Element token and a User secret are required to execute one of our Hub API calls (e.g. /hubs/documents or /hubs/crm) to:
* upload a file to a cloud storage account
* create a new contact in a CRM service

Our tokens and secrets are passed as HTTP Header Values.

> For example, to make an API call, the following authorization header is passed:

```
Authorization: User <INSERT_USER_SECRET>, Element <INSERT_ELEMENT_TOKEN>
```

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
