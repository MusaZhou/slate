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
## 易配-API <font color="green">http://www.xianyipei.com/app</font>


# Login-Registration

## <font color="blue">Get Verification Code</font>

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

<font size="4"><b> 获得手机验证码</b></font>

### Method:   POST

### Path:   <font color="green">/get_verification_code</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码

### Response

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 3.短信发送失败
msg | String | true | 

## <font color="blue">Registration</font>

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

<font size="4"><b> 注册</b></font>

### Method:   POST

### Path:   <font color="green">/registration</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码
code | String | true | 验证码
password | String | true | 密码

### Response

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 3.验证码不正确 4.验证码已过期 5.手机号已注册
msg | String | true | 

## <font color="blue">Login</font>

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
"msg": "Ok",
"cartId": 2,
"userId": 1,
"user_status": 2
}
```

<font size="4"><b> 登录</b></font>

### Method:   POST

### Path:   <font color="green">/login</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码
password | String | true | 密码

### Response:

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 3.手机号未注册 4.密码不正确
msg | String | true | 
cartId | string | true | 购物车id
userId | int | true | 用户id
user_status | int | true | 用户类型 1.普通用户 2.普通商户 3.vip商户 4.参展厂商 5.正在申请商铺 6.正在申请展会
image_url | string | false | 用户头像url
real_name | string | false | 真实姓名

## <font color="blue">Forget Password</font>

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

<font size="4"><b> 忘记密码</b></font>

### Method:   POST

### Path:   <font color="green">/forget_password</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
mobile | String | true | 手机号码
code | String | true | 验证码
password | String | true | 密码

### Response

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 4.验证码不正确 5.验证码已过期 3.手机号没有注册
msg | String | true | 

# Home

## <font color="blue">Home Search</font>

> Request:

```json
{ 
"type": "1", 
"search": "abc",
"provinceId": "5",
"page": 1
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
				"isVip": 1
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
				"image_url": "dasfas",
				"isVip": 1
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
				"image_url": "dsfaasdf",
				"isVip": 1
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
				"isVip": 1
			}
		]
}
```

<font size="4"><b> 首页搜索</b></font>

### Method:   POST

### Path:   <font color="green">/home_search</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
type | int | true | 搜索类型 1.店铺 2.商品
search | string | true | 搜索值
provinceId | int | true | 省份id
page | int | true | 页数

### Response

Name | Type | Mandatory | Description
--------- | ----------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shops | array(shop object) | false | 店铺列表
products | array(product object) | false | 商品列表

#### Shop object

Name | Type | Mandatory | Description
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
image_url | string | false | 图片URL
isVip | int | true | 是否为vip 1.是 2.否

#### Product object

Name | Type | Mandatory | Description
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
isVip | int | true | 是否为vip 1.是 2.否

## <font color="blue">Get City By GPS</font>

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
"cityName": "西安",
"provinceId": 1,
"provinceName": "陕西"
}
```

<font size="4"><b> 通过经纬度定位城市</b></font>

### Method:   POST

### Path:   <font color="green">/get_city_by_gps</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
latitude | String | true | 纬度
longitude | String | true | 经度

### Response:

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 3.curl false 4.baidu map error
msg | String | true | 
cityId | String | true | 城市Id
cityName | String | true | 城市名称
provinceId | int | true | 省份Id
provinceName | string | true | 省份名称

## <font color="blue">Get Recommended Secondary Shop Types</font>

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

<font size="4"><b> 首页热门店铺类型</b></font>

### Method:   POST

### Path:   <font color="green">/home_secondary_shop_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
secondaryShopTypeList | Array(secondaryShopType object) | true | 热门店铺列表

### SecondaryShopType Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
secondary_shop_type_id | int | true | 店铺类型id
secondary_shop_type_name | string | true | 店铺类型名称
image_url | string | true | 图片url

## <font color="blue">Get Recommended Product Types</font>

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
"hotSaleProductTypeList": [
						{
							"id": 1,
							"name": "test",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						},
						{
							"id": 2,
							"name": "test",
							"image_url": "http://123.123.12.1/image_download/brand_logo_images/2.png"
						}
						]
}
```

<font size="4"><b> 首页热门商品类型</b></font>

### Method:   POST

### Path:   <font color="green">/home_hot_sale_product_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
hotSaleProductTypeList | Array(hotSaleProductType object) | true | 热门商品类型列表

### ProductType Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 热卖商品类型id
name | string | true | 热卖商品类型名称
image_url | string | true | 图片url

## <font color="blue">Get Province List</font>

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

<font size="4"><b> 获得地区列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_province_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
provinceList | Array(province object) | true | 省份列表

### Province Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
province_id | int | true | 省份id
province_name | string | true | 省份名称
cityList | Array(city object) | true | 城市列表

### City Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
city_id | int | true | 城市id
city_name | string | true | 城市名称

## <font color="blue">Home Products</font>

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
"promotion": {
				"productActivityId": 2,
				"productId": 1,
				"productName": "fjdskf",
				"startTime": "2013-10-12 12:00:00",
				"endTime": "2013-10-12 12:00:00",
				"imageUrl": "http://123.123.12.1/image_download/brand_logo_images/2.png"
				},
"group": {
				"productActivityId": 2,
				"productId": 1,
				"productName": "fjdskf",
				"startTime": "2013-10-12 12:00:00",
				"endTime": "2013-10-12 12:00:00",
				"imageUrl": "http://123.123.12.1/image_download/brand_logo_images/2.png"
				},
"promotion": {
				"productActivityId": 2,
				"productId": 1,
				"productName": "fjdskf",
				"imageUrl": "http://123.123.12.1/image_download/brand_logo_images/2.png"
				}
}
```

<font size="4"><b> 首页产品</b></font>

### Method:   POST

### Path:   <font color="green">/home_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | String | true | 省份Id

### Response:

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
status | int | true | 1.成功 3.curl false 4.baidu map error
msg | String | true | 
promotion | Promotion Object | true | 促销产品
group | Group Object | true | 团购产品
comsumable | Consumbale Object | true | 消耗品产品

### Promotion Object:

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productActivityId | int | true | 活动Id
productId | int | true | 产品Id
productName | String | true | 产品名称
startTime | Datetime | true | 开始时间
endTime | Datetime | true | 结束时间
imageUrl | string | true | 图片URL

### Group Object:

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productActivityId | int | true | 活动Id
productId | int | true | 产品Id
productName | String | true | 产品名称
startTime | Datetime | true | 开始时间
endTime | Datetime | true | 结束时间
imageUrl | string | true | 图片URL

### Consumable Object:

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productActivityId | int | true | 活动Id
productId | int | true | 产品Id
productName | String | true | 产品名称
imageUrl | string | true | 图片URL

# General

## <font color="blue">Get Ad List</font>

> Request:

