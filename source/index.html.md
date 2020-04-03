---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kingpin API!

This API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

## GraphQL mutation 

To authorize, you need to get authentication token from GraphQL mutation sign_in. 


> GraphQL sign_in mutation response:

```json
{
  "data": {
    "sign_in": {
      "id": "14",
      "name": "Farahhhh",
      "token": "eyJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6ImZhcmFoczAyQGdtYWlsLmNvbSIsImV4cCI6MTkwMTI2NjE4NX0.-sdBaSGju0k8T8CuEEx3iY4aCk5iyTVWFQfih9V5HOI"
    }
  }
}
```
Make sure to replace `token` with from 'token' key that you get from GraphQL sign_in response.
.
Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {token}`

<aside class="notice">
You must replace <code>{token}</code> with token from GraphQL mutation sign_in response.
</aside>


# Photos

## Uploading Photos

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('Bearer {token}')
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

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
``` -->

> Response:

```json
{
  "data": {
    "message": "You have successfully uploaded your profile photo!",
    "img_url": "/attachments/02050d1e36ac38f6825b1ba565ca4bdb0f947d56/store/fill/100/100/1d30ea228ee32bbcd3374722fb0c7f0423acc4719f90f01e509ce29387a9/profile_image"
  }
}
```

This endpoint uploads user's profile photo

### HTTP Request

`POST http://kingpin-dev.eba-5qmbv3ry.ap-southeast-1.elasticbeanstalk.com/photos/upload`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
photo[profile_image] | - | Attachment to show user's profile photo
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

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

