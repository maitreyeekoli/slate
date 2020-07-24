---
title: API Reference

includes:
  - errors

search: true

code_clipboard: true
---
# Sold Plan
### createSoldPlan
This API is used for creating new contract for consumer. Creates a contract for the provided customer and device.
********************
>**Sample cURL:**

```shell
curl --location --request POST '<https://clientstag.servify.tech/primePublicApi/api/v1/SoldPlan/createSoldPlan'> '\ <br>
--header 'Content-Type: application/json' \
--header 'client-id: <CLIENT_ID>' \
--header 'hmac-signature: <HMAC_SIGNATURE>' \
--header 'x-date: <DATE>' \
--header 'x-host: <CLIENT_HOST.COM>' \
--header 'client-session-id: <CLIENT_SESSION_ID>'   \
--data-raw '{ "$data":"<ENCRYPTED_DATA>" }'
```
>**Decrypted Request Body:**

```json
{
    "ExternalReferenceID":"IND20D1775222344",
    "ProductUniqueID":"3569054353457",
    "SerialNumber":"hdgse356hs73h92b",
    "AlternateUniqueKey":"hfjshsh2345677w2233",
    "DeviceDateOfPurchase":"2020-06-15",
    "CustomerName":"Test",
    "PhoneCode":"91",
    "CountryCode":"IN",
    "MobileNo":"9098000000",
    "EmailID":"abc@gmail.com",
    "AlternateMobileNo":"9890111111",
    "BrandName":"Samsung",
    "ProductName":"Galaxy Note 10",
    "DateOfPurchase":"2020-02-21",
    "ExternalPlanCode":"INDSTG20200131234543",
    "ProductSubCategory":"Smartphone",
    "State":"Maharastra",
    "Zipcode":400093,
    "SalesChannel":"Samsung",
    "PartnerServiceLocationID":"4"
  }
 ```

**Request Parameter Description**<br>

**ExternalReferenceID** - String <br>
External reference ID of plan, it is client referenceid of plan

**ProductUniqueID** - String <br>
IMEI Number of device

**SerialNumber** - String <br>
Serial number of device

**AlternateUniqueKey** - String <br>
Device's second IMEI number

**DeviceDateOfPurchase** - String <br>
Device date of purchase, date format is YYYY-MM-DD

**CustomerName** - String <br>
Customer name who has purchased the plan

**PhoneCode** - String <br>
Customer phone number's country code

**CountryCode** - String <br>
Country code of customer

**MobileNo** - String <br>
Mobile number of customer

**EmailID** - String <br>
Email address of customer

**AlternateMobileNo** - String <br>
Alternate mobile number of customer

**BrandName** - String <br>
Brand name of customer device

**ProductName** - String <br>
Product name of customer device

**DateOfPurchase** - String <br>
Plan purchase date, date format is YYYY-MM-DD

**ExternalPlanCode** - String <br>
External plan code, it is client's unique plan code

**ProductSubCategory** - String <br>
Device product sub category, which is provided by Servify

**State** - String <br>
Customer's state

**Zipcode** - String <br>
Customer's zipcode

**SalesChannel** - String <br>
Plan sale source, which is provided by Servify

**PartnerServiceLocationID** - String <br>
Service center ID, which is provided by Servify
***
>**Encrypted Response :**

```json
{
    "$data": "<ENCRYPTED_RESPONSE>"
}
```
***
>**Decrypted Response Body:**

```json
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": {
      "InvoiceNo": "SLT/20-21/Plan/12244222",
      "SoldPlanCode": "M345DERT"
  }
}
```
**Response Object Parameters**

**status** - Number <br>
HTTP status code of the request

**success** - Boolean <br>
Value can be true/false. This will represent the success or failure of the API execution

**message** - String <br>
A meaningful, end-user-readable (or at the least log-worthy) message, explaining what went wrong

**data** - Object<br>
Contains the response payload
***
**Children attributes**
**InvoiceNo** - String <br>
Invoice number of created plan in Servify

**SoldPlanCode** - String
Plan code of Servify


### updatePlan
This API is used to update plan details.

>**Sample cURL:**

```shell
curl --location --request POST '<https://clientstag.servify.tech/primePublicApi/api/v1/SoldPlan/updatePlan'> \
--header 'Content-Type: application/json' \
--header 'client-id: <CLIENT_ID>' \
--header 'hmac-signature: <HMAC_SIGNATURE>' \
--header 'x-date: <DATE>' \
--header 'x-host: <CLIENT_HOST.COM>' \
--header 'client-session-id: <CLIENT_SESSION_ID>' \
--data-raw '{ "$data":"<ENCRYPTED_DATA>" }'
```
>**Decrypted Request Body:**

```json
{
    "OrderNumber": "SLT/20-21/Plan/S00030823",
    "ResponseCode": 1
}
```
**Request Parameter Description**<br>