```json
{
"provinceId": 1,
"locationId": 1,
"secondaryShopTypeId": 1,
"sectionId": 1
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

<font size="4"><b> 获得广告列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_ads</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
locationId | int | true | 广告位置Id(1:首页1 2:首页2 3:展区 4:互动 5:单品 6:店铺二级类型)
secondaryShopTypeId | int | false | (二级店铺类型id)当广告位置是6时必填
sectionId | int | true | (展区id)当广告位置为3时必填

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
adList | Array(ad object) | true | 广告列表

### Ad Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
ad_id | int | true | 广告id
ad_name | string | false | 名称
ad_type | int | true | 广告类型(1:店铺 2:产品 3:url 4:店铺(仅显示名字))
adable_id | int | true | 广告实体id(商店Id或产品Id)
ad_url | string | false | 若广告类型为3,为url地址
image_url | string | false | 若广告类型为1,2,3,为广告图片

## <font color="blue">Get User Status</font>

> Request:

```json
{
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"user_status": 2
}
```

<font size="4"><b> 获得用户类型</b></font>

### Method:   POST

### Path:   <font color="green">/get_user_status</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
user_status | int | true | 用户类型 1.普通用户 2.普通商户 3.vip商户 4.参展厂商 5.正在申请商铺 6.正在申请展会

## <font color="blue">Get Comments By Type</font>

> Request:

```json
{
"topicType": 1,
"topicId": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"commentList": [
						{
							"id": 1,
							"content": "内容1",
							"createdTime": "2016-05-05 17:33:00",
							"commentFromId": 1,
							"commentFromName": "fdsa",
							"commentFromImage": "http://121.12.11.11/image_download/brand_logo_images/2",
							"nestedCommentList": [
													{
														"id": 1,
														"content": "内容1",
														"createdTime": "2016-05-05 17:33:00",
														"commentFromId": 1,
														"commentFromName": "fdsa",
														"commentFromImage": "http://121.12.11.11/image_download/brand_logo_images/2",
														"commentToId": 1,
														"commentToName": "fdsa",
														"commentToImage": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"content": "内容1",
														"createdTime": "2016-05-05 17:33:00",
														"commentFromId": 1,
														"commentFromName": "fdsa",
														"commentFromImage": "http://121.12.11.11/image_download/brand_logo_images/2",
														"commentToId": 1,
														"commentToName": "fdsa",
														"commentToImage": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 2,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 2,
							"content": "内容1",
							"createdTime": "2016-05-05 17:33:00",
							"commentFromId": 1,
							"commentFromName": "fdsa",
							"commentFromImage": "http://121.12.11.11/image_download/brand_logo_images/2",
							"nestedCommentList": [
													{
														"id": 1,
														"content": "内容1",
														"createdTime": "2016-05-05 17:33:00",
														"commentFromId": 1,
														"commentFromName": "fdsa",
														"commentFromImage": "http://121.12.11.11/image_download/brand_logo_images/2",
														"commentToId": 1,
														"commentToName": "fdsa",
														"commentToImage": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"content": "内容1",
														"createdTime": "2016-05-05 17:33:00",
														"commentFromId": 1,
														"commentFromName": "fdsa",
														"commentFromImage": "http://121.12.11.11/image_download/brand_logo_images/2",
														"commentToId": 1,
														"commentToName": "fdsa",
														"commentToImage": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"imageList": [
											{
												"id": 3,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 4,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
			]
}
```

<font size="4"><b> 根据类型获得评论</b></font>

### Method:   POST

### Path:   <font color="green">/get_comments</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicType | int | true | 评论类型 1.产品评论 2.急件求购评论 3.急件转让评论 4.互动评论
topicId | int | true | 话题id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
commentList | Array(Comment object) | true | 评论列表

### Comment Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
content | string | true | 评论内容
createdTime | datetime | true | 评论时间
commentFromId | int | true | 评论人Id
commentFromName | string | true | 评论人名称
commentFromImage | string | true | 评论人图片url
nestedCommentList | Array(NestedComment Object) | false | 子评论列表(针对该评论的子评论)
imageList | Array(Image object) | true | 图片列表

### Nested Comment Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
content | string | true | 评论内容
createdTime | datetime | true | 评论时间
commentFromId | int | true | 评论人Id
commentFromName | string | true | 评论人名称
commentFromImage | string | true | 评论人图片url
commentToId | int | true | 评论对象Id
commentToName | string | true | 评论对象名称
commentToImage | string | true | 评论对象图片url

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Add Comment</font>

> Request:

```json
{
"topicType": 1,
"topicId": 1,
"userId": 1,
"content": "fdsf",
"commentToId": 2,
"innerCommentId": 3,
"imageList": [ "dfjdkasfjksadfj", "fkdsjfksdjf"]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"commentId": 2 
}
```

<font size="4"><b> 添加评论</b></font>

### Method:   POST

### Path:   <font color="green">/add_comment</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicType | int | true | 评论类型 1.订单评论 2.急件求购评论 3.急件转让评论 4.互动评论
topicId | int | true | 话题id
userId | int | true | 评论人Id
content | string | true | 内容1
commentToId | int | false | 评论对象Id, 若是给主题回复无需此参数, 若是给评论回复需此参数
innerCommentId | int | false | 父评论Id, 若是给主题回复无需此参数, 若是给评论回复需此参数
imageList | Array(String) | false | 图片列表(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
commentId | int | true | 评论Id

## <font color="blue">Add Like</font>

> Request:

```json
{
"topicType": 1,
"topicId": 1,
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"likeCount": 4 
}
```

<font size="4"><b> 点赞</b></font>

### Method:   POST

### Path:   <font color="green">/add_like</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicType | int | true | 评论类型 1.订单评论 2.急件求购评论 3.急件转让评论 4.互动评论
topicId | int | true | 话题id
userId | int | true | 评论人Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功 3.用户已对该话题点赞
msg | String | true | 
likeCount | int | true | 点赞次数

## <font color="blue">Get City List By Province</font>

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
"cityList": [
						{
							"id": 1,
							"name": "fadsf"
						},
						{
							"id": 2,
							"name": "fadsf"
						}
					]
}
```

<font size="4"><b> 根据省份获得城市列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_city_list_by_province</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
cityList | Array(City Object) | true | 职位类型

### City Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 城市Id;
name | string | true | 城市名称

## <font color="blue">Get Payment Params </font>

> Request:

```json
{
"userId": 3,
"paymentType": 1,
"paymentMethod": 2,
"amount": 15.00,
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"alipayData": {
					"service": "mobile.securitypay.pay",
					"partner": "03202390932",
					"_input_charset": "utf-8",
					"out_trade_no": "fskldafjsadkj",
					"subject": "fsdafkj",
					"payment_type": 1,
					"seller_id": "fdsfkjd@qq.com",
					"total_fee": 10,
					"body": "fsdafjksadj",
					"full": "_input_charset="utf-8"&body="用户ID-6:易配-申请展位"&notify_url="/app/alipay_notify_url.php"&out_trade_no="2016060217353313335"&partner="2088221980524436"&payment_type="1"&seller_id="1598881018@qq.com"&service="mobile.securitypay.pay"&subject="易配-申请展位"&total_fee="0.01"&sign="hF4xVV%2BbIUC8TW64tn8ctzperATjcevvzbveBYh0zRo6ffTkIvlTEE%2BBCRIu9kCNqGxNpHtmh710fo5H6NeIkpvdUCx239tyjbgbzkuzYbH76zEb777EsndqCk%2BbFrSV7weEq%2BYIrHnjTx4Nn3x8tX2NL8XQOZQd4Rc8l6167j0%3D"&sign_type="RSA""
				}
"wechatData:":{
					"appId": "909230293",
					"partnerId": "432423",
					"prepay_id": "jfksdjfk",
					"package": "fdsakfj",
					"noncestr": "fdsakfj",
					"timestamp": 2342342,
					"sign": "fksdfdsjafkjsadkfjsdaklfjsdaklfjsdkj"
				}
}
```

<font size="4"><b> 获得支付信息</b></font>

### Method:   POST

### Path:   <font color="green">/update_user_profile</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
paymentType | int | true | 支付场景 1.商品订单 2.展位 3.VIP
paymentMethod | int | true | 支付方式 1.支付宝 2.微信
amount | double | true | 金额

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |
alipayData | Alipay Object | false | 支付宝支付信息
wechatData | Wechat Object | false | 微信支付信息

### Alipay Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
service | string | true | 
partner | string | true |
_input_charset | string | true |
out_trade_no | string | true |
subject | string | true | 
payment_type | string | true | 
seller_id | string | true | 
total_fee | double | true | 
body | string | true | 
full | string | true | 拼接好签名的所有字符串

### Wechat Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
appId | string | true |
partnerId | string | true |
prepay_id | string | true | 
package | string | true | 
noncestr | string | true |
timestamp | string | true |
sign | string | true | 签名

# Shop

## <font color="blue">Get Shop Type List</font>

> Request:

```json
{
"provinceId": 1,
"search": "fdsaf"
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
												],
							"recommandedSecondaryShopTypeList": [
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
												],
							"recommandedSecondaryShopTypeList": [
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
}
```

<font size="4"><b> 获得店铺类别列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_shop_types</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
search | string | false | 搜索内容

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopTypeList | Array(Shop object) | true | 店铺类别列表

### Shop Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
primary_shop_type_id | int | true | 一级类别id
primary_shop_type_name | string | true | 一级类别名称
firstLetterList | Array(FirstLetter object) | true | 首字母列表
recommandedSecondaryShopTypeList | Array(SecondaryShopType object) | true | 热门二级类别

### FirstLetter Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
firstLetter | string | true | 首字母
secondaryShopTypeList | Array(SecondaryShopType object) | true | 二级类别列表

### SecondaryShopType Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
secondary_shop_type_id | int | true | 二级类别id
secondary_shop_type_name | string | true | 二级类别名称
image_url | string | true | 图片URL

## <font color="blue">Shop Type Search(depreciated)</font>

> Request:

```json
{
"search": "abc",
"page": 1
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
							"secondary_shop_type_name": "宝马",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"primary_shop_type_name": "小车"
						},
						{
							"secondary_shop_type_id": 2,
							"secondary_shop_type_name": "奔驰",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"primary_shop_type_name": "大车"
						}
			]
}
```

<font size="4"><b> 店铺类别搜索(不用)</b></font>

### Method:   POST

### Path:   <font color="green">/search_shop_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
search | string | true | 搜索内容
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
secondaryShopTypeList | Array(SecondaryShopType object) | true | 二级类别列表

### SecondaryLetter Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
secondary_shop_type_id | int | true | 二级类别id
secondary_shop_type_name | string | true | 二级类别名称
image_url | string | true | 图片URL
primary_shop_type_name | string | true | 一级类型名称

## <font color="blue">Get Shops By Secondary Shop Type</font>

> Request:

```json
{
"provinceId": 2,
"secondaryShopTypeId": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"shopList": [
						{
							"id": 1,
							"name": "标题1",
							"description": "内容1",
							"address": "小明",
							"isVip": 1,
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						},
						{
							"id": 2,
							"name": "标题1",
							"description": "内容1",
							"address": "小明",
							"isVip": 2,
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						}
			]
}
```

<font size="4"><b> 根据二级类别获得店铺列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_shops_by_secondary_shop_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
secondaryShopTypeId | int | true | 店铺二级类型Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopList | Array(Shop object) | true | 店铺列表

### Shop Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
description | string | true | 描述
address | string | true | 地址
isVip | int | true | 是否为vip 1.是 2.否
image_url | string | false | 图片URL

## <font color="blue">Get Shop Detail</font>

> Request:

```json
{
"shopId": 2,
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"shopDetail": {
					"id": 1,
					"name": "test",
					"service_time": "08:00-19:00",
					"collect_count": 12,
					"phone_1": "32423452",
					"phone_2": "23223252",
					"phone_3": "23542423",
					"address": "fsdafsadkfj",
					"sale_description": "fsdfjsdkfkfjasf",
					"description": "djfaksdjfkdsajfaks",
					"vipStartDate": "2016-05-05",
					"vipEndDate": "2016-10-05",
					"bannerList": [
										{
											"id": 1,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 2,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
				}
}
```

<font size="4"><b> 获得店铺详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_shop_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopDetail | Shop object | true | 店铺详情

### Shop Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
service_time | time | 营业时间
collect_count | int | 收藏人数
visit_count | int | 浏览人数
phone_1 | int | 电话1
phone_2 | int | 电话2
phone_3 | int | 电话3
sale_description | string | 主营描述
description | string | true | 描述
address | string | true | 地址
vipStartDate | date | false | vip起始时间
vipEndDate | date | false | vip结束时间
bannerList | Array(Image object) | false | 轮播图列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Collect Shop</font>

> Request:

```json
{
"shopId": 2,
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 收藏店铺</b></font>

### Method:   POST

### Path:   <font color="green">/collect_shop</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Register Shop</font>

> Request:

```json
{
"provinceId": 2,
"userId": 2,
"name": "fdsaf",
"address": "fdsafsda",
"type": 1,
"vipChargeId": 2,
"saleTypeList": [ 1, 2, 3],
"saleDescription": "fdsaf",
"phone_1": "fdsaf",
"phone_2": "fdsf",
"phone_3": "fdsf",
"wechat": "fdsaf",
"description": "fdsf",
"bankName": "fdsafdsa",
"bankAccount": "fdsafdas",
"license": "fdsjfksdjfkj",
"idFront": "fsdfdsafkj",
"idBack": "fdsafjk"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 注册店铺</b></font>

### Method:   POST

### Path:   <font color="green">/register_shop</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
userId | int | true | 用户Id
name | string | true | 名称
address | string | true | 地址
type | int | true | 1.普通店铺 2.VIP店铺
vipChargeId | int | false | VIP资费Id
saleTypeList | Array(int) | true | 主营类型id列表
saleDescription | string | true | 主营品牌
phone_1 | string | true | 联系电话
phone_2 | string | true | 订货电话
phone_3 | string | true | 技术咨询
wechat | string | true | 微信账号
description | string | true | 店铺描述
bankName | string | true | 收款账户银行
bankAccount | string | true | 收款账户账号
license | string | true | 营业执照图片(base64编码)
idFront | string | true | 身份证正面照片(base64编码)
idBack | string | true | 身份证反面照片(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get VIP Charges</font>

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
"chargeList": [
					{
						"id": 1,
						"name": "1 month",
						"price": 1000
					},
					{
						"id": 2,
						"name": "1 month",
						"price": 1500
					}
				]
}
```

<font size="4"><b> 获得VIP资费列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_vip_charge_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
chargeList | Array(ExhibitionCharge Object) | true | VIP资费列表

### VIPCharge Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | VIP资费Id
name | String | true | 名称
price | int | true | 价格

## <font color="blue">Get Sale Types</font>

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
"saleTypeList": [
					{
						"id": 1,
						"name": "fsdafasdf",
						"secondaryShopTypeList": [
													{ 
														"id": 1,
														"name": "fdsf"
													},
													{ 
														"id": 2,
														"name": "fdsf"
													}
												]
					},
					{
						"id": 2,
						"name": "dfsdsaf",
						"secondaryShopTypeList": [
													{ 
														"id": 3,
														"name": "fdsf"
													},
													{ 
														"id": 4,
														"name": "fdsf"
													}
												]
					}
				]
}
```

<font size="4"><b> 获得主营类型列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_sale_type_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
saleTypeList | Array(PrimaryShopType Object) | true | 一级类型列表

### PrimaryShopType Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 一级类型Id
name | String | true | 一级类型名称
secondaryShopTypeList | Array(SecondaryShopType Object) | true | 二级类型列表

### SecondaryShopType Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 二级类型Id
name | String | true | 二级类型名称

## <font color="blue">Update Recommended Products</font>

> Request:

```json
{
"shopId": 1,
"recommendedProductIdList": [1, 2, 3]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新店主推荐商品</b></font>

### Method:   POST

### Path:   <font color="green">/update_recommended_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 店铺Id
recommendedProductIdList | Array(int) | true | 推荐产品Id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get Secondary Shop Type List</font>

> Request:

```json
{
"shopId": 3
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"secondaryShopTypeList": [
							{
								"id": 1,
								"name": "fsdafasdf"
							},
							{
								"id": 2,
								"name": "dfsdsaf"
							}
						]
}
```

<font size="4"><b> 获得店铺二级类型列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_secondary_shop_type_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
secondaryShopTypeList | Array(SecondaryShopType Object) | true | 二级类型列表

### SecondaryShopType Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 二级类型Id
name | String | true | 二级类型名称

## <font color="blue">Get My Shop Detail</font>

> Request:

```json
{
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"shopDetail": {
					"id": 1,
					"name": "test",
					"service_time": "08:00-19:00",
					"collect_count": 12,
					"phone_1": "32423452",
					"phone_2": "23223252",
					"phone_3": "23542423",
					"address": "fsdafsadkfj",
					"sale_description": "fsdfjsdkfkfjasf",
					"description": "djfaksdjfkdsajfaks",
					"wechat": "fdsfj",
					"vipStartDate": "2016-05-05",
					"vipEndDate": "2016-10-05",
					"bannerList": [
										{
											"id": 1,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 2,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
				}
}
```

<font size="4"><b> 获得我的店铺详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_shop_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopDetail | Shop object | true | 店铺详情

### Shop Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
service_time | time | true | 营业时间
collect_count | int | true | 收藏人数
visit_count | int | true | 浏览人数
phone_1 | int | false | 电话1
phone_2 | int | false | 电话2
phone_3 | int | false | 电话3
sale_description | string | true | 主营描述
description | string | true | 描述
address | string | true | 地址
wechat | string | false | 微信账号
vipStartDate | date | false | vip起始时间
vipEndDate | date | false | vip结束时间
bannerList | Array(Image object) | false | 轮播图列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Update Shop Info</font>

> Request:

```json
{
"provinceId": 2,
"shopId": 2,
"name": "fdsaf",
"address": "fdsafsda",
"vipChargeId": 2,
"saleDescription": "fdsaf",
"phone_1": "fdsaf",
"phone_2": "fdsf",
"phone_3": "fdsf",
"wechat": "fdsaf",
"description": "fdsf",
"bankName": "fdsafdsa",
"bankAccount": "fdsafdas"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新店铺信息</b></font>

### Method:   POST

### Path:   <font color="green">/update_shop_info</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
shopId | int | true | 店铺Id
name | string | true | 名称
address | string | true | 地址
vipChargeId | int | false | VIP资费Id
saleDescription | string | true | 主营品牌
phone_1 | string | true | 联系电话
phone_2 | string | true | 订货电话
phone_3 | string | true | 技术咨询
wechat | string | true | 微信账号
description | string | true | 店铺描述
bankName | string | true | 收款账户银行
bankAccount | string | true | 收款账户账号

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Update Shop Images</font>

> Request:

```json
{
"shopId": 3,
"imageList": ["fdksajfksadjfksdaj", "fdsaklfjksdajfk"],
"existingImageIdList": [1, 3, 4]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新店铺图片</b></font>

### Method:   POST

### Path:   <font color="green">/update_shop_images</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id
imageList | Array(String) | false | 新增图片列表(base64编码)
existingImageIdList | Array(int) | true | 原有保留图片Id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Product

## <font color="blue">Get Owner Recommended Products</font>

> Request:

```json
{
"shopId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"productList": [
						{
							"id": 1,
							"name": "标题1",
							"original_price": 15.8,
							"price": "10.00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"description": "abc",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						},
						{
							"id": 2,
							"name": "标题1",
							"original_price": 15.8,
							"price": "10.00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"description": "abc",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						}
			]
}
```

<font size="4"><b> 获店长推荐商品</b></font>

### Method:   POST

### Path:   <font color="green">/get_owner_recommended_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productList | Array(Product object) | true | 商品列表

### Product Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
original_price | double | true | 原价
price | double | true | 现价
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
description | string | false | 描述
image_url | string | false | 图片URL

## <font color="blue">Get Product Type List By Shop</font>

> Request:

```json
{
"shopId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"productTypeList": [
						{
							"id": 1,
							"name": "name a",
							"productList": [
													{
														"id": 1,
														"name": "标题1",
														"original_price": 15.8,
														"price": "10.00",
														"brand": "BMW",
														"spec": "3*4",
														"model": "a",
														"car_model": "Benze",
														"description": "abc",
														"is_recommended": 1,
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"name": "标题1",
														"original_price": 15.8,
														"price": "10.00",
														"brand": "BMW",
														"spec": "3*4",
														"model": "a",
														"car_model": "Benze",
														"description": "abc",
														"is_recommended": 0,
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
										]
						},
						{
							"id": 2,
							"name": "name b",
							"productList": [
													{
														"id": 3,
														"name": "标题1",
														"original_price": 15.8,
														"price": "10.00",
														"brand": "BMW",
														"spec": "3*4",
														"model": "a",
														"car_model": "Benze",
														"description": "abc",
														"is_recommended": 1,
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 4,
														"name": "标题1",
														"original_price": 15.8,
														"price": "10.00",
														"brand": "BMW",
														"spec": "3*4",
														"model": "a",
														"car_model": "Benze",
														"description": "abc",
														"is_recommended": 1,
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
										]
						}
					]

}
```

<font size="4"><b> 获得产品类型列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_product_types_by_shop</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productTypeList | Array(ProductType object) | true | 商品类型列表

### ProductType Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 类型id
name | string | true | 类型名称
productList | Array(Product object) | true | 产品列表

### Product Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
original_price | double | true | 原价
price | double | true | 现价
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
description | string | false | 描述
is_recommended | int | true | 1.推荐产品 0.未推荐
image_url | string | false | 图片URL

## <font color="blue">Get Product Detail</font>

> Request:

```json
{
"productId": 1,
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"productDetail": [
						{
							"id": 1,
							"name": "标题1",
							"original_price": 15.8,
							"price": "10.00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"item_number": "fasdfaf",
							"customized_name_1": "abc",
							"customized_name_2": "abc",
							"customized_name_3": "abc",
							"customized_value_1": "abc",
							"customized_value_2": "abc",
							"customized_value_3": "abc",
							"description": "abc",
							"shop_id": 2,
							"shop_address": "afasdf",
							"phone_1": "1212412",
							"phone_2": "1212412",
							"phone_3": "1212412",
							"bannerImageList": [
													{
														"id": 1,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"referenceImageList": [
													{
														"id": 1,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"sampleComment": {
												"id": 1,
												"user_phone": "32424342",
												"content": "fasdfjsadkfj",
												"created_time": "2016-05-15 15:00:00",
												"imageList": [
																{
																	"id": 1,
																	"url": "http://121.12.11.11/image_download/brand_logo_images/2"
																},
																{
																	"id": 2,
																	"url": "http://121.12.11.11/image_download/brand_logo_images/2"
																}
															]
												}
						}
					]

}
```

<font size="4"><b> 获得产品详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_product_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productId | int | true | 产品Id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productDetail | Array(Product object) | true | 商品类型列表

### Product Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
original_price | double | true | 原价
price | double | true | 现价
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
item_number | string | false | 零件号
customized_name_1 | string | false | 自定义属性1名称
customized_name_2 | string | false | 自定义属性2名称
customized_name_3 | string | false | 自定义属性3名称
customized_value_1 | string | false | 自定义属性1值
customized_value_2 | string | false | 自定义属性2值
customized_value_3 | string | false | 自定义属性3值
description | string | false | 描述
shop_id | int | true | 店铺Id
shop_address | string | true | 店铺地址
phone_1 | string | true |  联系电话
phone_1 | string | true |  订货电话
phone_1 | string | true |  技术咨询
inventory | int | true |  库存
bannerImageList | Array(Image object) | false | 轮播图列表
referenceImageList | Array(Image object) | false | 参考图列表
sampleComment | Comment object | false | 评论实例

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

### Comment Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
user_phone | string | true | 评论人
content | string | true | 内容
created_time | datetime | true | 评论时间
imageList | Array(Image object) | true | 图片列表

## <font color="blue">Get Product Comments</font>

> Request:

```json
{
"productId": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"commentList": [
						{
							"id": 1,
							"user_phone": "2312412411",
							"content": "内容1",
							"created_time": "2016-05-05 17:33:00",
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 2,
							"user_phone": "2312412411",
							"content": "内容1",
							"created_time": "2016-05-05 17:33:00",
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
			]
}
```

<font size="4"><b> 获得产品评论</b></font>

### Method:   POST

### Path:   <font color="green">/get_product_comments</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productId | int | true | 产品id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
commentList | Array(Comment object) | true | 评论列表

### Comment Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
user_phone | string | true | 评论人电话
content | string | true | 评论内容
created_time | datetime | true | 评论时间
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Get Guess Products</font>

> Request:

```json
{
"productId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"productList": [
						{
							"id": 1,
							"name": "标题1",
							"price": "10.00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"sold_count": 100,
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						},
						{
							"id": 2,
							"name": "标题1",
							"price": "10.00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"sold_count": 100,
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						}
				]

}
```

<font size="4"><b> 获得猜你喜欢产品</b></font>

### Method:   POST

### Path:   <font color="green">/get_guess_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productId | int | true | 商品Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productList | Array(Product object) | true | 商品列表

### ProductType Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
price | double | true | 现价
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
sold_count | int | true | 销售数量
image_url | string | true | 图片URL

## <font color="blue">Get Consumable Products</font>

> Request:

```json
{
"provinceId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"productList": [
						{
							"id": 1,
							"name": "标题1",
							"price": "10.00",
							"original_price": "12.00",
							"shop_name": "afsadf",
							"shop_address": "dfasfasdf",
							"is_vip": 1,
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						},
						{
							"id": 2,
							"name": "标题1",
							"price": "10.00",
							"original_price": "12.00",
							"shop_name": "afsadf",
							"shop_address": "dfasfasdf",
							"is_vip": 1,
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						}
				]

}
```

<font size="4"><b> 获得消耗品</b></font>

### Method:   POST

### Path:   <font color="green">/get_consumbale_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productList | Array(Product object) | true | 商品列表

### ProductType Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
price | double | true | 现价
original_price | string | true | 原价
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
is_vip | int | true | 是否为vip 1:是 0:否
image_url | string | true | 图片URL

## <font color="blue">Collect Product</font>

> Request:

```json
{
"productId": 2,
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 收藏商品</b></font>

### Method:   POST

### Path:   <font color="green">/collect_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productId | int | true | 商品Id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Add Product Type</font>

> Request:

```json
{
"shopId": 2,
"productTypeName": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 添加货架</b></font>

### Method:   POST

### Path:   <font color="green">/add_product_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id
productTypeName | int | true | 货架名称

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Delete Product Type</font>

> Request:

```json
{
"productTypeId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除货架</b></font>

### Method:   POST

### Path:   <font color="green">/delete_product_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productTypeId | int | true | 货架Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Add Product</font>

> Request:

```json
{
"productTypeId": 2,
"secondaryShopTypeId": 2,
"name": "test",
"originalPrice": 20,
"price": 14.5,
"brand": "asdfb",
"spec": "dfasf",
"model": "fdsaf",
"carModel": "fdsaf",
"itemNo": "fdsaf",
"customizedName1": "fsdaf",
"customizedName2": "fdsaf",
"customizedName3": "fdsaf",
"customizedValue1": "fdsaf",
"customizedValue2": "fdsaf",
"customizedValue3": "fdsaf",
"description": "fdsf",
"firstImage": "fdsafksdajf",
"bannerImageList": [ "fdsajkfjsdak", "jfdsklafjdsk"],
"referenceImageList": [ "fdsakfjsda", "fjdksafj"]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 添加产品</b></font>

### Method:   POST

### Path:   <font color="green">/add_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
productTypeId | int | true | 货架Id
secondaryShopTypeId | int | true | 店铺二级类型id
name | string | true | 产品名称
originalPrice | double | true | 原价
price | double | true | 价格
brand | string | true | 品牌
spec | string | true | 规格
model | string | true | 型号
carModel | string | true | 车型
itemNo | string | true | 零件号
customizedName1 | string | true | 自定义类型名称1
customizedName2 | string | true | 自定义类型名称2
customizedName3 | string | true | 自定义类型名称3
description | string | true | 商品描述
firstImage | string | true | 首页图片(base64编码)
bannerImageList | Array(string) | true | 轮播图列表(base64编码)
referenceImageList | Array(string) | true | 参考图列表(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Product Activity

## <font color="blue">Get Group Activities</font>

> Request:

```json
{
"provinceId": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"groupActivityList": [
						{
							"id": 1,
							"product_id": 2,
							"product_name": "abc",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"original_price": 15,
							"group_price": 10,
							"condition_count": 100,
							"current_count": 10,
							"per_limit": 2,
							"start_time": "2016-05-05 21:00:00",
							"end_time": "2016-05-06 21:00:00"
						},
						{
							"id": 2,
							"product_id": 3,
							"product_name": "abc",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"original_price": 15,
							"group_price": 10,
							"condition_count": 100,
							"current_count": 10,
							"per_limit": 2,
							"start_time": "2016-05-05 21:00:00",
							"end_time": "2016-05-06 21:00:00"
						}
			]
}
```

<font size="4"><b> 获得团购活动</b></font>

### Method:   POST

### Path:   <font color="green">/get_group_activities</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
groupActivityList | Array(GroupActivity object) | true | 团购活动列表

### GroupActivity Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 活动id
product_id | int | true | 商品Id
product_name | string | true | 商品名称
image_url | string | true | 商品图片地址
original_price | double | true | 原价
group_price | double | true | 团购价
condition_count | int | true | 团购总数
current_count | int | true | 当前团购数量
per_limit | int | false | 每人限购
start_time | datetime | true | 开始时间
end_time | datetime | true | 结束时间

## <font color="blue">Get Group Activity Detail</font>

> Request:

```json
{
"activityId": 1,
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"groupActivityDetail": [
						{
							"id": 1,
							"product_id": 2,
							"shop_id": 2,
							"shop_name": "djfak",
							"shop_address": "fadsfj",
							"phone_1": "32423342",
							"phone_2": "32423342",
							"phone_3": "32423342",
							"product_name": "标题1",
							"original_price": 15.8,
							"group_price": "10.00",
							"condition_count": 100,
							"current_count": 10,
							"per_limit": 2,
							"start_time": "2016-05-05 14:00:00",
							"end_time": "2016-05-06 14:00:00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"item_number": "fasdfaf",
							"customized_name_1": "abc",
							"customized_name_2": "abc",
							"customized_name_3": "abc",
							"customized_value_1": "abc",
							"customized_value_2": "abc",
							"customized_value_3": "abc",
							"quantity": 30,
							"bannerImageList": [
													{
														"id": 1,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"referenceImageList": [
													{
														"id": 1,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"sampleComment": {
												"id": 1,
												"user_phone": "32424342",
												"content": "fasdfjsadkfj",
												"created_time": "2016-05-15 15:00:00",
												"imageList": [
																{
																	"id": 1,
																	"url": "http://121.12.11.11/image_download/brand_logo_images/2"
																},
																{
																	"id": 2,
																	"url": "http://121.12.11.11/image_download/brand_logo_images/2"
																}
															]
												}
						}
					]

}
```

<font size="4"><b> 获得团购活动详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_group_activity_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
activityId | int | true | 活动Id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
groupActivityDetail | Array(GroupActivity object) | true | 商品类型列表

### GroupActivity Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 活动id
product_id | int | true | 商品Id
shop_id | int | true | 店铺Id
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
phone_1 | string | true | 电话1
phone_2 | string | true | 电话2
phone_3 | string | true | 电话3
product_name | string | true | 商品名称
original_price | double | true | 原价
group_price | double | true | 团购价
condition_count | int | true | 团购总量
current_count | int | true | 当前团购数量
per_limit | int | true | 个人限购
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
item_number | string | false | 零件号
customized_name_1 | string | false | 自定义属性1名称
customized_name_2 | string | false | 自定义属性2名称
customized_name_3 | string | false | 自定义属性3名称
customized_value_1 | string | false | 自定义属性1值
customized_value_2 | string | false | 自定义属性2值
customized_value_3 | string | false | 自定义属性3值
start_time | datetime | true | 开始时间
end_time | datetime | true | 结束时间
inventory | int | true |  库存
bannerImageList | Array(Image object) | false | 轮播图列表
referenceImageList | Array(Image object) | false | 参考图列表
sampleComment | Comment object | false | 评论例子

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

### Comment Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
user_phone | string | true | 评论人
content | string | true | 内容
created_time | datetime | true | 评论时间
imageList | Array(Image object) | true | 图片列表

## <font color="blue">Get Promotion Activities</font>

> Request:

```json
{
"provinceId": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"promotionActivityList": [
						{
							"id": 1,
							"product_id": 3,
							"product_name": "abc",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"original_price": 15,
							"promotion_price": 10,
							"shop_name": "fajsdkf",
							"shop_address": "dfasfdasf",
							"status": 2,
							"time_remaining": "1天 12:00:12",
							"start_time": "2016-05-05 12:00:00",
							"end_time": "2016-05-05 12:00:00"
						},
						{
							"id": 2,
							"product_id": 3,
							"product_name": "abc",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"original_price": 15,
							"promotion_price": 10,
							"shop_name": "fajsdkf",
							"shop_address": "dfasfdasf",
							"status": 2,
							"time_remaining": "1天 12:00:12",
							"start_time": "2016-05-05 12:00:00",
							"end_time": "2016-05-05 12:00:00"
						}
			]
}
```

<font size="4"><b> 获得促销活动</b></font>

### Method:   POST

### Path:   <font color="green">/get_promotion_activities</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
promotionActivityList | Array(PromotionActivity object) | true | 团购活动列表

### PromotionActivity Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 活动id
product_id | int | true | 商品Id
product_name | string | true | 商品名称
image_url | string | true | 商品图片地址
original_price | double | true | 原价
promotion_price | double | true | 促销价
shop_name | string | true | 商店名称
shop_address | string | true | 商店地址
time_remaining | time | true | 剩余时间
start_time | datetime | true | 活动开始时间
end_time | datetime | true | 活动结束时间

## <font color="blue">Get Promotion Activity Detail</font>

> Request:

```json
{
"activityId": 1,
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"promotionActivityDetail": [
						{
							"id": 1,
							"product_id": 3,
							"shop_id": 2,
							"shop_name": "djfak",
							"shop_address": "fadsfj",
							"phone_1": "32423342",
							"phone_2": "32423342",
							"phone_3": "32423342",
							"product_name": "标题1",
							"original_price": 15.8,
							"promotion_price": "10.00",
							"time_remaining": "1天 12:00:12",
							"start_time": "2016-05-05 14:00:00",
							"end_time": "2016-05-06 14:00:00",
							"brand": "BMW",
							"spec": "3*4",
							"model": "a",
							"car_model": "Benze",
							"item_number": "fasdfaf",
							"customized_name_1": "abc",
							"customized_name_2": "abc",
							"customized_name_3": "abc",
							"customized_value_1": "abc",
							"customized_value_2": "abc",
							"customized_value_3": "abc",
							"quantity": 30,
							"bannerImageList": [
													{
														"id": 1,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"referenceImageList": [
													{
														"id": 1,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													},
													{
														"id": 2,
														"url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
												],
							"sampleComment": {
												"id": 1,
												"user_phone": "32424342",
												"content": "fasdfjsadkfj",
												"created_time": "2016-05-15 15:00:00",
												"imageList": [
																{
																	"id": 1,
																	"url": "http://121.12.11.11/image_download/brand_logo_images/2"
																},
																{
																	"id": 2,
																	"url": "http://121.12.11.11/image_download/brand_logo_images/2"
																}
															]
												}
						}
					]

}
```

<font size="4"><b> 获得促销活动详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_promotion_activity_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
activityId | int | true | 活动Id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
promotionActivityDetail | Array(GroupActivity object) | true | 商品类型列表

### GroupActivity Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 活动id
shop_id | int | true | 店铺Id
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
phone_1 | string | true | 电话1
phone_2 | string | true | 电话2
phone_3 | string | true | 电话3
product_name | string | true | 商品名称
original_price | double | true | 原价
promotion_price | double | true | 促销价
time_remaining | string | true | 剩余时间
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
item_number | string | false | 零件号
customized_name_1 | string | false | 自定义属性1名称
customized_name_2 | string | false | 自定义属性2名称
customized_name_3 | string | false | 自定义属性3名称
customized_value_1 | string | false | 自定义属性1值
customized_value_2 | string | false | 自定义属性2值
customized_value_3 | string | false | 自定义属性3值
start_time | datetime | true | 开始时间
end_time | datetime | true | 结束时间
inventory | int | true |  库存
bannerImageList | Array(Image object) | false | 轮播图列表
referenceImageList | Array(Image object) | false | 参考图列表
sampleComment | Comment object | false | 评论例子

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

### Comment Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
user_phone | string | true | 评论人
content | string | true | 内容
created_time | datetime | true | 评论时间
imageList | Array(Image object) | true | 图片列表

# Topic

## <font color="blue">Get Topics By Category</font>

> Request:

```json
{
"provinceId": 1,
"topicTypeId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"topicList": [
						{
							"id": 1,
							"topic_type_id": 1,
							"topic_type_name": "ttest",
							"content": "内容1",
							"user_name": "小明",
							"user_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"created_time": "2016-05-05 17:33:00",
							"comment_count": 10,
							"like_count": 3,
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 1,
							"topic_type_id": 1,
							"topic_type_name": "ttest",
							"content": "内容1",
							"user_name": "小明",
							"user_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"created_time": "2016-05-05 17:33:00",
							"comment_count": 10,
							"like_count": 3,
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						}
			]
}
```

<font size="4"><b> 根据类型获得帖子</b></font>

### Method:   POST

### Path:   <font color="green">/get_topics_by_category</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
topicTypeId | int | true | 帖子类型Id, 1~5
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
topicList | Array(Topic object) | true | 帖子列表

### Topic Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 帖子id
topic_type_id | int | true | 帖子类型Id
topic_type_name | string | true | 帖子类型名称
content | string | true | 帖子内容
user_name | string | true | 发帖人名字
user_url | string | true | 发帖人头像
created_time | string | true | 发布时间
comment_count | int | true | 评价次数
like_count | int | true | 点赞次数
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Get Topic Detail</font>

> Request:

```json
{
"topicId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"topicDetail": {
					"topicTypeName": "ttest",
					"content": "内容1",
					"likeCount": 13,
					"commentCount": 13,
					"createdTime": "2016-05-05 17:33:00",
					"imageList": [
									{
										"id": 1,
										"url": "http://121.12.11.11/image_download/brand_logo_images/2"
									},
									{
										"id": 1,
										"url": "http://121.12.11.11/image_download/brand_logo_images/2"
									}
								]
				}
}
```

<font size="4"><b> 获得帖子详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_topic_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicId | int | true | 帖子Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
topicDetail | Topic object | true | 帖子详情

### Topic Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
topicTypeName | string | true | 帖子类型名称
content | string | true | 帖子内容
createdTime | string | true | 发布时间
commentCount | int | true | 评价次数
likeCount | int | true | 点赞次数
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Publish Topic</font>

> Request:

```json
{
"topicTypeId": 3,
"content": "内容1",
"userId": 5,
"provinceId": 2,
"imageList": [ "dsafsdafasdfsadfa", "fsdafdsafsadfasf"]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"topicId": 3
}
```

<font size="4"><b> 发布帖子</b></font>

### Method:   POST

### Path:   <font color="green">/publish_topic</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicTypeId | int | true | 帖子类型Id
content | string | true | 帖子内容
userId | int | true | 发布人Id
provinceId | int | true | 省份Id
imageList | Array(String) | false | 图片列表(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
topicId | int | true | 帖子Id

## <font color="blue">Get My Topics</font>

> Request:

```json
{
"userId": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"topicList": [
						{
							"id": 1,
							"topic_type_id": 1,
							"topic_type_name": "ttest",
							"content": "内容1",
							"user_name": "小明",
							"user_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"created_time": "2016-05-05 17:33:00",
							"comment_count": 10,
							"like_count": 3,
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 1,
							"topic_type_id": 1,
							"topic_type_name": "ttest",
							"content": "内容1",
							"user_name": "小明",
							"user_url": "http://121.12.11.11/image_download/brand_logo_images/2",
							"created_time": "2016-05-05 17:33:00",
							"comment_count": 10,
							"like_count": 3,
							"imageList": [
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 1,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						}
			]
}
```

<font size="4"><b> 获得我的帖子</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_topics</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
topicList | Array(Topic object) | true | 帖子列表

### Topic Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 帖子id
topic_type_id | int | true | 帖子类型Id
topic_type_name | string | true | 帖子类型名称
content | string | true | 帖子内容
user_name | string | true | 发帖人名字
user_url | string | true | 发帖人头像
created_time | string | true | 发布时间
comment_count | int | true | 评价次数
like_count | int | true | 点赞次数
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Delete Topic</font>

> Request:

```json
{
"topicId": 3
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除帖子</b></font>

### Method:   POST

### Path:   <font color="green">/delete_topic</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicId | int | true | 帖子Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Cart

## <font color="blue">Get Cart Detail</font>

> Request:

```json
{
"cartId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"total_quantity": 20,
"total_amount": 100.00,
"cartItemGroups": [
						{
							"shop_id": 1,
							"shop_name": "标题1",
							"shop_address": "dfasdfasf",
							"shop_quantity": 10,
							"shop_amount": 100.00,
							"cartItemList": [
												{
													"cart_item_id": 1,
													"product_id": 1,
													"product_name": "abce",
													"product_brand": "abc",
													"product_spec": "adb",
													"quantity": 4,
													"product_activity_id": 4,
													"price": 4.00,
													"cart_item_amount": 16.00,
													"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
												},
												{
													"cart_item_id": 2,
													"product_id": 2,
													"product_name": "abce",
													"product_brand": "abc",
													"product_spec": "adb",
													"quantity": 4,
													"product_activity_id": 4,
													"price": 4.00,
													"cart_item_amount": 16.00,
													"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
												}
											]
						},
						{
							"shop_id": 2,
							"shop_name": "标题1",
							"shop_address": "dfasdfasf",
							"shop_quantity": 10,
							"shop_amount": 100.00,
							"cartItemList": [
												{
													"cart_item_id": 3,
													"product_id": 3,
													"product_name": "abce",
													"product_brand": "abc",
													"product_spec": "adb",
													"quantity": 4,
													"price": 4.00,
													"cart_item_amount": 16.00,
													"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
												},
												{
													"cart_item_id": 4,
													"product_id": 4,
													"product_name": "abce",
													"product_brand": "abc",
													"product_spec": "adb",
													"quantity": 4,
													"price": 4.00,
													"cart_item_amount": 16.00,
													"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
												}
											]
						},
			]
}
```

<font size="4"><b> 获得购物车详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_cart_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
cartId | int | true | 购物车id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
total_quantity | int | true | 产品总数
total_amount | double | true | 产品总金额
cartItemGroups | Array(CartItemGroup object) | true | 购物车店铺列表

### CartItemGroup Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
shop_id | int | true | 店铺id
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
shop_quantity | string | true | 购物车内店铺售卖数量
shop_amount | string | true | 购物车内店铺售卖金额
cartItemList | Array(CartItem object) | true | 购物车内店铺售卖产品列表

### CartItem Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
cart_item_id | int | true | 购物车条目id
product_id | int | true | 产品Id
product_name | string | true | 产品名称
product_brand | string | false | 产品品牌
product_spec | string | false | 产品规格
quantity | int | true | 数量
product_activity_id | int | false | 活动Id
price | double | true | 价格
cart_item_amount | double | true | 金额
image_url | string | true | 产品图片地址

## <font color="blue">Update Cart Item</font>

> Request:

```json
{
"cartId": 1,
"productId": 1,
"quantity": 3,
"productActivityId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新购物车条目</b></font>

### Method:   POST

### Path:   <font color="green">/update_cart_item</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
cartId | int | true | 购物车id
productId | int | true | 产品id
quantity | int | true | 数量
productActivityId | int | false | 活动id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Remove Cart Item</font>

> Request:

```json
{
"cartItemId": 1,
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除购物车条目</b></font>

### Method:   POST

### Path:   <font color="green">/remove_cart_item</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
cartItemId | int | true | 购物车条目id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Remove Cart Items</font>

> Request:

```json
{
"cartItemIdList": [1, 2, 3]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除购物车条目(多条)</b></font>

### Method:   POST

### Path:   <font color="green">/remove_cart_items</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
cartItemIdList | Array(int) | true | 购物车条目id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Delivery Address

## <font color="blue">Get Delivery Addresses By User</font>

> Request:

```json
{
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"deliveryAddressList": [
							{
								"id": 1,
								"contact_person": "abc",
								"phone": "23243242",
								"address": "r5fsdkfjdskfj",
								"is_default": 0
							},
							{
								"id": 2,
								"contact_person": "abc",
								"phone": "23243242",
								"address": "r5fsdkfjdskfj",
								"is_default": 0
							}
						]
}
```

<font size="4"><b> 获得配送地址列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_delivery_addresses_by_user</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
deliveryAddressList | Array(DeliveryAddress object) | true | 配送地址列表

### DeliveryAddress object:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 配送地址id
contact_person | String | true | 联系人
phone | string | true | 电话
address | string | true | 地址
is_default | int | true | 是否为默认收货地址 1:是 0:否

## <font color="blue">Add Delivery Address</font>

> Request:

```json
{
"userId": 1,
"contactPerson": "asdf",
"phone": "21323",
"address": "fadsfas"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 添加配送地址</b></font>

### Method:   POST

### Path:   <font color="green">/add_delivery_address</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id
contactPerson | String | true | 联系人
phone | string | true | 电话
address | string | true | 地址

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Update Delivery Address</font>

> Request:

```json
{
"deliveryAddressId": 1,
"contact_person": "asdf",
"phone": "21323",
"address": "fadsfas"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新配送地址</b></font>

### Method:   POST

### Path:   <font color="green">/update_delivery_address</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
deliveryAddressId | int | true | 配送地址id
contact_person | String | true | 联系人
phone | string | true | 电话
address | string | true | 地址

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Set Default Delivery Address</font>

> Request:

```json
{
"deliveryAddressId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 设置默认配送地址</b></font>

### Method:   POST

### Path:   <font color="green">/set_default_delivery_address</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
deliveryAddressId | int | true | 配送地址id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Delete Delivery Address</font>

> Request:

```json
{
"deliveryAddressId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除配送地址</b></font>

### Method:   POST

### Path:   <font color="green">/delete_delivery_address</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
deliveryAddressId | int | true | 配送地址id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Get Default Delivery Address</font>

> Request:

```json
{
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"defaultDeliveryAddress": {
								"id": 1,
								"contact_person": "abc",
								"phone": "23243242",
								"address": "r5fsdkfjdskfj"
						}
}
```

<font size="4"><b> 获得默认配送地址</b></font>

### Method:   POST

### Path:   <font color="green">/get_default_delivery_address</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1:成功 3:无默认配送地址
msg | String | true | 
MandatoryDeliveryAddress | Array(DeliveryAddress object) | true | 配送地址

### DeliveryAddress object:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 配送地址id
contact_person | String | true | 联系人
phone | string | true | 电话
address | string | true | 地址

# Order

## <font color="blue">Create New Orders</font>

> Request:

```json
{
"cartItemIdList": [1, 2, 3]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 创建新订单</b></font>

### Method:   POST

### Path:   <font color="green">/create_new_orders</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
cartItemIdList | Array(int) | true | 购物车条目id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Attach Delivery Address To Orders</font>

> Request:

```json
{
"orderIdList": [1, 2, 3],
"deliveryAddressId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 给订单绑定配送地址</b></font>

### Method:   POST

### Path:   <font color="green">/attach_delivery_address_to_orders</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderIdList | Array(int) | true | 订单id列表
deliveryAddressId | int | true | 配送地址id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Attach Note To Orders</font>

> Request:

```json
{
"orderIdList": [1, 2, 3],
"note": "fdsa"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 给订单绑定备注</b></font>

### Method:   POST

### Path:   <font color="green">/attach_note_to_orders</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderIdList | Array(int) | true | 订单id列表
note | string | true | 备注

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Get Newly Created Orders</font>

> Request:

```json
{
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"total_quantity": 30,
"total_amount": 1000,
"orderList": [
				{
					"id": 1,
					"shop_name": "abc",
					"shop_address": "fasdfajsdkfl",
					"note": "fdsak",
					"quantity": 10,
					"amount": 10,
					"orderItemList": [
										{
											"id": 1,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 2,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
				},
				{
					"id": 2,
					"shop_name": "abc",
					"shop_address": "fasdfajsdkfl",
					"note": "fdsak",
					"quantity": 10,
					"amount": 10,
					"orderItemList": [
										{
											"id": 3,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 4,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
				}
			]
}
```

<font size="4"><b> 获得新建订单</b></font>

### Method:   POST

### Path:   <font color="green">/get_newly_created_orders</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |
total_quantity | int | true | 商品总数量
total_amount | double | true | 商品总额
orderList | Array(Order object) | true | 订单列表

### Ordre object

 Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 订单id
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
note | string | false | 备注
quantity | int | true | 店铺商品数量
amount | double | true | 店铺商品金额
orderItemList | Array(OrderItem object) | true | 订单条目列表

### OrdreItem object

 Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 订单条目id
product_id | string | true | 商品Id
product_name | string | true | 商品名称
quantity | int | true | 商品数量
amount | double | true | 商品金额
price | double | true | 商品价格
image_url | string | true | 商品图片Url

## <font color="blue">Get Orders By Type</font>

> Request:

```json
{
"userId": 1,
"orderType": 1,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"orderList": [
				{
					"id": 1,
					"order_status_id": 1,
					"shop_name": "abc",
					"shop_address": "fasdfajsdkfl",
					"note": "fdsak",
					"quantity": 10,
					"amount": 10,
					"created_time": "2016-05-05 12:00:00",
					"orderItemList": [
										{
											"id": 1,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 2,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
				},
				{
					"id": 2,
					"order_status_id": 2,
					"shop_name": "abc",
					"shop_address": "fasdfajsdkfl",
					"note": "fdsak",
					"quantity": 10,
					"amount": 10,
					"created_time": "2016-05-05 12:00:00",
					"orderItemList": [
										{
											"id": 3,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 4,
											"product_id": 1,
											"quantity": 20,
											"amount": 30,
											"price": 10,
											"product_name": "fdsaf",
											"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
				}
			]
}
```

<font size="4"><b> 根据类型获得订单</b></font>

### Method:   POST

### Path:   <font color="green">/get_orders_by_type</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id
orderType | int | true | 1:待付款 2:待发货 3:待收货 4:待评价 99:全部
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |
orderList | Array(Order object) | true | 订单列表

### Ordre object

 Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 订单id
order_status_id | int | true | 订单状态id 1:待付款 3,4:待发货 5:申请取消中 6:待收货 7:待评价 8:已完成 9:已取消
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
note | string | false | 备注
quantity | int | true | 店铺商品数量
amount | double | true | 店铺商品金额
created_time | datetime | true | 下单时间
orderItemList | Array(OrderItem object) | true | 订单条目列表

### OrdreItem object

 Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 订单条目id
product_id | string | true | 商品Id
product_name | string | true | 商品名称
quantity | int | true | 商品数量
amount | double | true | 商品金额
price | double | true | 商品价格
image_url | string | true | 商品图片Url

## <font color="blue">Rate Order</font>

> Request:

```json
{
"orderId": 1,
"content": "abcd",
"imageList": [
				"afjdsajfkasdjfksadfjksaldfjijkdfjkasdjfkasdjfkasldfj",
				"fjkadsjfksdajfkdsajfksdajfksdajfksadjfksdajfksdajfksdaf"
			]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 评价订单</b></font>

### Method:   POST

### Path:   <font color="green">/rate_order</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id
content | string | true | 内容
imageList | Array(string) | true | base64编码图片数组

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Receive Order</font>

> Request:

```json
{
"orderId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 确认收货</b></font>

### Method:   POST

### Path:   <font color="green">/receive_order</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Return Order</font>

> Request:

```json
{
"orderId": 1,
"cancelReason": "nothing"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 申请未发货订单退货</b></font>

### Method:   POST
### Path:   <font color="green">/return_order</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id
cancelReason | string | true | 退货理由

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Get Logistics Info</font>

> Request:

```json
{
"orderId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"logisticsInfo": {
					"deliveryInfo_id": 1,
					"logistics_id": "fdsajsdafjsadkfj",
					"logistics_company": "fsd",
					"delivery_time": "2016-05-11 15:10:00",
					"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
				}
}
```

<font size="4"><b> 获得物流详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_logistics_info</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |
logisticsInfo | Logistics object | true | 物流详情

### Logistics:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
deliveryInfo_id | int | true | 物流条目id
logistics_id | String | true | 物流编号
logistics_company | string | true | 物流公司
delivery_time | datetime | true | 发货时间
image_url | string | true | 发货单据图片地址

## <font color="blue">Cancel Order</font>

> Request:

```json
{
"orderId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 取消未支付订单</b></font>

### Method:   POST

### Path:   <font color="green">/cancel_order</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功 4.用户未设置微信或支付宝账号
msg | String | true |

## <font color="blue">Confirm Order Delivered</font>

> Request:

```json
{
"orderId": 1,
"logisticsId": "fdsaf",
"logisticsCompany": "fjdsalfj",
"image": "fdsajfk"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 确认发货</b></font>

### Method:   POST

### Path:   <font color="green">/confirm_order_delivered</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id
logisticsId | string | true | 物流订单Id
logisticsCompany | string | true | 物流公司
image | string | true | 发货单据照片(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Confirm Orders</font>

> Request:

```json
{
"orderIdList": [1, 2, 3]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 确认新订单</b></font>

### Method:   POST

### Path:   <font color="green">/order_confirmed</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderIdList | Array(int) | true | 订单id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Remind Order Delivery</font>

> Request:

```json
{
"orderId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 提醒发货</b></font>

### Method:   POST

### Path:   <font color="green">/remind_delivery</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
orderId | int | true | 订单id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Exhibition

## <font color="blue">Get Exhibition Factories</font>

> Request:

```json
{
"sectionId": 1,
"page": 1,
"provinceId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"exhibitionSpotList": [
						{
							"id": 1,
							"shop_id": 3,
							"name": "fsadf",
							"sale_description": "fdsafsa",
							"address": "fasdf",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						},
						{
							"id": 2,
							"shop_id": 3,
							"name": "fsadf",
							"sale_description": "fdsafsa",
							"address": "fasdf",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						}
					]
}
```

<font size="4"><b> 根据展区获得厂家展位</b></font>

### Method:   POST

### Path:   <font color="green">/get_exhibition_factory</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
sectionId | int | true | 展区id 1:小车配件 2:农用 3:大车 4:加装 5:汽车用品 6:电子产品 7:空调 8:灯具 9:其它 
page | int | true | 页数
provinceId | int | true | 省份Id, 99为全国

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
exhibitionSpotList | Array(Exhibition object) | true | 展位列表

### Exhibition Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 展位Id
shop_id | int | true | 店铺Id
name | String | true | 厂家名称
sale_description | String | true | 主营描述
address | string | true | 地址
image_url | string | true | 店铺图片

## <font color="blue">Get Exhibition Factory Detail</font>

> Request:

```json
{
"exhibitionSpotId": 2,
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"exhibitionSpot": {
						"id": 1,
						"shop_id": 1,
						"name": "fsdf",
						"address": "fdsafasf",
						"sale_description": "fdsafdsaf",
						"phone_1": "fadsfsaf",
						"phone_2": "fdajksfd",
						"phone_3": "fajdskfs",
						"service_time": "12:00-18:00",
						"description": "fdsakf",
						"wechat": "weafa",
						"visit_count": 20,
						"imageList": [
										{
											"id": 1,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 2,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
					}
}
```

<font size="4"><b> 获得展位详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_exhibition_factory_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
exhibitionSpotId | int | true | 展位id
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
exhibitionSpot | ExhibitionSpot | true | 展位列表

### ExhibitionSpot Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 展位Id
shop_id | int | true | 商铺Id
name | String | true | 厂家名称
sale_description | String | true | 主营描述
address | string | true | 地址
description | string | true | 店铺描述
phone_1 | string | true | 业务联系
phone_2 | string | true | 订货电话
phone_3 | string | true | 技术咨询
service_time | string | true | 营业时间
wechat | string | true | 微信号
visit_count | int | true | 浏览人数
imageList | string | true | 店铺图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Get Exhibition Charges</font>

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
"chargeList": [
					{
						"id": 1,
						"name": "1 month",
						"price": 1000
					},
					{
						"id": 2,
						"name": "1 month",
						"price": 1500
					}
				]
}
```

<font size="4"><b> 获得展费列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_exhibition_charges</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
chargeList | Array(ExhibitionCharge Object) | true | 展费列表

### ExhibitionCharge Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 展费Id
name | String | true | 名称
price | int | true | 价格

## <font color="blue">Apply Exhibition Spot</font>

> Request:

```json
{
"userId": 1,
"name": "asdfsa",
"contactPerson": "fdsaf",
"phone_1": "fdsaf",
"phone_2": "fdjsaf",
"phone_3": "fjdskf",
"address": "fdsafds",
"sectionId": 3,
"saleDescription": "fdsfasf",
"exhibitionChargeId": 3,
"license": "fdsafdsajkfjkkkkkkk",
"idFront": "fdsaklfjdsakfjkdsafj",
"idBack": "fdjskalfjdsaklfjdksafjk"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 申请展位</b></font>

### Method:   POST

### Path:   <font color="green">/apply_exhibition_spot</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
name | string | true | 厂家名称
contactPerson | string | true | 联系人
phone_1 | string | true | 联系电话
phone_2 | string | true | 订货电话
phone_3 | string | true | 技术咨询
address | string | true | 地址
sectionId | int | true | 展区id
saleDescription | string | true | 主营描述
exhibitionChargeId | int | true | 展费Id
license | string | true | 营业执照base64编码照片
idFront | string | true | 身份证正面base64编码照片
idBack | string | true | 身份证背面base64编码照片
### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Search Exhibition Factories</font>

> Request:

```json
{
"searchContent": "fd",
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"factoryList": [
						{
							"id": 1,
							"shop_id": 3,
							"name": "fsadf",
							"sale_description": "fdsafsa",
							"address": "fasdf",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						},
						{
							"id": 2,
							"shop_id": 3,
							"name": "fsadf",
							"sale_description": "fdsafsa",
							"address": "fasdf",
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
						}
					]
}
```

<font size="4"><b> 搜索厂家展位</b></font>

### Method:   POST

### Path:   <font color="green">/search_exhibition_spot</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
searchContent | string | true | 搜索内容
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
factoryList | Array(Exhibition object) | true | 展位列表

### Exhibition Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 展位Id
shop_id | int | true | 店铺Id
name | String | true | 厂家名称
sale_description | String | true | 主营描述
address | string | true | 地址
image_url | string | true | 店铺图片

## <font color="blue">Update Exhibition Spot</font>

> Request:

```json
{
"userId": 1,
"name": "asdfsa",
"contactPerson": "fdsaf",
"phone_1": "fdsaf",
"phone_2": "fdjsaf",
"phone_3": "fjdskf",
"address": "fdsafds",
"sectionId": 3,
"saleDescription": "fdsfasf",
"exhibitionChargeId": 3,
"description": "dasff",
"bankName": "dsfasa",
"bankNumber": "2353252435435643"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新展位</b></font>

### Method:   POST

### Path:   <font color="green">/update_exhibition_spot</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
name | string | false | 厂家名称
contactPerson | string | false | 联系人
phone_1 | string | false | 联系电话
phone_2 | string | false | 订货电话
phone_3 | string | false | 技术咨询
address | string | false | 地址
sectionId | int | false | 展区id
saleDescription | string | false | 主营描述
exhibitionChargeId | int | false | 展费Id
description | string | false | 店铺描述
bankName | string | false | 银行名称
bankNumber | string | false | 银行账号

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get My Exhibition Detail</font>

> Request:

```json
{
"userId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"exhibitionSpot": {
						"id": 1,
						"shop_id": 1,
						"name": "fsdf",
						"address": "fdsafasf",
						"sale_description": "fdsafdsaf",
						"phone_1": "fadsfsaf",
						"phone_2": "fdajksfd",
						"phone_3": "fajdskfs",
						"service_time": "12:00-18:00",
						"description": "fdsakf",
						"wechat": "weafa",
						"visit_count": 20,
						"imageList": [
										{
											"id": 1,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 2,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
									]
					}
}
```

<font size="4"><b> 获得我的展位详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_exhibition_spot_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
exhibitionSpot | ExhibitionSpot | true | 展位列表

### ExhibitionSpot Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 展位Id
shop_id | int | true | 商铺Id
name | String | true | 厂家名称
sale_description | String | true | 主营描述
address | string | true | 地址
description | string | true | 店铺描述
phone_1 | string | true | 业务联系
phone_2 | string | true | 订货电话
phone_3 | string | true | 技术咨询
service_time | string | true | 营业时间
wechat | string | true | 微信号
visit_count | int | true | 浏览人数
imageList | string | true | 店铺图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

# Buyer Info

## <font color="blue">Get Attendance Info</font>

> Request:

```json
{
"userId": 2,
"shopId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"totalCount": 30,
"attendanceList": [ "2016-05-20", "2016-05-21", "2016-05-23"],
"consecutiveCount": 10,
"gift_1": "fdsf",
"gift_2": "fdfs"
}
```

<font size="4"><b> 获得签到信息</b></font>

### Method:   POST

### Path:   <font color="green">/get_buyer_attendance</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
shopId | int | true | 店铺Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
totalCount | int | true | 签到总数
attendanceList | Array(String) | true | 本月签到日期列表(Y-m-d)
consecutiveCount | int | true | 连续签到次数
gift_1 | string | false | 15天礼物名称
gift_2 | string | false | 30天礼物名称

## <font color="blue">Set Attendance</font>

> Request:

```json
{
"userId": 2,
"shopId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"reward": 1,
"gift": "dfsaf",
"consecutiveCount": 10
}
```

<font size="4"><b> 买家签到</b></font>

### Method:   POST

### Path:   <font color="green">/set_buyer_attendance</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
shopId | int | true | 店铺Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
reward | int | true | 获奖状态(0:未获奖 1:获得15天奖 2:获得30天奖)
consecutiveCount | int | true | 连续签到次数
gift | string | true | 奖品名称

## <font color="blue">Get Product Collect</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"collectList": [
					{
						"id": 3,
						"product_id": 4,
						"name": "fdsa",
						"original_price": 23,
						"price": 31,
						"brand": "fdsf",
						"spec": "fdsaf",
						"model": "fdsaf",
						"car_model": "fdasf",
						"description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
					},
					{

						"id": 4,
						"product_id": 4,
						"name": "fdsa",
						"original_price": 23,
						"price": 31,
						"brand": "fdsf",
						"spec": "fdsaf",
						"model": "fdsaf",
						"car_model": "fdasf",
						"description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
					}
				]
}
```

<font size="4"><b> 获得用户产品收藏</b></font>

### Method:   POST

### Path:   <font color="green">/get_buyer_product_collects</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
collectList | Array(Product Object) | true | 收藏列表

### Product Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 收藏ID
product_id | int | true | 商品id
name | string | true | 商品名称
original_price | double | true | 原价
price | double | true | 现价
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
description | string | false | 描述
image_url | string | true | 图片URL

## <font color="blue">Get Shop Collect</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"collectList": [
					{
						"id": 3,
						"shop_id": 4,
						"name": "fdsa",
						"address": "fdasf",
						"sale_description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
					},
					{
						"id": 4,
						"shop_id": 4,
						"name": "fdsa",
						"address": "fdasf",
						"sale_description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
					}
				]
}
```

<font size="4"><b> 获得用户店铺收藏</b></font>

### Method:   POST

### Path:   <font color="green">/get_buyer_shop_collects</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
collectList | Array(Shop Object) | true | 收藏列表

### Shop Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 收藏ID
shop_id | int | true | 店铺id
name | string | true | 店铺名称
sale_description | string | 主营描述
address | string | true | 地址
image_url | string | true | 图片URL

## <font color="blue">Remove Collect </font>

> Request:

```json
{
"collectIdList": [1, 2, 3]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除收藏</b></font>

### Method:   POST

### Path:   <font color="green">/remove_collect</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
collectIdList | Array(int) | true | 收藏Id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get User Profile </font>

> Request:

```json
{
"userId": 3
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"profileInfo": {
					"realName": "fdsf",
					"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
					"companyName": "fdsf",
					"contact": "fdsf",
					"companyAddress": "fdsafkjk",
					"saleDescription": "fdsjfj",
					"wechat": "fdasf",
					"alipay": "fsdajkf"
				}
}
```

<font size="4"><b> 获得个人信息</b></font>

### Method:   POST

### Path:   <font color="green">/get_user_profile</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
profileInfo | Profile Object | true | 个人信息

### Profile Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
realName | string | true | 真实姓名
image_url | String | false | 头像url
companyName | string | false | 公司名称
contact | string | false | 联系方式
companyAddress | string | false | 公司地址
saleDescription | string | false | 主营业务
wechat | string | false | 微信支付账号
alipay | string | false | 支付宝账号

## <font color="blue">Update User Profile </font>

> Request:

```json
{
"userId": 3,
"realName": "fdsf",
"image": "fjksdajfsdkaj",
"wechat": "fdsaf",
"alipay": "fdssfj"
}
```

> Response:

```json
{
"head_url": "http://121.12.11.11/image_download/brand_logo_images/2",
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新个人信息</b></font>

### Method:   POST

### Path:   <font color="green">/update_user_profile</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
realName | string | false | 真实姓名
image | string | false | 图片(base64编码)
wechat | string | false | 微信支付账号
alipay | string | false | 支付宝账号

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
head_url | string | true | 头像url
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get Visit Products</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"collectList": [
					{
						"id": 3,
						"name": "fdsa",
						"original_price": 23,
						"price": 31,
						"brand": "fdsf",
						"spec": "fdsaf",
						"model": "fdsaf",
						"car_model": "fdasf",
						"description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
						"shop_name": "fdsaf",
						"shop_address": "fdsafas",
						"is_vip": 1
					},
					{
						"id": 4,
						"name": "fdsa",
						"original_price": 23,
						"price": 31,
						"brand": "fdsf",
						"spec": "fdsaf",
						"model": "fdsaf",
						"car_model": "fdasf",
						"description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
						"shop_name": "fdsaf",
						"shop_address": "fdsafas",
						"is_vip": 1
					}
				]
}
```

<font size="4"><b> 获得用户历史足迹-产品</b></font>

### Method:   POST

### Path:   <font color="green">/get_buyer_product_visits</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
collectList | Array(Product Object) | true | 收藏列表

### Product Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 商品id
name | string | true | 商品名称
original_price | double | true | 原价
price | double | true | 现价
brand | string | false | 品牌
spec | string | false | 规格
model | string | false | 型号
car_model | string | false | 汽车型号
description | string | false | 描述
image_url | string | true | 图片URL
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
is_vip | string | true | 知否为vip 1为是， 2为否

## <font color="blue">Get Visit Shop</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"collectList": [
					{
						"id": 3,
						"name": "fdsa",
						"address": "fdasf",
						"sale_description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
						"is_vip": 1
					},
					{
						"id": 4,
						"name": "fdsa",
						"address": "fdasf",
						"sale_description": "fdsaf",
						"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
						"is_vip": 2
					}
				]
}
```

<font size="4"><b> 获得用户历史足迹-店铺</b></font>

### Method:   POST

### Path:   <font color="green">/get_buyer_shop_visits</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
collectList | Array(Shop Object) | true | 收藏列表

### Shop Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
sale_description | string | 主营描述
address | string | true | 地址
image_url | string | true | 图片URL
is_vip | string | true | 知否为vip 1为是， 2为否

## <font color="blue">Update Shop Images</font>

> Request:

```json
{
"userId": 2,
"imageList": ["fdskafjsadkfj", "fjdsaklfjksdajfk"],
"existingImageIdList": [1, 2]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新店铺轮播图</b></font>

### Method:   POST

### Path:   <font color="green">/update_shop_images</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
imageList | int | false | 新增图片列表(base64编码)
existingImageIdList | Array(int) | false | 保留的原有图片id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

### Shop Object

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
sale_description | string | 主营描述
address | string | true | 地址
image_url | string | true | 图片URL
is_vip | string | true | 知否为vip 1为是， 2为否

## <font color="blue">User Feedback</font>

> Request:

```json
{
"userId": 2,
"image": "fdsakfjfdsafsaf",
"content": "fadsjklfj"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 用户反馈</b></font>

### Method:   POST

### Path:   <font color="green">/user_feedback</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 买家Id
image | string | false | 图片(base64编码)
content | string | true | 内容

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get My Messages </font>

> Request:

```json
{
"userId": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"messageList": [
					{
						"id": 2,
						"title": "fdsfj",
						"content": "fjdsakfj",
						"created_time": "2013-10-12 12:00:00",
					},
					{
						"id": 2,
						"title": "fdsfj",
						"content": "fjdsakfj",
						"created_time": "2013-10-12 12:00:00",
					}
				]
}
```

<font size="4"><b> 获得我的消息</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_messages</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
messageList | Array(Message Object) | true | 消息列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
id | int | true | 消息Id
title | String | true | 标题
content | String | true | 内容
created_time | datetime | true | 时间

## <font color="blue">Delete Messages </font>

> Request:

```json
{
"messageIdList": [1, 2, 3]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除我的消息</b></font>

### Method:   POST

### Path:   <font color="green">/remove_messages</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
messageIdList | Array(int) | true | 消息Id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Product Topic

## <font color="blue">Get Need Product List</font>

> Request:

```json
{
"provinceId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"needProductList": [
						{
							"id": 1,
							"productName": "fadsf",
							"publishTime": "2016-05-05 12:00:00",
							"carBrand": "fdsf",
							"carModel": "fdsaf",
							"engineModel": "fdsafas",
							"status": 1,
							"visitCount": 12
						},
						{
							"id": 2,
							"productName": "fadsf",
							"publishTime": "2016-05-05 12:00:00",
							"carBrand": "fdsf",
							"carModel": "fdsaf",
							"engineModel": "fdsafas",
							"status": 1,
							"visitCount": 12
						}
					]
}
```

<font size="4"><b> 获得急件求购列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_need_product_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
needProductList | Array(NeedProduct Object) | true | 急件求购列表

### NeedProduct Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 急件求购Id;
productName | string | true | 商品名称
publishTime | datetime | true | 发布时间
carBrand | string | true | 汽车品牌
carModel | string | true | 具体车型
engineModel | string | true | 发动机型号
status | int | true | 1:求购中 2.已下架
visitCount | int | true | 浏览次数

## <font color="blue">Get Transfer Product List</font>

> Request:

```json
{
"provinceId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"transferProductList": [
						{
							"id": 1,
							"publisherId": 2,
							"publisherName": "fjdskf",
							"publisherImageUrl": "http://121.12.11.11/image_download/brand_logo_images/2",
							"publishTime": "2016-05-05 12:00:00",
							"title": "fdsf",
							"description": "fdsaf",
							"status": 1,
							"visitCount": 12,
							"imageList": [
											{
												"id": 2,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 3,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 2,
							"publisherId": 2,
							"publisherName": "fjdskf",
							"publisherImageUrl": "http://121.12.11.11/image_download/brand_logo_images/2",
							"publishTime": "2016-05-05 12:00:00",
							"title": "fdsf",
							"description": "fdsaf",
							"status": 1,
							"visitCount": 12,
							"imageList": [
											{
												"id": 4,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 5,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
					]
}
```

<font size="4"><b> 获得急件转让列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_transfer_product_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
transferProductList | Array(TransferProduct Object) | true | 急件转让列表

### NeedProduct Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 急件转让Id;
publisherId | int | true | 发布者Id
publisherName | string | true | 发布者姓名
publisherImageUrl | string | true | 发布者头像url
publishTime | datetime | true | 发布时间
title | string | true | 标题
description | string | true | 描述
status | int | true | 1:转让中 2.已下架
visitCount | int | true | 浏览次数
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Get Need Product Detail</font>

> Request:

```json
{
"needProductId": 2,
"userId": 3
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"needProduct": {
					"id": 1,
					"publisherId": 8,
					"publisherName": "fedfa",
					"publisherImage": "http://121.12.11.11/image_download/brand_logo_images/2",
					"productName": "fadsf",
					"publishTime": "2016-05-05 12:00:00",
					"carBrand": "fdsf",
					"carModel": "fdsaf",
					"engineModel": "fdsafas",
					"description": "fdsaklfj",
					"status": 1,
					"visitCount": 12,
					"contactPerson": "fdsafa",
					"phone": "23242234",
					"address": "fdsajklfdj",
					"wechat": "fdskfj",
					"imageList": [
										{
											"id": 4,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 5,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
								]
				},
}
```

<font size="4"><b> 获得急件求购详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_need_product_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
needProductId | int | true | 急件求购id
useId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
needProduct | NeedProduct Object | true | 急件求购详情

### NeedProduct Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 帖子Id;
publisherId | int | true | 发帖人id
publisherName | string | true | 发帖人名字
publisherImage | string | false | 发帖人头像url地址
productName | string | true | 商品名称
publishTime | datetime | true | 发布时间
carBrand | string | true | 汽车品牌
carModel | string | true | 具体车型
engineModel | string | true | 发动机型号
description | string | true | 详情描述
status | int | true | 1:求购中 2.已下架
visitCount | int | true | 浏览次数
contactPerson | string | true | 联系人
phone | string | true | 电话
address | string | true | 地址
wechat | string | true | 微信
imageList | Array(Image) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Get Transfer Product Detail</font>

> Request:

```json
{
"transferProductId": 2,
"userId": 3
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"transferProduct": {
					"id": 1,
					"publisherId": 8,
					"publisherName": "fedfa",
					"publisherImage": "http://121.12.11.11/image_download/brand_logo_images/2",
					"title": "fadsf",
					"publishTime": "2016-05-05 12:00:00",
					"price": 15,
					"contactCount": 12,
					"description": "fdsaklfj",
					"status": 1,
					"visitCount": 12,
					"contactPerson": "fdsafa",
					"phone": "23242234",
					"imageList": [
										{
											"id": 4,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										},
										{
											"id": 5,
											"url": "http://121.12.11.11/image_download/brand_logo_images/2"
										}
								]
				},
}
```

<font size="4"><b> 获得急件转让详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_transfer_product_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
transferProductId | int | true | 急件转让id
useId | int | true | 用户Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
transferProduct | TransferProduct Object | true | 急件求购详情

### TransferProduct Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 帖子Id;
publisherId | int | true | 发帖人id
publisherName | string | true | 发帖人名字
publisherImage | string | false | 发帖人头像url地址
title | string | true | 标题
publishTime | datetime | true | 发布时间
price | double | true | 转让价格
contactCount | int | true | 联系次数
description | string | true | 详情描述
status | int | true | 1:求购中 2.已下架
visitCount | int | true | 浏览次数
contactPerson | string | true | 联系人
phone | string | true | 电话
imageList | Array(Image) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Contact Transfer Product</font>

> Request:

```json
{
"transferProductId": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"contactCount": 4 
}
```

<font size="4"><b> 急件转让更新联系次数</b></font>

### Method:   POST

### Path:   <font color="green">/contact_transfer_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
transferProductId | int | true | 急件转让id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
contactCount | int | true | 联系次数

## <font color="blue">Publish Need Product</font>

> Request:

```json
{
"provinceId": 2,
"userId": 3,
"productName": "fadsf",
"carBrand": "fdsf",
"carModel": "fdsaf",
"engineModel": "fdsafas",
"description": "fdsaklfj",
"contactPerson": "fdsafa",
"phone": "23242234",
"address": "fdsajklfdj",
"wechat": "fdskfj",
"imageList": [ 
				"fsdafdsjfkasjfkasljf",
				"fdsakfjasdkfjkasdfjkas"
			]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"needProductId": 3
}
```

<font size="4"><b> 发布急件求购</b></font>

### Method:   POST

### Path:   <font color="green">/publish_need_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份id
useId | int | true | 用户Id
productName | string | true | 商品名称
carBrand | string | true | 汽车品牌
carModel | string | true | 具体车型
engineModel | string | true | 发动机型号
description | string | true | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
address | string | true | 地址
wechat | string | true | 微信
imageList | Array(Image) | true | 图片列表(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
needProductId | int | true | 急件求购Id

## <font color="blue">Publish Transfer Product</font>

> Request:

```json
{
"provinceId": 2,
"userId": 3,
"title": "fadsf",
"price": 15,
"description": "fdsaklfj",
"contactPerson": "fdsafa",
"phone": "23242234",
"imageList": [ 
				"fsdafdsjfkasjfkasljf",
				"fdsakfjasdkfjkasdfjkas"
			]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"transferProductId": 4 
}
```

<font size="4"><b> 发布急件转让</b></font>

### Method:   POST

### Path:   <font color="green">/publish_transfer_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
useId | int | true | 用户Id
title | string | true | 标题
price | double | true | 转让价格
description | string | true | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
imageList | Array(Image) | true | 图片列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
transferProductId | int | true | 急件求购Id

## <font color="blue">Get My Need Product List</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"needProductList": [
						{
							"id": 1,
							"productName": "fadsf",
							"publishTime": "2016-05-05 12:00:00",
							"carBrand": "fdsf",
							"carModel": "fdsaf",
							"engineModel": "fdsafas",
							"status": 1,
							"visitCount": 12,
							"publisherId": 3,
							"publisherName": "fdsf",
							"publisherImage": "http://121.12.11.11/image_download/brand_logo_images/2",
							"description": "fdsafdsa",
							"contactPerson": "fsadfs",
							"phone": "fdsaf",
							"address": "fdsfd",
							"wechat": "dfaskfj",
							"imageList": [
											{
												"id": 2,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 3,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 2,
							"productName": "fadsf",
							"publishTime": "2016-05-05 12:00:00",
							"carBrand": "fdsf",
							"carModel": "fdsaf",
							"engineModel": "fdsafas",
							"status": 1,
							"visitCount": 12,
							"publisherId": 3,
							"publisherName": "fdsf",
							"publisherImage": "http://121.12.11.11/image_download/brand_logo_images/2",
							"description": "fdsafdsa",
							"contactPerson": "fsadfs",
							"phone": "fdsaf",
							"address": "fdsfd",
							"wechat": "dfaskfj",
							"imageList": [
											{
												"id": 2,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 3,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						}
					]
}
```

<font size="4"><b> 我的急件求购列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_need_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
needProductList | Array(NeedProduct Object) | true | 急件求购列表

### NeedProduct Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 急件求购Id;
productName | string | true | 商品名称
publishTime | datetime | true | 发布时间
carBrand | string | true | 汽车品牌
carModel | string | true | 具体车型
engineModel | string | true | 发动机型号
status | int | true | 1:求购中 2.已下架
visitCount | int | true | 浏览次数
publisherId | int | true | 发帖人id
publisherName | string | true | 发帖人名字
publisherImage | string | false | 发帖人头像url地址
description | string | true | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
address | string | true | 地址
wechat | string | true | 微信
imageList | Array(Image) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Get My Transfer Product List</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"transferProductList": [
						{
							"id": 1,
							"publisherId": 2,
							"publisherName": "fjdskf",
							"publisherImage": "http://121.12.11.11/image_download/brand_logo_images/2",
							"publishTime": "2016-05-05 12:00:00",
							"title": "fdsf",
							"description": "fdsaf",
							"status": 1,
							"visitCount": 12,
							"price": 12,
							"contactCount": 4,
							"contactPerson": "fdsf",
							"phone": "fdjsakf",
							"imageList": [
											{
												"id": 2,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 3,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
						{
							"id": 2,
							"publisherId": 2,
							"publisherName": "fjdskf",
							"publisherImage": "http://121.12.11.11/image_download/brand_logo_images/2",
							"publishTime": "2016-05-05 12:00:00",
							"title": "fdsf",
							"description": "fdsaf",
							"status": 1,
							"visitCount": 12,
							"price": 12,
							"contactCount": 4,
							"contactPerson": "fdsf",
							"phone": "fdjsakf",
							"imageList": [
											{
												"id": 4,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											},
											{
												"id": 5,
												"url": "http://121.12.11.11/image_download/brand_logo_images/2"
											}
										]
						},
					]
}
```

<font size="4"><b> 我的急件转让列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_transfer_products</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
transferProductList | Array(TransferProduct Object) | true | 急件转让列表

### TransferProduct Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 急件转让Id;
publisherId | int | true | 发布者Id
publisherName | string | true | 发布者姓名
publisherImage | string | true | 发布者头像url
publishTime | datetime | true | 发布时间
title | string | true | 标题
description | string | true | 描述
status | int | true | 1:转让中 2.已下架
visitCount | int | true | 浏览次数
price | double | true | 转让价格
contactCount | int | true | 联系次数
contactPerson | string | true | 联系人
phone | string | true | 电话
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Mandatory | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

## <font color="blue">Toggle Prouct Topic State</font>

> Request:

```json
{
"topicId": 3,
"topicType": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新急件求购/急件转让状态</b></font>

### Method:   POST

### Path:   <font color="green">/toggle_product_topic_state</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicId | int | true | 求购/转让Id
topicType | int | true | 类型 1.急件求购 2.急件转让

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Remove Product Topic</font>

> Request:

```json
{
"topicId": 3,
"topicType": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除急件求购/急件转让</b></font>

### Method:   POST

### Path:   <font color="green">/delete_product_topic</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
topicId | int | true | 求购/转让Id
topicType | int | true | 类型 1.急件求购 2.急件转让

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Update Need Product</font>

> Request:

```json
{
"needProductId": 2,
"productName": "fadsf",
"carBrand": "fdsf",
"carModel": "fdsaf",
"engineModel": "fdsafas",
"description": "fdsaklfj",
"contactPerson": "fdsafa",
"phone": "23242234",
"address": "fdsajklfdj",
"wechat": "fdskfj",
"imageList": [ 
				"fsdafdsjfkasjfkasljf",
				"fdsakfjasdkfjkasdfjkas"
			],
"existingImageIdList": [1, 2]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新急件求购</b></font>

### Method:   POST

### Path:   <font color="green">/update_need_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
needProductId | int | true | 急件求购id
productName | string | true | 商品名称
carBrand | string | false | 汽车品牌
carModel | string | false | 具体车型
engineModel | string | false | 发动机型号
description | string | false | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
address | string | false | 地址
wechat | string | false | 微信
imageList | Array(Image) | false | 新增图片列表(base64编码)
existingImageIdList | Array(int) | true | 原有保留图片Id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Update Transfer Product</font>

> Request:

```json
{
"transferProductId": 2,
"userId": 3,
"title": "fadsf",
"price": 15,
"description": "fdsaklfj",
"contactPerson": "fdsafa",
"phone": "23242234",
"imageList": [ 
				"fsdafdsjfkasjfkasljf",
				"fdsakfjasdkfjkasdfjkas"
			],
"existingImageIdList": [1, 2]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新急件转让</b></font>

### Method:   POST

### Path:   <font color="green">/update_transfer_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
transferProductId | int | true | 急件转让Id
title | string | true | 标题
price | double | true | 转让价格
contactCount | int | true | 联系次数
description | string | true | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
imageList | Array(Image) | false | 新增图片列表(base64编码)
existingImageIdList | Array(int) | true | 原有保留图片Id列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Job

## <font color="blue">Ge Job Type List</font>

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
"jobTypeList": [
						{
							"id": 1,
							"name": "fadsf"
						},
						{
							"id": 2,
							"name": "fadsf"
						}
				]
}
```

<font size="4"><b> 获得职位类型</b></font>

### Method:   POST

### Path:   <font color="green">/get_job_type_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobTypeList | Array(JobType Object) | true | 职位类型

### JobType Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 职位类型Id;
name | string | true | 职位类型名称

## <font color="blue">Get Job Recruit List</font>

> Request:

```json
{
"filterCity": 1,
"filterJob": 2,
"filterSalary": "1000~2000",
"filterExperience": "1 year",
"provinceId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobRecruitList": [
						{
							"id": 1,
							"jobTypeName": "fadsf",
							"companyName": "dsfsaf",
							"companyAddress": "fdsf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"image": "http://121.12.11.11/image_download/brand_logo_images/2",
							"status": 1
						},
						{
							"id": 2,
							"jobTypeName": "fadsf",
							"companyName": "dsfsaf",
							"companyAddress": "fdsf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"image": "http://121.12.11.11/image_download/brand_logo_images/2",
							"status": 1
						}
					]
}
```

<font size="4"><b> 根据条件获得招聘列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_job_recruit_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
filterCity | int | false | 过滤城市Id
filterJob | int | false | 过滤工种Id
filterSalary | string | false | 过滤工资
filterExperience | string | false | 过滤经验
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobRecruitList | Array(JobRecruit Object) | true | 招聘列表

### JobRecruit Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 招聘Id;
jobTypeName | string | true | 职位名称
companyName | datetime | true | 公司名称
companyAddress | string | true | 公司地址
publishTime | string | true | 发布时间
salary | string | true | 薪资
image | int | true | 公司logo
status | int | true | 状态 1.发布中 2.停止发布

## <font color="blue">Get Job Recruit Detail</font>

> Request:

```json
{
"jobRecruitId": 1,
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobRecruit": {
					"id": 4,
					"jobTypeName": "fadsf",
					"companyName": "dsfsaf",
					"companyAddress": "fdsf",
					"publishTime": "2016-05-05 12:00:00",
					"salary": "fdsafas",
					"image": "http://121.12.11.11/image_download/brand_logo_images/2",
					"cityName": "fds",
					"education": "education",
					"gender": "fd",
					"number": "fd",
					"experience": "dafd",
					"age": "fds",
					"companyProperty": "fds",
					"companyScale": "fd",
					"companyWelfare": "fd",
					"phone": "fdsf",
					"description": "fsd",
					"contactPerson": "fed",
					"status": 1
				}
}
```

<font size="4"><b> 获得招聘详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_job_recruit_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
jobRecruitId | int | true | 招聘Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobRecruit | JobRecruit Object | true | 招聘详情

### JobRecruit Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 招聘Id;
jobTypeName | string | false | 职位名称
companyName | datetime | false | 公司名称
companyAddress | string | false | 公司地址
publishTime | string | false | 发布时间
salary | string | false | 薪资
image | int | false | 公司logo
cityName | string | false | 城市名称
education | string | false | 学历
gender | string | true | 性别
number | string | false | 招聘人数
publishTime | datetime | false | 发布时间
experience | string | false | 工作经验
age | string | false | 年龄
companyProperty | string | false | 公司性质
companyScale | string | false | 公司简介
companyWelfare | string | false | 公司福利
phone | string | false | 联系电话
description | string | false | 岗位描述
contactPerson | string | false | 联系人
status | int | true | 状态 1.发布中 2.停止发布

## <font color="blue">Publish Job Recruit</font>

> Request:

```json
{
"userId": 3,
"jobTypeId": 5,
"companyName": "dsfsaf",
"companyAddress": "fdsf",
"salary": "fdsafas",
"image": "http://121.12.11.11/image_download/brand_logo_images/2",
"cityId": 4,
"education": "education",
"gender": "fd",
"number": "fd",
"experience": "dafd",
"age": "fds",
"companyProperty": "fds",
"companyScale": "fd",
"companyWelfare": "fd",
"phone": "fdsf",
"description": "fsd",
"contactPerson": "fed"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 发布招聘</b></font>

### Method:   POST

### Path:   <font color="green">/publish_job_recruit</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
useId | int | true | 发布人Id
jobTypeId | int | false | 工作种类Id
companyName | datetime | false | 公司名称
companyAddress | string | false | 公司地址
publishTime | string | false | 发布时间
salary | string | false | 薪资
image | int | false | 公司logo
cityId | string | false | 城市Id
education | string | false | 学历
gender | string | true | 性别 1.男性 2.女性
number | string | false | 招聘人数
experience | string | false | 工作经验
age | string | false | 年龄
companyProperty | string | false | 公司性质
companyScale | string | false | 公司简介
companyWelfare | string | false | 公司福利
phone | string | false | 联系电话
description | string | false | 岗位描述
contactPerson | string | false | 联系人

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Search Job Recruit</font>

> Request:

```json
{
"search": "fdasf",
"provinceId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobRecruitList": [
						{
							"id": 1,
							"jobTypeName": "fadsf",
							"companyName": "dsfsaf",
							"companyAddress": "fdsf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"image": "http://121.12.11.11/image_download/brand_logo_images/2",
							"status": 1
						},
						{
							"id": 2,
							"jobTypeName": "fadsf",
							"companyName": "dsfsaf",
							"companyAddress": "fdsf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"image": "http://121.12.11.11/image_download/brand_logo_images/2",
							"status": 1
						}
					]
}
```

<font size="4"><b> 搜索招聘列表</b></font>

### Method:   POST

### Path:   <font color="green">/search_job_recruit</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
search | int | false | 搜索内容
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobRecruitList | Array(JobRecruit Object) | true | 招聘列表

### JobRecruit Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 招聘Id;
jobName | string | true | 职位名称
companyName | datetime | true | 公司名称
companyAddress | string | true | 公司地址
publishTime | string | true | 发布时间
salary | string | true | 薪资
image | int | true | 公司logo
status | int | true | 状态 1.发布中 2.停止发布

## <font color="blue">Get Job Application List</font>

> Request:

```json
{
"filterCity": 1,
"filterJob": 2,
"filterSalary": "1000~2000",
"filterExperience": "1 year",
"provinceId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobApplicationList": [
						{
							"id": 1,
							"jobTypeName": "fadsf",
							"name": "dsfsaf",
							"city": "fdsf",
							"gender": "fdsf",
							"education": "fdsaf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"experience": "fdsaf",
							"status": 1
						},
						{
							"id": 2,
							"jobTypeName": "fadsf",
							"name": "dsfsaf",
							"city": "fdsf",
							"gender": "fdsf",
							"education": "fdsaf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"experience": "fdsaf",
							"status": 1
						}
					]
}
```

<font size="4"><b> 根据条件获得求职列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_job_application_list</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
filterCity | int | false | 过滤城市Id
filterJob | int | false | 过滤工种Id
filterSalary | string | false | 过滤工资
filterExperience | string | false | 过滤经验
provinceId | int | true | 省份Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobApplicationList | Array(JobApplication Object) | true | 求职列表

### JobApplication Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 求职Id
name | string | true | 求职人姓名
jobTypeName | string | true | 职位名称
city | string | true | 城市名称
gender | string | true | 性别
publishTime | string | true | 发布时间
salary | string | true | 薪资
education | string | false | 学历
experience | string | false | 经验
status | int | true | 状态 1.发布中 2.停止发布

## <font color="blue">Get Job Application Detail</font>

> Request:

```json
{
"jobApplicationId": 1,
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobApplication": {
					"id": 2,
					"jobTypeName": "fadsf",
					"name": "dsfsaf",
					"city": "fdsf",
					"gender": "fdsf",
					"education": "fdsaf",
					"publishTime": "2016-05-05 12:00:00",
					"salary": "fdsafas",
					"experience": "fdsaf",
					"status": 1,
					"age": 20,
					"phone": "fdsaf",
					"description": "fdsafj"
				}
}
```

<font size="4"><b> 获得求职详情</b></font>

### Method:   POST

### Path:   <font color="green">/get_job_application_detail</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
jobApplicationId | int | true | 招聘Id

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobApplication | JobApplication Object | true | 求职详情

### JobApplication Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 求职Id
name | string | true | 求职人姓名
jobTypeName | string | true | 职位名称
city | string | true | 城市名称
gender | string | true | 性别
publishTime | string | true | 发布时间
salary | string | true | 薪资
education | string | true | 学历
experience | string | false | 经验
status | int | true | 状态 1.发布中 2.停止发布
age | string | false | 年龄
description | string | false | 个人简介
phone | string | false | 联系电话

## <font color="blue">Publish Job Application</font>

> Request:

```json
{
"userId": 3,
"jobTypeId": 5,
"name": "dsfsaf",
"cityId": 46,
"gender": "fdsf",
"education": "fdsaf",
"salary": "fdsafas",
"experience": "fdsaf",
"age": 20,
"phone": "fdsaf",
"description": "fdsafj"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 发布求职</b></font>

### Method:   POST

### Path:   <font color="green">/publish_job_application</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
useId | int | true | 发布人Id
jobTypeId | int | false | 工作种类Id
name | string | true | 求职人姓名
city | string | true | 城市名称
gender | string | true | 性别
salary | string | true | 薪资
education | string | true | 学历
experience | string | false | 经验
age | string | false | 年龄
description | string | false | 个人简介
phone | string | false | 联系电话

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Get My Job Application List</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobApplicationList": [
						{
							"id": 1,
							"jobTypeName": "fadsf",
							"name": "dsfsaf",
							"city": "fdsf",
							"gender": "fdsf",
							"education": "fdsaf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"experience": "fdsaf",
							"status": 1,
							"age": 20,
							"phone": "fdsaf",
							"description": "fdsafj"
						},
						{
							"id": 2,
							"jobTypeName": "fadsf",
							"name": "dsfsaf",
							"city": "fdsf",
							"gender": "fdsf",
							"education": "fdsaf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"experience": "fdsaf",
							"status": 1,
							"age": 20,
							"phone": "fdsaf",
							"description": "fdsafj"
						}
					]
}
```

<font size="4"><b> 获得我的求职列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_job_applications</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobApplicationList | Array(JobApplication Object) | true | 求职列表

### JobApplication Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 求职Id
name | string | true | 求职人姓名
jobTypeName | string | true | 职位名称
city | string | true | 城市名称
gender | string | true | 性别
publishTime | string | true | 发布时间
salary | string | true | 薪资
education | string | false | 学历
experience | string | false | 经验
status | int | true | 状态 1.发布中 2.停止发布
age | string | false | 年龄
description | string | false | 个人简介
phone | string | false | 联系电话

## <font color="blue">Get My Job Recruit List</font>

> Request:

```json
{
"userId": 2,
"page": 1
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok",
"jobRecruitList": [
						{
							"id": 1,
							"jobTypeName": "fadsf",
							"companyName": "dsfsaf",
							"companyAddress": "fdsf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"status": 1,
							"image": "http://121.12.11.11/image_download/brand_logo_images/2",
							"cityName": "fds",
							"education": "education",
							"gender": "fd",
							"number": "fd",
							"experience": "dafd",
							"age": "fds",
							"companyProperty": "fds",
							"companyScale": "fd",
							"companyWelfare": "fd",
							"phone": "fdsf",
							"description": "fsd",
							"contactPerson": "fed"
						},
						{
							"id": 2,
							"jobTypeName": "fadsf",
							"companyName": "dsfsaf",
							"companyAddress": "fdsf",
							"publishTime": "2016-05-05 12:00:00",
							"salary": "fdsafas",
							"status": 1,
							"image": "http://121.12.11.11/image_download/brand_logo_images/2",
							"cityName": "fds",
							"education": "education",
							"gender": "fd",
							"number": "fd",
							"experience": "dafd",
							"age": "fds",
							"companyProperty": "fds",
							"companyScale": "fd",
							"companyWelfare": "fd",
							"phone": "fdsf",
							"description": "fsd",
							"contactPerson": "fed"
						}
					]
}
```

<font size="4"><b> 获得我的招聘列表</b></font>

### Method:   POST

### Path:   <font color="green">/get_my_job_recruits</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户Id
page | int | true | 页数

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
jobRecruitList | Array(JobRecruit Object) | true | 招聘列表

### JobRecruit Object

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
id | int | true | 招聘Id;
jobTypeName | string | true | 职位名称
companyName | datetime | true | 公司名称
companyAddress | string | true | 公司地址
publishTime | string | true | 发布时间
salary | string | true | 薪资
status | int | true | 状态 1.发布中 2.停止发布
image | int | false | 公司logo
cityName | string | false | 城市名称
education | string | false | 学历
gender | string | true | 性别
number | string | false | 招聘人数
experience | string | false | 工作经验
age | string | false | 年龄
companyProperty | string | false | 公司性质
companyScale | string | false | 公司规模
companyWelfare | string | false | 公司福利
phone | string | false | 联系电话
description | string | false | 岗位描述
contactPerson | string | false | 联系人

## <font color="blue">Update Job Application</font>

> Request:

```json
{
"jobApplicationId": 3,
"jobTypeId": 5,
"name": "dsfsaf",
"cityId": 46,
"gender": "fdsf",
"education": "fdsaf",
"salary": "fdsafas",
"experience": "fdsaf",
"age": 20,
"phone": "fdsaf",
"description": "fdsafj"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 发布求职</b></font>

### Method:   POST

### Path:   <font color="green">/update_job_application</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
jobApplicationId | int | true | 求职Id
jobTypeId | int | false | 工作种类Id
name | string | true | 求职人姓名
city | string | true | 城市名称
gender | string | true | 性别
salary | string | true | 薪资
education | string | true | 学历
experience | string | false | 经验
age | string | false | 年龄
description | string | false | 个人简介
phone | string | false | 联系电话

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Update Job Recruit</font>

> Request:

```json
{
"jobRecruitId": 3,
"jobTypeId": 5,
"companyName": "dsfsaf",
"companyAddress": "fdsf",
"salary": "fdsafas",
"image": "http://121.12.11.11/image_download/brand_logo_images/2",
"cityId": 4,
"education": "education",
"gender": "fd",
"number": "fd",
"experience": "dafd",
"age": "fds",
"companyProperty": "fds",
"companyScale": "fd",
"companyWelfare": "fd",
"phone": "fdsf",
"description": "fsd",
"contactPerson": "fed"
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新招聘</b></font>

### Method:   POST

### Path:   <font color="green">/update_job_recruit</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
jobRecruitId | int | true | 招聘Id
jobTypeId | int | false | 工作种类Id
companyName | datetime | false | 公司名称
companyAddress | string | false | 公司地址
publishTime | string | false | 发布时间
salary | string | false | 薪资
image | int | false | 公司logo
cityId | string | false | 城市Id
education | string | false | 学历
gender | string | true | 性别 1.男性 2.女性
number | string | false | 招聘人数
experience | string | false | 工作经验
age | string | false | 年龄
companyProperty | string | false | 公司简介
companyScale | string | false | 公司规模
companyWelfare | string | false | 公司福利
phone | string | false | 联系电话
description | string | false | 岗位描述
contactPerson | string | false | 联系人

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Toggle Job State</font>

> Request:

```json
{
"jobId": 3,
"jobType": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新招聘/求职状态</b></font>

### Method:   POST

### Path:   <font color="green">/toggle_job_state</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
jobId | int | true | 工作Id
jobType | int | true | 类型 1.求职 2.招聘

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Remove Job</font>

> Request:

```json
{
"jobId": 3,
"jobType": 2
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 删除招聘/求职</b></font>

### Method:   POST

### Path:   <font color="green">/remove_job</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
jobId | int | true | 工作Id
jobType | int | true | 类型 1.求职 2.招聘

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |

## <font color="blue">Update Need Product</font>

> Request:

```json
{
"needProductId": 2,
"productName": "fadsf",
"carBrand": "fdsf",
"carModel": "fdsaf",
"engineModel": "fdsafas",
"description": "fdsaklfj",
"contactPerson": "fdsafa",
"phone": "23242234",
"address": "fdsajklfdj",
"wechat": "fdskfj",
"existingImageIdList": [1, 2],
"imageList": [ 
				"fsdafdsjfkasjfkasljf",
				"fdsakfjasdkfjkasdfjkas"
			]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新急件求购</b></font>

### Method:   POST

### Path:   <font color="green">/update_need_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
needProductId | int | true | 急件求购id
productName | string | true | 商品名称
carBrand | string | true | 汽车品牌
carModel | string | true | 具体车型
engineModel | string | true | 发动机型号
description | string | true | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
address | string | true | 地址
wechat | string | true | 微信
existingImageIdList | Array(int) | false | 原有保留图片Id列表
imageList | Array(Image) | false | 新增图片列表(base64编码)

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

## <font color="blue">Update Transfer Product</font>

> Request:

```json
{
"transferProductId": 2,
"title": "fadsf",
"price": 15,
"description": "fdsaklfj",
"contactPerson": "fdsafa",
"phone": "23242234",
"existingImageIdList": [1, 2],
"imageList": [ 
				"fsdafdsjfkasjfkasljf",
				"fdsakfjasdkfjkasdfjkas"
			]
}
```

> Response:

```json
{
"status": 1,
"msg": "Ok"
}
```

<font size="4"><b> 更新急件转让</b></font>

### Method:   POST

### Path:   <font color="green">/update_transfer_product</font>

### Request

Name | Type | Mandatory | Description
--------- | ------- | ------- | -----------
transferProductId | int | true | 急件转让Id
title | string | true | 标题
price | double | true | 转让价格
contactCount | int | true | 联系次数
description | string | true | 详情描述
contactPerson | string | true | 联系人
phone | string | true | 电话
existingImageIdList | Array(int) | false | 原有保留图片Id列表
imageList | Array(Image) | true | 新增图片列表

### Response:

Name | Type | Mandatory | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 