---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='https://zoicraze.co.in'>Main Website</a>
  - <a href='https://zoicrazeshopping.com'>Shopping Website</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Zoi Craze API! You can use our API to access Zoi Craze API endpoints, which can get information on associate profiles, wallet balance in our database.

> Make sure to replace `{ACCESS_TOKEN}` with your Access Token retrieved from Associate LOGIN endpoint.

Zoi Craze uses Access TOKEN to allow access to the API. You can get access token at [Login Endpoint](#login).

Zoi Craze expects for the Acces Token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {ACCESS_TOKEN}`

<aside class="notice">
You must replace <code>{ACCESS_TOKEN}</code> with Access Token.
</aside>

# Associate

## Login

This endpoint retrieve Access Token by `username` and `password`

```shell
curl "https://zoicraze.co.in/api/associate/login"
```

> The above command returns JSON structured like this:

```json
{
    "status": "SUCCESS",
    "access_token": "{ACCESS_TOKEN}",
}
```

### HTTP Request

`POST https://zoicraze.co.in/api/associate/login`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
username | `string` | username, `required`, cannot be left blank!
password | `string` | password, `required`, cannot be left blank!

## Profile

This endpoint retrieves associate profile.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://zoicraze.co.in/api/associate/me" \
  -H "Authorization: Bearer {ACCESS_TOKEN}"
```

> The above command returns JSON structured like this:

```json
{
	"status": "SUCCESS",
	"response": {
		"id": 1,
		"username": "{USERNAME}",
		"full_name": "{FULLNAME}",
		"mobile": "{MOBILE}",
		"email": "{EMAIL}",
		"created_at": "23 May 2021",
		"details": {
			"address": "{ADDRESS}",
			"pincode": "{PINCODE}",
			"city": "{CITY}",
			"district": "{DISTRICT}",
			"state": "{STATE}",
			"country": "{COUNTRY}"
		},
		"wallet_balance": {
			"shopping_wallet": "{SHOPPING_WALLET_BALANCE}"
		},
		"no_of_ids": 1,
		"is_topup": "Active",
		"is_active": "Active",
		"package": {
			"id": "{ID}",
			"amount": "{AMOUNT}",
			"name": "{PACKAGE_NAME}",
			"description": "{PACKAGE_DESCRIPTION}",
			"status": "Active"
		},
		"shop_point": 1500
	}
}
```

### HTTP Request

`GET https://zoicraze.co.in/api/associate/me`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`
Authorization | `Bearer {ACCESS_TOKEN}`

## Get Balance

This endpoint retrieves associate shopping wallet balance.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://zoicraze.co.in/api/associate/get_balance" \
  -H "Authorization: Bearer {ACCESS_TOKEN}"
```

> The above command returns JSON structured like this:

```json
{
	"status": "SUCCESS",
	"response": {
		"id": "{ID}",
		"username": "{USERNAME}",
		"wallet_balance": {
			"shopping_wallet": "{SHOPPING_WALLET_BALANCE}"
		}
	}
}
```

### HTTP Request

`GET https://zoicraze.co.in/api/associate/get_balance`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`
Authorization | `Bearer {ACCESS_TOKEN}`

## Deduct Wallet

This endpoint deducts fund from shopping wallet of associate.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://zoicraze.co.in/api/associate/deduct_wallet" \
  -H "Authorization: Bearer {ACCESS_TOKEN}"
```

> The above command returns JSON structured like this:

```json
{
	"status": "SUCCESS",
	"response": {
		"id": "{ID}",
		"username":"{USERNAME}",
		"remark": "{REMARK}",
		"amount":"{AMMOUNT}",
		"transaction_type": "{TRANSACTION_TYPE}",
		"reference_no": "{REFERENCE_NO}",
		"wallet_balance": {
			"shopping_wallet": "{SHOPPING_WALLET_BALANCE}"
		}
	}
}
```

### HTTP Request

`POST https://zoicraze.co.in/api/associate/deduct_wallet`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`
Authorization | `Bearer {ACCESS_TOKEN}`

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
amount 	  | `integer` | amount, `required`, cannot be left blank!
order_no  | `integer` | order_no, `required`, cannot be left blank!

## Transaction Revert

This endpoint revert transaction back to previous.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://zoicraze.co.in/api/associate/transaction_revert" \
  -H "Authorization: Bearer {ACCESS_TOKEN}"
```

> The above command returns JSON structured like this:

```json
{
	"status": "SUCCESS",
	"response": {
		"id": "{ID}",
		"username":"{USERNAME}",
		"remark": "{REMARK}",
		"amount":"{AMMOUNT}",
		"transaction_type": "{TRANSACTION_TYPE}",
		"reference_no": "{REFERENCE_NO}",
		"wallet_balance": {
			"shopping_wallet": "{SHOPPING_WALLET_BALANCE}"
		}
	}
}
```

### HTTP Request

`POST https://zoicraze.co.in/api/associate/transaction_revert`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`
Authorization | `Bearer {ACCESS_TOKEN}`

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
reference_no | `string` | reference_no, `required`, cannot be left blank!
amount 	 	 | `integer` | amount, `required`, cannot be left blank!
order_no 	 | `integer` | order_no, `required`, cannot be left blank!

<aside class="notice">
`reference_no` and `order_no` should match with the existing records when the transaction was created or wallet has been deducted.
</aside>

## Get Transaction

This endpoint get the transaction by reference_no.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://zoicraze.co.in/api/associate/get_transaction" \
  -H "Authorization: Bearer {ACCESS_TOKEN}"
```

> The above command returns JSON structured like this:

```json
{
	"status": "SUCCESS",
	"response": {
		"id": "{ID}",
		"username":"{USERNAME}",
		"remark": "{REMARK}",
		"amount":"{AMMOUNT}",
		"transaction_type": "{TRANSACTION_TYPE}",
		"reference_no": "{REFERENCE_NO}",
		"wallet_balance": {
			"shopping_wallet": "{SHOPPING_WALLET_BALANCE}"
		}
	}
}
```

### HTTP Request

`POST https://zoicraze.co.in/api/associate/get_transaction`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`
Authorization | `Bearer {ACCESS_TOKEN}`

### Body Parameters

Parameter | Type | Description
--------- | ------- | -----------
reference_no | `string` | reference_no, `required`, cannot be left blank!

## Logout

This endpoint logouts the associate.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://zoicraze.co.in/api/associate/logout" \
  -H "Authorization: Bearer {ACCESS_TOKEN}"
```

> The above command returns JSON structured like this:

```json
{
	"message": "You have been successfully logged out!"
}
```

### HTTP Request

`GET https://zoicraze.co.in/api/associate/logout`

### HTTP Headers

Header | Value
---------| --------
Content-Type | `application/json`
Accept | `application/json`
Authorization | `Bearer {ACCESS_TOKEN}`