**OrderNumber** - String <br>
Invoice number, which was shared in "createSoldPlan" API response by Servify.

**ResponseCode** - Number<br>
Need to determine plan is created or not in client system, its value will be 1 for success or 0 for fail. It will be update in Servify system.

>**Decrypted Response Body:**

```json
{
    "success": true,
    "code": "aegis_441",
    "msg": "Order updated",
    "data": {
        "InvoiceNo": "SLT/20-21/Plan/S00030870",
        "PurchaseFailure": true 
    }
}
```

**Response Object Parameters** <br>

**code** - String <br>
Response code from Servify (can be ignored by client)

**success** - Boolean <br>
Value can be true/false. This will represent the success or failure of the API execution

**msg** - String <br>
A meaningful, end-user-readable (or at the least log-worthy) message, explaining what went wrong

**data** - Object <br>
Contains the response payload

**Child attributes of data object:**

**InvoiceNo** - String <br>
Invoice number of plan

**PurchaseFailure** - Boolean <br>
In Servify system plan is the purchase or not flag, if the value is true means successfully purchase or value is false means failed to purchase


# TradeIn
### getBrands
This API is used to get a brand list which is registered in Servify's system for the client.

********
>**Sample cURL:**

```shell
curl --location --request POST '<https://clientstag.servify.tech/primePublicApi/api/v1/TradeIn/getBrands'> \
--header 'Content-Type: application/json' \
--header 'client-id: <CLIENT_ID>' \
--header 'hmac-signature: <HMAC_SIGNATURE>' \
--header 'x-date: <DATE>' \
--header 'x-host: <CLIENT_HOST.COM>' \
--header 'client-session-id: <CLIENT_SESSION_ID>' \
--data-raw '{ "$data":"<ENCRYPTED_DATA>" }'
```

>**Decrypt Request Body:**

```json
{
    "partner": "Servify Partner"
}
```

**Request Parameter Description**

**partner** - String
Partner name which is provided by Servify during integration.

>**Encrypted Response :**

```json
{
    "$data": "<ENCRYPTED_RESPONSE>"
}
```

***

>**Decrypted Response Body:**

```json
{
    "data": {
        "brands": [{
            "brandName": "Apple"
        }, {
            "brandName": "LGE"
        }, {
            "brandName": "Motorola"
        }, {
            "brandName": "Nokia"
        }, {
            "brandName": "OnePlus"
        }, {
            "brandName": "Samsung"
        }, {
            "brandName": "Sony"
        }]
    },
    "statusCode": "SFY.TI.2000",
    "message": "success"
}
```

**Response Object Parameters** <br>

**data** - Object <br>
Contains the response payload.

***
**Child attributes of data object:**

**brands** - Array of objects <br>
It is an array of brands.

***
**Child attributes of brands object:**

**brandName** - String <br>
Name of the brand

**statusCode** - String <br>
Status code of request-response

**message** - String <br>
A meaningful, end-user-readable (or at the least log-worthy) message, explaining what went wrong.



## getProducts
This API is used to get a product list which is registered in Servify's system for the client

***

>**Sample cURL:**

```shell
curl --location --request POST '<https://clientstag.servify.tech/primePublicApi/api/v1/TradeIn/getProducts'> \
--header 'Content-Type: application/json' \
--header 'client-id: <CLIENT_ID>' \
--header 'hmac-signature: <HMAC_SIGNATURE>' \
--header 'x-date: <DATE>' \
--header 'x-host: <CLIENT_HOST.COM>' \
--header 'client-session-id: <CLIENT_SESSION_ID>' \
--data-raw '{ "$data":"<ENCRYPTED_DATA>" }'
```

>**Decrypt Request Body:**

```json
{
    "partner": "Servify Partner"
}
```

**Request Parameter Description**

**partner** - String <br>
Partner name which is provided by Servify during integration.

>**Encrypted Response :**

```json
{
    "$data": "<ENCRYPTED_RESPONSE>"
}
```

>**Decrypted Response Body:**

```json
{
    "data": {
        "productDetails": [{
                "brandName": "Apple",
                "products": [{
                    "productName": "iPhone 6"
                }]
            },
            {
                "brandName": "Samsung",
                "products": [{
                    "productName": "Galaxy S7 edge"
                }]
            }
        ]
    },
    "statusCode": "SFY.TI.2000",
    "message": "success"
}
```

**Response Object Parameters**

**statusCode** - String <br>
Status code of request-response

**message** - String <br>
A meaningful, end-user-readable (or at the least log-worthy) message, explaining what went wrong

**data** - Object <br>
Contains the response payload

***
**Child attributes of data object:**

**productDetails** - Array of objects <br>
Product details of brands

***
**Child attributes of productDetails object:**

**brandName** - String <br>
Brand name of the product

**products** - Array of objects <br>
Product list of brand

***
**Child attributes of products object:**

**productName** - String <br>
Product name of the brand.

***

