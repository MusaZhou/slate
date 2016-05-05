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
## 易配-API <font color="green">http://121.42.137.124/caraccessories/app</font>


# Login-Registration

## Get Verification Code

> Request:

```json
{ 
"mobile": "17791865815"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<b> 获得手机验证码</b>

### Method:   POST
### Path:   <font color="green">/get_verification_code</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码

### Response

Name | Type | Default | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 -3.短信发送失败
msg | String | true | 

## Registration

> Request:

```json
{
"mobile": "17791865815",
"code": "21342",
"password": "12345"
}
```

> Response:

```json
{
"status": "1",
"msg": "Ok"
}
```

<b> 注册</b>

### Method:   POST
### Path:   <font color="green">/registration</font>

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
"password": "12345"
}
```

> Response:

```json
{
"status": "1",
"msg": "Ok"
}
```

<b> 登录</b>

### Method:   POST
### Path:   <font color="green">/login</font>

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

## Forget Password

> Request:

```json
{
"mobile": "17791865815",
"code": "21342",
"password": "12345"
}
```

> Response:

```json
{
"status": "1",
"msg": "Ok"
}
```

<b> 忘记密码</b>

### Method:   POST
### Path:   <font color="green">/forget_password</font>

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
"provinceId": "5"
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
				"image_url": "adfa"
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
			}
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
				"image_url": "dsfaasdf"
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
				"image_url": "dsfaasdf"
			}
		],
}
```

<b> 首页搜索</b>

### Method:   POST
### Path:   <font color="green">/home_search</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
type | int | true | 搜索类型 1.店铺 2.商品
search | string | true | 搜索值
provinceId | int | true | 省份id

### Response

Name | Type | Default | Description
--------- | ----------------- | ------- | -----------
status | int | true | 1.成功 -3.短信发送失败
msg | String | true | 
shops | array(shop object) | false | 店铺列表
products | array(product object) | false | 商品列表

#### Shop object

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

#### Product object

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
image_url | string | true | 图片URL

## Get City By GPS

> Request:

```json
{
"latitude": 34.34,
"longitude": 108.93
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
### Path:   <font color="green">/get_city_by_gps</font>

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
provinceId | int | true | 省份Id

## Get Recommended Secondary Shop Types

> Request:

```json
{
"provinceId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"secondaryShopTypeList": [
						{
							"secondary_shop_type_id": 1,
							"secondary_shop_type_name": "test",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						},
						{
							"secondary_shop_type_id": 2,
							"secondary_shop_type_name": "test",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						}
						]
}
```

<b> 首页热门店铺类型</b>

### Method:   POST
### Path:   <font color="green">/home_secondary_shop_type</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
secondaryShopTypeList | Array(secondaryShopType object) | true | 热门店铺列表

### SecondaryShopType Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
secondary_shop_type_id | int | true | 店铺类型id
secondary_shop_type_name | string | true | 店铺类型名称
image_url | string | true | 图片url

## Get Recommended Product Types

> Request:

```json
{
"provinceId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"productTypeList": [
						{
							"product_type_id": 1,
							"product_type_name": "test",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						},
						{
							"product_type_id": 2,
							"product_type_name": "test",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						}
						]
}
```

<b> 首页热门商品类型</b>

### Method:   POST
### Path:   <font color="green">/home_product_type</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productTypeList | Array(productType object) | true | 热门商品类型列表

### ProductType Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
product_type_id | int | true | 商品类型id
product_type_name | string | true | 商品类型名称
image_url | string | true | 图片url

## Get Province List

> Request:

```json
{

}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"provinceList": [
						{
							"province_id": 1,
							"province_name": "陕西",
							"cityList": [
											{
												"city_id": 1,
												"city_name": "西安"
											},
											{
												"city_id": 2,
												"city_name": "西安"
											}
										]
						},
						{
							"province_id": 2,
							"province_name": "陕西",
							"cityList": [
											{
												"city_id": 3,
												"city_name": "西安"
											},
											{
												"city_id": 4,
												"city_name": "西安"
											}
										]
						}
						]
}
```

<b> 获得地区列表</b>

### Method:   POST
### Path:   <font color="green">/get_province_list</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
provinceList | Array(province object) | true | 省份列表

### Province Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
province_id | int | true | 省份id
province_name | string | true | 省份名称
cityList | Array(city object) | true | 城市列表

### City Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
city_id | int | true | 城市id
city_name | string | true | 城市名称

## Get Ad List

> Request:

```json
{
"provinceId": 1,
"locationId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"adList": [
						{
							"ad_id": 1,
							"ad_name": "abc",
							"ad_type": 1,
							"adable_id": 1,
							"ad_url": "http://123.123.12.1/index.html",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						},
						{
							"ad_id": 1,
							"ad_name": "abc",
							"ad_type": 1,
							"adable_id": 1,
							"ad_url": "http://123.123.12.1/index.html",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						}
			]
}
```

<b> 获得广告列表</b>

### Method:   POST
### Path:   <font color="green">/get_ads</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
locationId | int | true | 广告位置Id(1:首页1 2:首页2 3:展区 4:互动 5:单品 6:店铺二级类型)

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
adList | Array(ad object) | true | 广告列表

### Ad Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
ad_id | int | true | 广告id
ad_name | string | false | 名称
ad_type | int | true | 广告类型(1:店铺 2:产品 3:url 4:店铺(仅显示名字))
adable_id | int | true | 广告实体id(商店Id或产品Id)
ad_url | string | false | 若广告类型为3,为url地址
image_url | string | false | 若广告类型为1,2,3,为广告图片

## Get Shop Type List

> Request:

```json
{
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"ShopTypeList": [
						{
							"primary_shop_type_id": 1,
							"primary_shop_type_name": "小车",
							"firstLetterList": [
													{
														"firstLetter": "A",
														"secondaryShopTypeList": [
																					{
																						"secondary_shop_type_id": 1,
																						"secondary_shop_type_name": "宝马",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					},
																					{
																						"secondary_shop_type_id": 2,
																						"secondary_shop_type_name": "奔驰",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					}
																				]
													},
													{
														"firstLetter": "B",
														"secondaryShopTypeList": [
																					{
																						"secondary_shop_type_id": 3,
																						"secondary_shop_type_name": "法拉利",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					},
																					{
																						"secondary_shop_type_id": 4,
																						"secondary_shop_type_name": "劳斯莱斯",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					}
																				]
													}
												]
						},
						{
							"primary_shop_type_id": 2,
							"primary_shop_type_name": "单品专卖",
							"firstLetterList": [
													{
														"firstLetter": "A",
														"secondaryShopTypeList": [
																					{
																						"secondary_shop_type_id": 5,
																						"secondary_shop_type_name": "影音",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					},
																					{
																						"secondary_shop_type_id": 6,
																						"secondary_shop_type_name": "座套",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					}
																				]
													},
													{
														"firstLetter": "B",
														"secondaryShopTypeList": [
																					{
																						"secondary_shop_type_id": 7,
																						"secondary_shop_type_name": "内部装饰",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					},
																					{
																						"secondary_shop_type_id": 8,
																						"secondary_shop_type_name": "外部装饰",
																						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
																					}
																				]
													}
												]
						}
			]
}
```

<b> 获得店铺类别列表</b>

### Method:   POST
### Path:   <font color="green">/get_shop_types</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopTypeList | Array(Shop object) | true | 店铺类别列表

### Shop Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
primary_shop_type_id | int | true | 一级类别id
primary_shop_type_name | string | false | 一级类别名称
firstLetterList | Array(FirstLetter object) | true | 首字母列表

### FirstLetter Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
firstLetter | string | true | 首字母
secondaryShopTypeList | Array(SecondaryShopType object) | true | 二级类别列表

### SecondaryLetter Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
secondary_shop_type_id | int | true | 二级类别id
secondary_shop_type_name | string | true | 二级类别名称
image_url | string | true | 图片URL