---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# 简介

正式服务器地址: http://geeift.com

测试服务器地址: http://test.geeift.com

# 用户认证

> 用户登录后，需要在请求的http头部添加Access-Token, 从而让服务器知道当前的用户登录状态


```shell
# With shell, you can just pass the correct header with each request
curl "url.com/v1/xxx"
  -H "Access-Token: 登录令牌"
```

# 用户

## 登录

### HTTP Request

`GET /v1/users/signin`


```shell
curl /v1/users/signin
  -d "phone=15618890099&password=12345678"
```


> 返回

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
> 返回

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

