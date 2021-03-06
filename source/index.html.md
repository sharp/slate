---
title: API Reference

language_tabs:
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

---

# 简介

> 正式服务器地址: http://geeift.com

> 测试服务器地址: http://test.geeift.com


--- 

# 用户认证

用户登录后，需要在请求的http头部添加Access-Token, 从而让服务器知道当前的用户登录状态

With shell, you can just pass the correct header with each request

```shell
curl "url.com/v1/xxx"
  -H "Access-Token: 登录令牌"
```

---

# 用户

## 登录


### HTTP Request


`GET /v1/users/signin`


```shell
curl /v1/users/signin
  -d "phone=15618890099&password=12345678"
```


返回

```json
  profile{
    "user_id": 1,
    "username": "Fluffums",
    "access_token": "令牌",
    "phone": 15618890099
  }
```

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
phone | string | 手机号码.
password | string | 登录密码.


## 注册

### HTTP Request

`POST /v1/users/siginup`

```shell
curl /v1/users/signup -d "phone=15618899988&password=12345678&sms_token=12345&username=sharp"
```

返回

```json
  profile{
    "user_id": 1,
    "username": "Fluffums",
    "access_token": "令牌",
    "phone": 15618890099
  }
```

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
phone | string | 手机号码.
password | string | 登录密码.
sms_token | string | 手机验证码.
username | string | 用户名.

## 发送验证码(不校验用户是否存在)

### HTTP Request

`POST /v1/sms_tokens`

```shell
curl /v1/sms_token -d "phone=15618899988"
```

测试环境返回


```json
  {
    "sms_token": 12345
  }
```

## 发送验证码(校验用户是否存在)

### HTTP Request

`POST /v1/sms_tokens/send`

```shell
curl /v1/sms_tokens/send -d "phone=15618899988"
```

测试环境返回

```json
  {
    "sms_token": 12345
  }
```

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

This endpoint retrieves a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

