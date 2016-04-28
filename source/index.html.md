---
title: API Reference

language_tabs:
  - php
  - java
  - ios

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction
  所有请求和返回参数都是JSON格式
## 易配-API

#### HOST: "http://121.42.137.124"

#### Base URL: "/caraccessories/app"


# Login-Registration

## get verification code

> Request:

```json
{ 
"mobile": "17791865815", 
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
}
```

### 获得手机验证码

### Method:   POST
### Path:   /get_verification_code

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码

### Response

Name | Type | Default | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 -3.短信发送失败
msg | String | true | 

## registration

> Request:

```json
{
"mobile": "17791865815",
"code": "21342",
"password": "12345",
}
```

> Response:

```json
{
"status": "1",
"msg": "Ok",
}
```

### 注册

### Method:   POST
### Path:   /registration

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码
code | String | true | 验证码
password | String | true | 密码

### Response

Name | Type | Default | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 -3.验证码不正确 -4.验证码已过期 -5.手机号已注册
msg | String | true | 

## Login

> Request:

```json
{
"mobile": "17791865815",
"password": "12345",
}
```

> Response:

```json
{
"status": "1",
"msg": "Ok",
}
```

### 登录

### Method:   POST
### Path:   /login

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码
password | String | true | 密码

### Response:

Name | Type | Default | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 -3.手机号未注册 -4.密码不正确
msg | String | true | 

## Forget password

> Request:

```json
{
"mobile": "17791865815",
"code": "21342",
"password": "12345",
}
```

> Response:

```json
{
"status": "1",
"msg": "Ok",
}
```

### 忘记密码

### Method:   POST
### Path:   /forget_password

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码
code | String | true | 验证码
password | String | true | 密码

### Response

Name | Type | Default | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 -4.验证码不正确 -5.验证码已过期 -3.手机号没有注册
msg | String | true | 