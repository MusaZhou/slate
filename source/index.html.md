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
"cartId": 2
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
cartId | string | true | 购物车id

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

## <font color="blue">Home Search</font>

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

<b> 首页热门商品类型</b>

### Method:   POST
### Path:   <font color="green">/home_hot_sale_product_type</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
hotSaleProductTypeList | Array(hotSaleProductType object) | true | 热门商品类型列表

### ProductType Object

Name | Type | Default | Description
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

# General

## <font color="blue">Get Ad List</font>

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
secondaryShopTypeId | int | false | 当广告位置是6时必填

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

# Shop

## <font color="blue">Get Shop Type List</font>

> Request:

```json
{
"provinceId": 1
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

<b> 获得店铺类别列表</b>

### Method:   POST
### Path:   <font color="green">/get_shop_types</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id

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
primary_shop_type_name | string | true | 一级类别名称
firstLetterList | Array(FirstLetter object) | true | 首字母列表
recommandedSecondaryShopTypeList | Array(SecondaryShopType object) | true | 热门二级类别

### FirstLetter Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
firstLetter | string | true | 首字母
secondaryShopTypeList | Array(SecondaryShopType object) | true | 二级类别列表

### SecondaryShopType Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
secondary_shop_type_id | int | true | 二级类别id
secondary_shop_type_name | string | true | 二级类别名称
image_url | string | true | 图片URL

## <font color="blue">Shop Type Search</font>

> Request:

```json
{
"search": "abc"
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

<b> 店铺类别搜索</b>

### Method:   POST
### Path:   <font color="green">/search_shop_type</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
search | string | true | 搜索内容

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
secondaryShopTypeList | Array(SecondaryShopType object) | true | 二级类别列表

### SecondaryLetter Object

Name | Type | Default | Description
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
"secondaryShopTypeId": 1
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
							"address": "小明"
						},
						{
							"id": 2,
							"name": "标题1",
							"description": "内容1",
							"address": "小明"
						}
			]
}
```

<b> 根据二级类别获得店铺列表</b>

### Method:   POST
### Path:   <font color="green">/get_shops_by_secondary_shop_type</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
provinceId | int | true | 省份Id
secondaryShopTypeId | int | true | 店铺二级类型Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopList | Array(Shop object) | true | 店铺列表

### Shop Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
description | string | true | 描述
address | string | true | 地址

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

<b> 获得店铺详情</b>

### Method:   POST
### Path:   <font color="green">/get_shop_detail</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id
userId | int | true | 用户Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
shopDetail | Shop object | true | 店铺详情

### Shop Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 店铺id
name | string | true | 店铺名称
service_time | time | 营业时间
collect_count | int | 收藏人数
phone_1 | int | 电话1
phone_2 | int | 电话2
phone_3 | int | 电话3
sale_description | string | 主营描述
description | string | true | 描述
address | string | true | 地址
bannerList | Array(Image object) | false | 轮播图列表

### Image Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

# Product

## <font color="blue">Get Owner Recommended Products</font>

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
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
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
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
						}
			]
}
```

<b> 获店长推荐商品</b>

### Method:   POST
### Path:   <font color="green">/get_owner_recommended_products</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productList | Array(Product object) | true | 商品列表

### Product Object

