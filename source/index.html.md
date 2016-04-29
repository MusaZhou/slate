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
## 易配-API http://121.42.137.124/caraccessories/app


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

<b> 获得手机验证码</b>

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

<b> 注册</b>

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

<b> 登录</b>

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

<b> 忘记密码</b>

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

# Home

## Home Search

> Request:

```json
{ 
"type": "1", 
"search": "abc",
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"shops":
		[
			{
				"id":"1",
				"name": "abc",
				"viewd_count": 14,
				"address": "abc",
				"sale_description": "abc",
				"service_time_start": "08:00",
				"service_time_end": "20:00",
				"description": "abc",
				"phone1": "12312432211",
				"image_url": "adfa",
			},
			{
				"id": "2",
				"name": "abc",
				"viewd_count": 14,
				"address": "abc",
				"sale_description": "abc",
				"service_time_start": "08:00",
				"service_time_end": "20:00",
				"description": "abc",
				"phone1": "12312432211",
				"image_url": "dasfas"
			},
		],
"products":
		[
			{
				"id": "1",
				"name": "abc",
				"price": 14,
				"quantity": 3,
				"spec": "abc",
				"model": "aaf",
				"car_model": "sadf",
				"description": "abc",
				"image_url": "dsfaasdf",
			},
			{
				"id": "2",
				"name": "abc",
				"price": 14,
				"quantity": 3,
				"spec": "abc",
				"model": "aaf",
				"car_model": "sadf",
				"description": "abc",
				"image_url": "dsfaasdf",
			},
		],
}
```

<b> 首页搜索</b>

### Method:   POST
### Path:   /home_search

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
type | int | true | 搜索类型 1.店铺 2.商品
search | string | true | 搜索值

### Response

Name | Type | Default | Description
--------- | ----------------- | ------- | -----------
status | int | true | 1.成功 -3.短信发送失败
msg | String | true | 
shops | array(shop object) | false | 店铺列表
products | array(product object) | false | 商品列表

#### shop object

Name | Type | Default | Description
--------- | ----------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
viewed_count | int | true | 浏览人数
address | string | true |
sale_description | string | true |
service_time_start | time | true | 营业开始时间
service_time_end | time | true | 营业结束时间
description | string | true | 
phone_1 | string | true |
image_url | string | true | 图片URL

#### product object

Name | Type | Default | Description
--------- | ----------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
price | double | true |
brand | string | true |
quantity | int | true | 库存
spec | string | true | 规格
model | string | true |
car_model | string | true |
description | string | true | 
image_url | string | 图片URL

## Get City By GPS

> Request:

```json
{
"latitude": 34.34,
"longitude": 108.93,
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"cityId": "10",
"cityName": "西安"
}
```

<b> 通过经纬度定位城市</b>

### Method:   POST
### Path:   /get_city_by_gps

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
latitude | String | true | 纬度
longitude | String | true | 经度

### Response:

Name | Type | Default | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 -3.手机号未注册 -4.密码不正确
msg | String | true | 
cityId | String | true | 城市Id
cityName | String | true | 城市名称