Name | Type | Default | Description
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
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
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
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
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
														"image_url": "http://121.12.11.11/image_download/brand_logo_images/2"
													}
										]
						}
					]

}
```

<b> 获得产品类型列表</b>

### Method:   POST
### Path:   <font color="green">/get_product_types_by_shop</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
shopId | int | true | 店铺Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productTypeList | Array(ProductType object) | true | 商品类型列表

### ProductType Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 类型id
name | string | true | 类型名称
productList | Array(Product object) | true | 产品列表

### Product Object

Name | Type | Default | Description
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
							"shop_address": "afasdf",
							"shop_phone": "1212412",
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

<b> 获得产品详情</b>

### Method:   POST
### Path:   <font color="green">/get_product_detail</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
productId | int | true | 产品Id
userId | int | true | 用户Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productDetail | Array(Product object) | true | 商品类型列表

### Product Object

Name | Type | Default | Description
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
shop_address | string | true | 店铺地址
shop_phone | string | true |  店铺电话
inventory | int | true |  库存
bannerImageList | Array(Image object) | false | 轮播图列表
referenceImageList | Array(Image object) | false | 参考图列表
sampleComment | Comment object | false | 评论实例

### Image Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

### Comment Object

Name | Type | Default | Description
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
"productId": 1
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

<b> 获得产品评论</b>

### Method:   POST
### Path:   <font color="green">/get_product_comments</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
productId | int | true | 产品id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
commentList | Array(Comment object) | true | 评论列表

### Comment Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 评论id
user_phone | string | true | 评论人电话
content | string | true | 评论内容
created_time | datetime | true | 评论时间
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Default | Description
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
							"image_url": "http://121.12.11.11/image_download/brand_logo_images/2",
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

<b> 获得猜你喜欢产品</b>

### Method:   POST
### Path:   <font color="green">/get_guess_products</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
productId | int | true | 商品Id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
productList | Array(Product object) | true | 商品列表

### ProductType Object

Name | Type | Default | Description
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

# Topic

## <font color="blue">Get All Topics</font>

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
"topicList": [
						{
							"id": 1,
							"title": "标题1",
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
							"title": "标题1",
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

<b> 获得所有帖子</b>

### Method:   POST
### Path:   <font color="green">/get_all_topics</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
topicList | Array(Topic object) | true | 帖子列表

### Topic Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 帖子id
title | string | true | 帖子标题
content | string | true | 帖子内容
user_name | string | true | 发帖人名字
user_url | string | true | 发帖人头像
created_time | string | true | 发布时间
comment_count | int | true | 评价次数
like_count | int | true | 点赞次数
imageList | Array(Image object) | true | 图片列表

### Image Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
id | int | true | 图片id
url | string | true | 图片URL

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

<b> 获得购物车详情</b>

### Method:   POST
### Path:   <font color="green">/get_cart_detail</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
cartId | int | true | 购物车id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
total_quantity | int | true | 产品总数
total_amount | double | true | 产品总金额
cartItemGroups | Array(CartItemGroup object) | true | 购物车店铺列表

### CartItemGroup Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
shop_id | int | true | 店铺id
shop_name | string | true | 店铺名称
shop_address | string | true | 店铺地址
shop_quantity | string | true | 购物车内店铺售卖数量
shop_amount | string | true | 购物车内店铺售卖金额
cartItemList | Array(CartItem object) | true | 购物车内店铺售卖产品列表

### CartItem Object

Name | Type | Default | Description
---------------------- | ------- | ------- | -----------
cart_item_id | int | true | 购物车条目id
product_id | int | true | 产品Id
product_name | string | true | 产品名称
product_brand | string | false | 产品品牌
product_spec | string | false | 产品规格
quantity | int | true | 数量
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

<b> 更新购物车条目</b>

### Method:   POST

### Path:   <font color="green">/update_cart_item</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
cartId | int | true | 购物车id
productId | int | true | 产品id
quantity | int | true | 数量
productActivityId | int | false | 活动id

### Response:

Name | Type | Default | Description
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

<b> 删除购物车条目</b>

### Method:   POST

### Path:   <font color="green">/update_cart_item</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
cartItemId | int | true | 购物车条目id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 

# Delivery Address

## <font color="blue">Get Delivery Addresses By User</font>

> Request:

```json
{
"userId": 1,
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

<b> 获得配送地址列表</b>

### Method:   POST

### Path:   <font color="green">/update_delivery_addresses_by_user</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true | 
deliveryAddressList | Array(DeliveryAddress object) | true | 配送地址列表

### DeliveryAddress object:

Name | Type | Default | Description
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

<b> 添加配送地址</b>

### Method:   POST

### Path:   <font color="green">/add_delivery_address</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id
contact_person | String | true | 联系人
phone | string | true | 电话
address | string | true | 地址

### Response:

Name | Type | Default | Description
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

<b> 更新配送地址</b>

### Method:   POST

### Path:   <font color="green">/update_delivery_address</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
deliveryAddressId | int | true | 配送地址id
contact_person | String | true | 联系人
phone | string | true | 电话
address | string | true | 地址

### Response:

Name | Type | Default | Description
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

<b> 设置默认配送地址</b>

### Method:   POST

### Path:   <font color="green">/set_default_delivery_address</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
deliveryAddressId | int | true | 配送地址id

### Response:

Name | Type | Default | Description
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

<b> 删除配送地址</b>

### Method:   POST

### Path:   <font color="green">/delete_delivery_address</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
deliveryAddressId | int | true | 配送地址id

### Response:

Name | Type | Default | Description
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

<b> 获得默认配送地址</b>

### Method:   POST

### Path:   <font color="green">/get_default_delivery_address</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
userId | int | true | 用户id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1:成功 3:无默认配送地址
msg | String | true | 
defaultDeliveryAddress | Array(DeliveryAddress object) | true | 配送地址

### DeliveryAddress object:

Name | Type | Default | Description
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

<b> 创建新订单</b>

### Method:   POST
### Path:   <font color="green">/create_new_orders</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
cartItemIdList | Array(int) | true | 购物车条目id列表

### Response:

Name | Type | Default | Description
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

<b> 给订单绑定配送地址</b>

### Method:   POST
### Path:   <font color="green">/attach_delivery_address_to_orders</font>

### Request

Name | Type | Default | Description
--------- | ------- | ------- | -----------
orderIdList | Array(int) | true | 订单id列表
deliveryAddressId | int | true | 配送地址id

### Response:

Name | Type | Default | Description
-------------------- | ----------------------- | ------- | -----------
status | int | true | 1.成功
msg | String | true |
