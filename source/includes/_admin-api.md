# PaymentIQ Backoffice Admin API v1.3.14-SNAPSHOT

> Scroll down for example requests and responses.

The PaymentIQ Backoffice Admin API is organized around REST and uses JSON. It is language independent and supportedfor virtually all programming languages. <br/><br/>To get started you need to register an api client in backoffice admin > api clients, only backoffice users with merchant admin role are allowed to setup clients. A registered client is assigned a unique Client ID and Client Secret which will be used in the OAuth flow. The client secret should not be shared.The api uses OAuth 2.0 <a href='https://tools.ietf.org/html/rfc6749#section-4.3'>resource owner password credentials grant</a> to issue access tokens on behalf of users. <br/><br/> To request an access token provice base64 encoded [clientId:clientSecret] in the authorization header and your backoffice user credentials.<br/><br/>curl -X POST https://test-backoffice.paymentiq.io/paymentiq/oauth/token -H 'authorization: Basic YzU3YTNlOTlkODAzNDE4Njh' -H 'content-type: application/x-www-form-urlencoded' -d 'username=test&password=test&grant_type=password' <br/><br/>To make an api request provide your bearer token in the authorizaton header.<br/><br/>curl -X GET 'https://test-backoffice.paymentiq.io/paymentiq/admin/v1/payments?merchantId=100101999&limit=10' -H 'authorization: Bearer xxxx.xxxx.xxxxx' 
  -H 'content-type: application/json' \
  -d '{
	"limit": 10
}'<br/><br/>To issue a new access_token if expired provide your refresh_token.<br/><br/>curl -X POST 'https://test-backoffice.paymentiq.io/paymentiq/oauth/token?grant_type=refresh_token&refresh_token=xxx.xxxx.xxxx' -H 'authorization: Basic RDBHNlpLSFVHSjJWV0'

Base URLs:

* <a href="/paymentiq">/paymentiq</a>



Email: <a href="mailto:technicalsupport@bambora.com">PaymentIQ</a> 
 License: undefined

# Authentication



- oAuth2 authentication. 

    - Flow: password

    - Token URL = [oauth/token](oauth/token)

|Scope|Scope Description|
|---|---|
|default|default scope|




# User Accounts

## search_1

`GET /admin/v1/accounts`

*search*

Search user psp account for a merchant and its submerchants.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
merchantId|query|string|true|merchantId
merchants|query|array[string]|false|Array of merchant ids to filter on. By defaut will filter on all mids below current mid available
statuses|query|array[string]|false|List of statuses
providerTypes|query|array[string]|false|List of providerTypes
limit|query|integer(int32)|false|Limit on how many transactions to return. Max limit is 1000. Default is 100.
offset|query|integer(int32)|false|Offset useful for multi page results or pagination
descOrder|query|boolean|false|Descending order
id|query|integer(int32)|false|User account id
firstUsedFrom|query|string(date-time)|false|First used range from
firstUsedTo|query|string(date-time)|false|First used range to
lastUsedFrom|query|string(date-time)|false|Last used range from
lastUsedTo|query|string(date-time)|false|Last used range to
lastSuccessFrom|query|string(date-time)|false|Last success range from
lastSuccessTo|query|string(date-time)|false|Last success range to
startFrom|query|string(date-time)|false|Start range from
startTo|query|string(date-time)|false|Start range to
expiryFrom|query|string(date-time)|false|Expired range from
expiryTo|query|string(date-time)|false|Expired range to
noSuccessfulTxMin|query|integer(int32)|false|Number of min successful transactions
noSuccessfulTxMax|query|integer(int32)|false|Number of max successful transactions
noFailedTxMin|query|integer(int32)|false|Number of min failed transactions
noFailedTxMax|query|integer(int32)|false|Number of max failed transactions
visible|query|boolean|false|User visibility
accountUuid|query|string|false|User account uuid
maskedAccount|query|string|false|User masked account
merchantUserId|query|string|false|Merchant user id
holder|query|string|false|Account holder


#### Enumerated Values

|Parameter|Value|
|---|---|
statuses|ACTIVE|
statuses|INACTIVE|
statuses|NEW|
statuses|DELETED|
statuses|BLOCKED|
statuses|ACTIVE|
statuses|INACTIVE|
statuses|NEW|
statuses|DELETED|
statuses|BLOCKED|
providerTypes|ACCENTPAY|
providerTypes|BANK|
providerTypes|BANKIBAN|
providerTypes|BANKINTIBAN|
providerTypes|BANKINTL|
providerTypes|BANKLOCAL|
providerTypes|CREDITCARD|
providerTypes|NETELLER|
providerTypes|SKRILL|
providerTypes|ENVOY|
providerTypes|PAYSAFECARD|
providerTypes|UKASH|
providerTypes|PAYBOX|
providerTypes|PUGGLEPAY|
providerTypes|CLICKANDBUY|
providerTypes|PAYPAL|
providerTypes|MBANKOMAT|
providerTypes|PAYLEVO|
providerTypes|SIRU|
providerTypes|WORLDPAY|
providerTypes|IBANQ|
providerTypes|IDEAL|
providerTypes|LAVAPAY|
providerTypes|INSTADEBIT|
providerTypes|IDEBIT|
providerTypes|ECOPAYZ|
providerTypes|FORTUMO|
providerTypes|ASTROPAYCARD|
providerTypes|ASTROPAYDIRECT|
providerTypes|PPRO|
providerTypes|YUUCOLLECT|
providerTypes|BOKU|
providerTypes|NEOSURFVOUCHER|
providerTypes|CHINAUNIONPAY|
providerTypes|CITADEL|
providerTypes|PRZELEWY24|
providerTypes|PAYGROUND|
providerTypes|TELEINGRESO|
providerTypes|VENUSPOINT|
providerTypes|ENTROPAY|
providerTypes|MOBILEGIRO|
providerTypes|SMSVOUCHER|
providerTypes|TODITOCASH|
providerTypes|TICKETPREMIUM|
providerTypes|QIWI|
providerTypes|ICARD|
providerTypes|TOLAMOBILE|
providerTypes|FLEXEPIN|
providerTypes|FUNANGA|
providerTypes|VISAVOUCHER|
providerTypes|GIFTCARD|
providerTypes|MIFINITY|
providerTypes|OXXO|
providerTypes|IWALLET|
providerTypes|SEQR|
providerTypes|BOLETO|
providerTypes|CRYPTOCURRENCY|
providerTypes|MUCHBETTER|
providerTypes|KLUWP|
providerTypes|ASTROPAYBANK|
providerTypes|INTERNAL_CORRECTION|
providerTypes|EXTERNAL_CORRECTION|
providerTypes|INTERNAL|
providerTypes|EUTELLER|
providerTypes|TRUSTLY|
providerTypes|EPRO|
providerTypes|CASHLIB|
providerTypes|APCO|
providerTypes|SECURETRADING|
providerTypes|DOTPAY|
providerTypes|BLIK|
providerTypes|UNKNOWN|
providerTypes|ACCENTPAY|
providerTypes|BANK|
providerTypes|BANKIBAN|
providerTypes|BANKINTIBAN|
providerTypes|BANKINTL|
providerTypes|BANKLOCAL|
providerTypes|CREDITCARD|
providerTypes|NETELLER|
providerTypes|SKRILL|
providerTypes|ENVOY|
providerTypes|PAYSAFECARD|
providerTypes|UKASH|
providerTypes|PAYBOX|
providerTypes|PUGGLEPAY|
providerTypes|CLICKANDBUY|
providerTypes|PAYPAL|
providerTypes|MBANKOMAT|
providerTypes|PAYLEVO|
providerTypes|SIRU|
providerTypes|WORLDPAY|
providerTypes|IBANQ|
providerTypes|IDEAL|
providerTypes|LAVAPAY|
providerTypes|INSTADEBIT|
providerTypes|IDEBIT|
providerTypes|ECOPAYZ|
providerTypes|FORTUMO|
providerTypes|ASTROPAYCARD|
providerTypes|ASTROPAYDIRECT|
providerTypes|PPRO|
providerTypes|YUUCOLLECT|
providerTypes|BOKU|
providerTypes|NEOSURFVOUCHER|
providerTypes|CHINAUNIONPAY|
providerTypes|CITADEL|
providerTypes|PRZELEWY24|
providerTypes|PAYGROUND|
providerTypes|TELEINGRESO|
providerTypes|VENUSPOINT|
providerTypes|ENTROPAY|
providerTypes|MOBILEGIRO|
providerTypes|SMSVOUCHER|
providerTypes|TODITOCASH|
providerTypes|TICKETPREMIUM|
providerTypes|QIWI|
providerTypes|ICARD|
providerTypes|TOLAMOBILE|
providerTypes|FLEXEPIN|
providerTypes|FUNANGA|
providerTypes|VISAVOUCHER|
providerTypes|GIFTCARD|
providerTypes|MIFINITY|
providerTypes|OXXO|
providerTypes|IWALLET|
providerTypes|SEQR|
providerTypes|BOLETO|
providerTypes|CRYPTOCURRENCY|
providerTypes|MUCHBETTER|
providerTypes|KLUWP|
providerTypes|ASTROPAYBANK|
providerTypes|INTERNAL_CORRECTION|
providerTypes|EXTERNAL_CORRECTION|
providerTypes|INTERNAL|
providerTypes|EUTELLER|
providerTypes|TRUSTLY|
providerTypes|EPRO|
providerTypes|CASHLIB|
providerTypes|APCO|
providerTypes|SECURETRADING|
providerTypes|DOTPAY|
providerTypes|BLIK|
providerTypes|UNKNOWN|

> Example responses

```json
[
  {
    "id": 1,
    "merchantId": 1234,
    "accountUuid": "958acd6b-b386-4a2c-bead-e3ed49613d44",
    "merchantUserId": "ENVOY",
    "holder": "testuser",
    "type": "CreditcardDeposit",
    "providerType": "CREDITCARD",
    "hashedAccount": "958acd6b-b386-4a2c-bead-e3ed49613d44",
    "maskedAccount": "4444********1234",
    "startDate": "2020-01-01 00:00:00",
    "expiryDate": "2020-01-01 00:00:00",
    "firstUsed": "2020-01-01 00:00:00",
    "lastUsed": "2020-01-01 00:00:00",
    "lastSuccess": "2020-01-01 00:00:00",
    "noSuccessfulTx": 20,
    "noFailedTx": 10,
    "description": "string",
    "status": "ACTIVE"
  }
]
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully found user psp accounts|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for search request|[ErrorResponse](#schemaerrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[UserAccountResponse](#schemauseraccountresponse)]|false|No description
?? id|integer(int64)|false|User account id
?? merchantId|integer(int32)|false|Merchant id
?? accountUuid|string|false|Account UUID
?? merchantUserId|string|false|Merchant user id
?? holder|string|false|Card holder
?? type|string|false|Transaction type
?? providerType|string|false|Provider type
?? hashedAccount|string|false|Hashed account
?? maskedAccount|string|false|Masked account
?? startDate|string(date-time)|false|Date when account can first be used (if applicable)
?? expiryDate|string(date-time)|false|Date when account will expiry (if applicable)
?? firstUsed|string(date-time)|false|When account was first used
?? lastUsed|string(date-time)|false|When account was last used
?? lastSuccess|string(date-time)|false|When account had last successful tx
?? noSuccessfulTx|integer(int32)|false|No of successful transactions
?? noFailedTx|integer(int32)|false|No of failed transactions
?? description|string|false|Description for the use of psp account
?? status|string|false|User account status



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

# Payments

## search

`GET /admin/v1/payments`

*search*

Search transactions for a merchant and its submerchants.

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
merchantId|query|string|true|merchantId
currencies|query|array[string]|false|Array of ISO 3-letter currency, e.g. SEK,EUR,USD
states|query|array[string]|false|Array of states, example SUCCESSFUL, REGISTERED
statuses|query|array[string]|false|Array of statuses, example SUCCESS, WAITING_INPUT
txTypes|query|array[string]|false|Array of transaction types, example CreditcardDeposit, CreditcardWithdrawal
psps|query|array[string]|false|Array of psps, example Entropay, Realex, Pacnet
initiatedPsps|query|array[string]|false|Array of initiated psps, example Entropay, Realex, Pacnet
idList|query|array[integer]|false|List of transaction ids
limit|query|integer(int32)|false|Limit on how many transactions to return. Max limit is 10 000. Default is 100.
offset|query|integer(int32)|false|Offset useful for multi page results or pagination
descOrder|query|boolean|false|Descending order
id|query|integer(int64)|false|Transaction id
originTxId|query|integer(int64)|false|Origin transaction id
txRefId|query|string|false|Normally (for now) the user is only allowed to search on the currently logged-in users mid. Transaction ref id in format ${merchantId}A${id}
pspStatusCode|query|string|false|Psp status code
pspAccount|query|string|false|Psp account
channelId|query|string|false|Channel id
merchantUserCat|query|string|false|Merchant user cat
merchantUserCountryCode|query|string|false|Merchant user country code, example PER = PERU
merchantUserId|query|string|false|Merchant user id
merchantUserEmail|query|string|false|Merchant user email
maskedUserAccount|query|string|false|Masked user account
ipAddr|query|string|false|Ip address
pspRefId|query|string|false|Psp ref id
includeRelated|query|boolean|false|Include related transactions
txDateFrom|query|string(date-time)|false|Transaction date from yyyy-MM-dd HH:mm:ss
txDateTo|query|string(date-time)|false|Transaction date to yyyy-MM-dd HH:mm:ss


#### Enumerated Values

|Parameter|Value|
|---|---|
currencies|AED|
currencies|AFN|
currencies|ALL|
currencies|AMD|
currencies|ANG|
currencies|AOA|
currencies|ARS|
currencies|AUD|
currencies|AWG|
currencies|AZN|
currencies|BAM|
currencies|BBD|
currencies|BDT|
currencies|BGN|
currencies|BHD|
currencies|BIF|
currencies|BMD|
currencies|BND|
currencies|BOB|
currencies|BOV|
currencies|BRL|
currencies|BSD|
currencies|BTN|
currencies|BWP|
currencies|BYR|
currencies|BZD|
currencies|CAD|
currencies|CDF|
currencies|CHE|
currencies|CHF|
currencies|CHW|
currencies|CLF|
currencies|CLP|
currencies|CNY|
currencies|COP|
currencies|COU|
currencies|CRC|
currencies|CUC|
currencies|CUP|
currencies|CVE|
currencies|CZK|
currencies|DJF|
currencies|DKK|
currencies|DOP|
currencies|DZD|
currencies|EGP|
currencies|ERN|
currencies|ETB|
currencies|EUR|
currencies|FJD|
currencies|FKP|
currencies|GBP|
currencies|GEL|
currencies|GHS|
currencies|GIP|
currencies|GMD|
currencies|GNF|
currencies|GTQ|
currencies|GYD|
currencies|HKD|
currencies|HNL|
currencies|HRK|
currencies|HTG|
currencies|HUF|
currencies|IDR|
currencies|ILS|
currencies|INR|
currencies|IQD|
currencies|IRR|
currencies|ISK|
currencies|JMD|
currencies|JOD|
currencies|JPY|
currencies|KES|
currencies|KGS|
currencies|KHR|
currencies|KMF|
currencies|KPW|
currencies|KRW|
currencies|KWD|
currencies|KYD|
currencies|KZT|
currencies|LAK|
currencies|LBP|
currencies|LKR|
currencies|LRD|
currencies|LSL|
currencies|LTL|
currencies|LVL|
currencies|LYD|
currencies|MAD|
currencies|MDL|
currencies|MGA|
currencies|MKD|
currencies|MMK|
currencies|MNT|
currencies|MOP|
currencies|MRO|
currencies|MUR|
currencies|MVR|
currencies|MWK|
currencies|MXN|
currencies|MXV|
currencies|MYR|
currencies|MZN|
currencies|NAD|
currencies|NGN|
currencies|NIO|
currencies|NOK|
currencies|NPR|
currencies|NZD|
currencies|OMR|
currencies|PAB|
currencies|PEN|
currencies|PGK|
currencies|PHP|
currencies|PKR|
currencies|PLN|
currencies|PYG|
currencies|QAR|
currencies|RON|
currencies|RSD|
currencies|RUB|
currencies|RWF|
currencies|SAR|
currencies|SBD|
currencies|SCR|
currencies|SDG|
currencies|SEK|
currencies|SGD|
currencies|SHP|
currencies|SLL|
currencies|SOS|
currencies|SRD|
currencies|STD|
currencies|SYP|
currencies|SZL|
currencies|THB|
currencies|TJS|
currencies|TMT|
currencies|TND|
currencies|TOP|
currencies|TRY|
currencies|TTD|
currencies|TWD|
currencies|TZS|
currencies|UAH|
currencies|UGX|
currencies|USD|
currencies|USN|
currencies|USS|
currencies|UYU|
currencies|UZS|
currencies|VEF|
currencies|VND|
currencies|VUV|
currencies|WST|
currencies|XAF|
currencies|XAG|
currencies|XAU|
currencies|XBA|
currencies|XBB|
currencies|XBC|
currencies|XBD|
currencies|XCD|
currencies|XDR|
currencies|XFU|
currencies|XOF|
currencies|XPD|
currencies|XPF|
currencies|XPT|
currencies|XTS|
currencies|XXX|
currencies|YER|
currencies|ZAR|
currencies|ZMK|
currencies|ZWL|
currencies|AED|
currencies|AFN|
currencies|ALL|
currencies|AMD|
currencies|ANG|
currencies|AOA|
currencies|ARS|
currencies|AUD|
currencies|AWG|
currencies|AZN|
currencies|BAM|
currencies|BBD|
currencies|BDT|
currencies|BGN|
currencies|BHD|
currencies|BIF|
currencies|BMD|
currencies|BND|
currencies|BOB|
currencies|BOV|
currencies|BRL|
currencies|BSD|
currencies|BTN|
currencies|BWP|
currencies|BYR|
currencies|BZD|
currencies|CAD|
currencies|CDF|
currencies|CHE|
currencies|CHF|
currencies|CHW|
currencies|CLF|
currencies|CLP|
currencies|CNY|
currencies|COP|
currencies|COU|
currencies|CRC|
currencies|CUC|
currencies|CUP|
currencies|CVE|
currencies|CZK|
currencies|DJF|
currencies|DKK|
currencies|DOP|
currencies|DZD|
currencies|EGP|
currencies|ERN|
currencies|ETB|
currencies|EUR|
currencies|FJD|
currencies|FKP|
currencies|GBP|
currencies|GEL|
currencies|GHS|
currencies|GIP|
currencies|GMD|
currencies|GNF|
currencies|GTQ|
currencies|GYD|
currencies|HKD|
currencies|HNL|
currencies|HRK|
currencies|HTG|
currencies|HUF|
currencies|IDR|
currencies|ILS|
currencies|INR|
currencies|IQD|
currencies|IRR|
currencies|ISK|
currencies|JMD|
currencies|JOD|
currencies|JPY|
currencies|KES|
currencies|KGS|
currencies|KHR|
currencies|KMF|
currencies|KPW|
currencies|KRW|
currencies|KWD|
currencies|KYD|
currencies|KZT|
currencies|LAK|
currencies|LBP|
currencies|LKR|
currencies|LRD|
currencies|LSL|
currencies|LTL|
currencies|LVL|
currencies|LYD|
currencies|MAD|
currencies|MDL|
currencies|MGA|
currencies|MKD|
currencies|MMK|
currencies|MNT|
currencies|MOP|
currencies|MRO|
currencies|MUR|
currencies|MVR|
currencies|MWK|
currencies|MXN|
currencies|MXV|
currencies|MYR|
currencies|MZN|
currencies|NAD|
currencies|NGN|
currencies|NIO|
currencies|NOK|
currencies|NPR|
currencies|NZD|
currencies|OMR|
currencies|PAB|
currencies|PEN|
currencies|PGK|
currencies|PHP|
currencies|PKR|
currencies|PLN|
currencies|PYG|
currencies|QAR|
currencies|RON|
currencies|RSD|
currencies|RUB|
currencies|RWF|
currencies|SAR|
currencies|SBD|
currencies|SCR|
currencies|SDG|
currencies|SEK|
currencies|SGD|
currencies|SHP|
currencies|SLL|
currencies|SOS|
currencies|SRD|
currencies|STD|
currencies|SYP|
currencies|SZL|
currencies|THB|
currencies|TJS|
currencies|TMT|
currencies|TND|
currencies|TOP|
currencies|TRY|
currencies|TTD|
currencies|TWD|
currencies|TZS|
currencies|UAH|
currencies|UGX|
currencies|USD|
currencies|USN|
currencies|USS|
currencies|UYU|
currencies|UZS|
currencies|VEF|
currencies|VND|
currencies|VUV|
currencies|WST|
currencies|XAF|
currencies|XAG|
currencies|XAU|
currencies|XBA|
currencies|XBB|
currencies|XBC|
currencies|XBD|
currencies|XCD|
currencies|XDR|
currencies|XFU|
currencies|XOF|
currencies|XPD|
currencies|XPF|
currencies|XPT|
currencies|XTS|
currencies|XXX|
currencies|YER|
currencies|ZAR|
currencies|ZMK|
currencies|ZWL|
states|SUCCESSFUL|
states|REGISTERED|
states|PROCESSING|
states|WAITING_INPUT|
states|WAITING_APPROVAL|
states|FAILED|
states|INCONSISTENT|
states|CANCELLED|
states|REPROCESSING|
states|SUCCESSFUL|
states|REGISTERED|
states|PROCESSING|
states|WAITING_INPUT|
states|WAITING_APPROVAL|
states|FAILED|
states|INCONSISTENT|
states|CANCELLED|
states|REPROCESSING|
statuses|SUCCESS|
statuses|SUCCESS_WITHDRAWAL_APPROVAL|
statuses|SUCCESS_WITHDRAWAL_AUTO_APPROVAL|
statuses|SUCCESS_WAITING_CAPTURE|
statuses|SUCCESS_WAITING_AUTO_CAPTURE|
statuses|SUCCESS_AUTO_CAPTURED|
statuses|SUCCESS_CAPTURED|
statuses|REGISTERED|
statuses|PROCESSING_PROVIDER|
statuses|PROCESSING_MERCHANT|
statuses|CONT_WITH_N3DS|
statuses|REPROCESSING_PROVIDER|
statuses|REPROCESSING_MERCHANT|
statuses|WAITING_INPUT|
statuses|WAITING_3D_SECURE|
statuses|WAITING_DEPOSIT_CONFIRMATION|
statuses|WAITING_NOTIFICATION|
statuses|WAITING_DEPOSIT_APPROVAL|
statuses|WAITING_WITHDRAWAL_APPROVAL|
statuses|WAITING_DEPOSIT_AUTO_APPROVAL|
statuses|WAITING_WITHDRAWAL_AUTO_APPROVAL|
statuses|WAITING_DEPOSIT_ON_HOLD_APPROVAL|
statuses|WAITING_WITHDRAWAL_ON_HOLD_APPROVAL|
statuses|ERR_READ_TIMEOUT|
statuses|ERR_REFERENCE_MISMATCH|
statuses|ERR_INCONSISTENT_TRANSACTION|
statuses|ERR_UNKNOWN_CALLBACK|
statuses|ERR_IO_EXCEPTION|
statuses|ERR_UNKNOWN_RESPONSE|
statuses|ERR_SYSTEM_ERROR|
statuses|ERR_FAILED_TO_CONNECT|
statuses|ERR_DECLINED_BAD_REQUEST|
statuses|ERR_DECLINED_FRAUD|
statuses|ERR_DECLINED_NO_FUNDS|
statuses|ERR_DECLINED_ACCOUNT_SUSPENDED|
statuses|ERR_DECLINED_OTHER_REASON|
statuses|ERR_DECLINED_CONTACT_SUPPORT|
statuses|ERR_DECLINED_CONFIG_ERROR|
statuses|ERR_NOT_AUTHENTICATED|
statuses|ERR_INVALID_RESPONSE|
statuses|ERR_DECLINED_REQ_BLOCKED|
statuses|ERR_PSP_OUT_OF_SERVICE|
statuses|ERR_DECLINED_NOT_AUTHORIZED|
statuses|ERR_RESPONSE_CODE_UNKNOWN|
statuses|ERR_PSP_ACCOUNT_USED_BY_OTHER_USER|
statuses|ERR_PSP_ACCOUNT_NOT_USED|
statuses|ERR_TOO_MANY_PSP_ACCOUNTS|
statuses|ERR_DECLINED_DUPLICATE_TX_ID|
statuses|ERR_DECLINED_INVALID_ACCOUNT_NUMBER|
statuses|ERR_MERCHANT_OUT_OF_SERVICE|
statuses|ERR_DECLINED_LIMIT_OVERDRAWN|
statuses|ERR_MERCHANT_RESPONSE_CODE_UNKNOWN|
statuses|ERR_DECLINED_NO_PROVIDER_FOUND|
statuses|ERR_DECLINED_PROVIDER_ACCOUNT_CONFIG_ERROR|
statuses|ERR_MERCHANT_INVALID_RESPONSE|
statuses|ERR_DECLINED_3D_VALIDATION_FAILED|
statuses|ERR_DECLINED_3D_EXPIRED|
statuses|ERR_VAULTIQ_OUT_OF_SERVICE|
statuses|ERR_DECLINED_IP_BLOCKED|
statuses|ERR_DECLINED_BIN_BLOCKED|
statuses|ERR_VAULTIQ_UNKNOWN_ACCOUNT|
statuses|ERR_DECLINED_KYC_BLOCK|
statuses|ERR_DECLINED_KYC_USER_UNDER_AGE|
statuses|ERR_DECLINED_KYC_CHECK_FAILED|
statuses|ERR_DECLINED_BIC_BLOCK|
statuses|ERR_DECLINED_EXPIRED|
statuses|ERR_DECLINED_REPEAT_CANCELLED|
statuses|ERR_DECLINED_CURRENCY_NOT_SUPPORTED|
statuses|ERR_DECLINED_FRAUD_SCORE_THRESHOLD_EXCEEDED|
statuses|ERR_DECLINED_MERCHANT_NOT_FOUND|
statuses|ERR_DECLINED_MERCHANT_NOT_ENABLED|
statuses|ERR_DECLINED_PROVIDER_NOT_ENABLED|
statuses|ERR_DECLINED_UNDER_MAINTENANCE|
statuses|ERR_NO_REFERRAL_TX_FOUND|
statuses|ERR_DECLINE_TX_NOT_FOUND|
statuses|ERR_DECLINE_COUNTRY_NOT_SUPPORTED|
statuses|ERR_DECLINED_NOT_SUPPORTED_PAYMENT_METHOD_FRAUD|
statuses|ERR_DECLINED_FRAUD_PROVIDER_ACCOUNT_CONFIG_ERROR|
statuses|ERR_CANCELLED_BY_USER|
statuses|ERR_CANCELLED_BY_MERCHANT|
statuses|ERR_CANCELLED_BY_PSP|
statuses|SUCCESS|
statuses|SUCCESS_WITHDRAWAL_APPROVAL|
statuses|SUCCESS_WITHDRAWAL_AUTO_APPROVAL|
statuses|SUCCESS_WAITING_CAPTURE|
statuses|SUCCESS_WAITING_AUTO_CAPTURE|
statuses|SUCCESS_AUTO_CAPTURED|
statuses|SUCCESS_CAPTURED|
statuses|REGISTERED|
statuses|PROCESSING_PROVIDER|
statuses|PROCESSING_MERCHANT|
statuses|CONT_WITH_N3DS|
statuses|REPROCESSING_PROVIDER|
statuses|REPROCESSING_MERCHANT|
statuses|WAITING_INPUT|
statuses|WAITING_3D_SECURE|
statuses|WAITING_DEPOSIT_CONFIRMATION|
statuses|WAITING_NOTIFICATION|
statuses|WAITING_DEPOSIT_APPROVAL|
statuses|WAITING_WITHDRAWAL_APPROVAL|
statuses|WAITING_DEPOSIT_AUTO_APPROVAL|
statuses|WAITING_WITHDRAWAL_AUTO_APPROVAL|
statuses|WAITING_DEPOSIT_ON_HOLD_APPROVAL|
statuses|WAITING_WITHDRAWAL_ON_HOLD_APPROVAL|
statuses|ERR_READ_TIMEOUT|
statuses|ERR_REFERENCE_MISMATCH|
statuses|ERR_INCONSISTENT_TRANSACTION|
statuses|ERR_UNKNOWN_CALLBACK|
statuses|ERR_IO_EXCEPTION|
statuses|ERR_UNKNOWN_RESPONSE|
statuses|ERR_SYSTEM_ERROR|
statuses|ERR_FAILED_TO_CONNECT|
statuses|ERR_DECLINED_BAD_REQUEST|
statuses|ERR_DECLINED_FRAUD|
statuses|ERR_DECLINED_NO_FUNDS|
statuses|ERR_DECLINED_ACCOUNT_SUSPENDED|
statuses|ERR_DECLINED_OTHER_REASON|
statuses|ERR_DECLINED_CONTACT_SUPPORT|
statuses|ERR_DECLINED_CONFIG_ERROR|
statuses|ERR_NOT_AUTHENTICATED|
statuses|ERR_INVALID_RESPONSE|
statuses|ERR_DECLINED_REQ_BLOCKED|
statuses|ERR_PSP_OUT_OF_SERVICE|
statuses|ERR_DECLINED_NOT_AUTHORIZED|
statuses|ERR_RESPONSE_CODE_UNKNOWN|
statuses|ERR_PSP_ACCOUNT_USED_BY_OTHER_USER|
statuses|ERR_PSP_ACCOUNT_NOT_USED|
statuses|ERR_TOO_MANY_PSP_ACCOUNTS|
statuses|ERR_DECLINED_DUPLICATE_TX_ID|
statuses|ERR_DECLINED_INVALID_ACCOUNT_NUMBER|
statuses|ERR_MERCHANT_OUT_OF_SERVICE|
statuses|ERR_DECLINED_LIMIT_OVERDRAWN|
statuses|ERR_MERCHANT_RESPONSE_CODE_UNKNOWN|
statuses|ERR_DECLINED_NO_PROVIDER_FOUND|
statuses|ERR_DECLINED_PROVIDER_ACCOUNT_CONFIG_ERROR|
statuses|ERR_MERCHANT_INVALID_RESPONSE|
statuses|ERR_DECLINED_3D_VALIDATION_FAILED|
statuses|ERR_DECLINED_3D_EXPIRED|
statuses|ERR_VAULTIQ_OUT_OF_SERVICE|
statuses|ERR_DECLINED_IP_BLOCKED|
statuses|ERR_DECLINED_BIN_BLOCKED|
statuses|ERR_VAULTIQ_UNKNOWN_ACCOUNT|
statuses|ERR_DECLINED_KYC_BLOCK|
statuses|ERR_DECLINED_KYC_USER_UNDER_AGE|
statuses|ERR_DECLINED_KYC_CHECK_FAILED|
statuses|ERR_DECLINED_BIC_BLOCK|
statuses|ERR_DECLINED_EXPIRED|
statuses|ERR_DECLINED_REPEAT_CANCELLED|
statuses|ERR_DECLINED_CURRENCY_NOT_SUPPORTED|
statuses|ERR_DECLINED_FRAUD_SCORE_THRESHOLD_EXCEEDED|
statuses|ERR_DECLINED_MERCHANT_NOT_FOUND|
statuses|ERR_DECLINED_MERCHANT_NOT_ENABLED|
statuses|ERR_DECLINED_PROVIDER_NOT_ENABLED|
statuses|ERR_DECLINED_UNDER_MAINTENANCE|
statuses|ERR_NO_REFERRAL_TX_FOUND|
statuses|ERR_DECLINE_TX_NOT_FOUND|
statuses|ERR_DECLINE_COUNTRY_NOT_SUPPORTED|
statuses|ERR_DECLINED_NOT_SUPPORTED_PAYMENT_METHOD_FRAUD|
statuses|ERR_DECLINED_FRAUD_PROVIDER_ACCOUNT_CONFIG_ERROR|
statuses|ERR_CANCELLED_BY_USER|
statuses|ERR_CANCELLED_BY_MERCHANT|
statuses|ERR_CANCELLED_BY_PSP|
txTypes|CreditcardDeposit|
txTypes|CreditcardWithdrawal|
txTypes|EntropayDeposit|
txTypes|ICardDeposit|
txTypes|ICardWithdrawal|
txTypes|NetellerDeposit|
txTypes|NetellerWithdrawal|
txTypes|SkrillDeposit|
txTypes|SkrillWithdrawal|
txTypes|PayboxDeposit|
txTypes|ClickandBuyDeposit|
txTypes|ClickandBuyWithdrawal|
txTypes|PayPalDeposit|
txTypes|PayPalWithdrawal|
txTypes|MbankomatDeposit|
txTypes|IBanqDeposit|
txTypes|IBanqWithdrawal|
txTypes|LavaPayDeposit|
txTypes|LavaPayWithdrawal|
txTypes|InstadebitDeposit|
txTypes|InstadebitWithdrawal|
txTypes|IDebitDeposit|
txTypes|IDebitWithdrawal|
txTypes|EcoPayzDeposit|
txTypes|EcoPayzWithdrawal|
txTypes|AstroPayCardWithdrawal|
txTypes|AstroPayDirectDeposit|
txTypes|AstroPayDirectWithdrawal|
txTypes|VenusPointDeposit|
txTypes|VenusPointWithdrawal|
txTypes|MiFinityEWalletDeposit|
txTypes|MiFinityEWalletWithdrawal|
txTypes|IWalletDeposit|
txTypes|IWalletWithdrawal|
txTypes|MuchBetterDeposit|
txTypes|MuchBetterWithdrawal|
txTypes|AstroPayBankWithdrawal|
txTypes|EutellerDeposit|
txTypes|EnvoyDeposit|
txTypes|EnvoyWithdrawal|
txTypes|TrustlyDeposit|
txTypes|TrustlyWithdrawal|
txTypes|BankDeposit|
txTypes|BankLocalWithdrawal|
txTypes|BankIBANWithdrawal|
txTypes|BankIntIBANWithdrawal|
txTypes|IdealDeposit|
txTypes|ChinaUnionPayDeposit|
txTypes|BankIntlWithdrawal|
txTypes|ChinaUnionPayWithdrawal|
txTypes|BoletoBancarioDeposit|
txTypes|PaysafecardDeposit|
txTypes|UkashDeposit|
txTypes|UkashWithdrawal|
txTypes|PaysafecardWithdrawal|
txTypes|CashlibDeposit|
txTypes|TicketPremiumDeposit|
txTypes|FlexepinDeposit|
txTypes|FunangaDeposit|
txTypes|VisaVoucherDeposit|
txTypes|GiftcardDeposit|
txTypes|PugglePayDeposit|
txTypes|PaylevoDeposit|
txTypes|YuuCollectDeposit|
txTypes|NeosurfVoucherDeposit|
txTypes|OxxoDeposit|
txTypes|SeqrDeposit|
txTypes|CryptoCurrencyDeposit|
txTypes|SeqrWithdrawal|
txTypes|SiruDeposit|
txTypes|SiruStatus|
txTypes|SiruPriceCalc|
txTypes|FortumoDeposit|
txTypes|BokuDeposit|
txTypes|BlikDeposit|
txTypes|PayGroundDeposit|
txTypes|SmsVoucherDeposit|
txTypes|QiwiDeposit|
txTypes|QiwiWithdrawal|
txTypes|AccentPayDeposit|
txTypes|AccentPayWithdrawal|
txTypes|WorldPayDeposit|
txTypes|WorldPayWithdrawal|
txTypes|PProDeposit|
txTypes|PProWithdrawal|
txTypes|EProPaymentWallDeposit|
txTypes|ApcoDeposit|
txTypes|SecureTradingDeposit|
txTypes|DotpayDeposit|
txTypes|Przelewy24Deposit|
txTypes|SweGiroDeposit|
txTypes|ToditoCashDeposit|
txTypes|TolaMobileDeposit|
txTypes|KluwpDeposit|
txTypes|TeleingresoDeposit|
txTypes|ManualChargeback|
txTypes|ManualRefund|
txTypes|ManualCancel|
txTypes|ManualVoid|
txTypes|ManualChargeBackWon|
txTypes|Refund|
txTypes|Cancel|
txTypes|Void|
txTypes|Capture|
txTypes|CreditcardDeposit|
txTypes|CreditcardWithdrawal|
txTypes|EntropayDeposit|
txTypes|ICardDeposit|
txTypes|ICardWithdrawal|
txTypes|NetellerDeposit|
txTypes|NetellerWithdrawal|
txTypes|SkrillDeposit|
txTypes|SkrillWithdrawal|
txTypes|PayboxDeposit|
txTypes|ClickandBuyDeposit|
txTypes|ClickandBuyWithdrawal|
txTypes|PayPalDeposit|
txTypes|PayPalWithdrawal|
txTypes|MbankomatDeposit|
txTypes|IBanqDeposit|
txTypes|IBanqWithdrawal|
txTypes|LavaPayDeposit|
txTypes|LavaPayWithdrawal|
txTypes|InstadebitDeposit|
txTypes|InstadebitWithdrawal|
txTypes|IDebitDeposit|
txTypes|IDebitWithdrawal|
txTypes|EcoPayzDeposit|
txTypes|EcoPayzWithdrawal|
txTypes|AstroPayCardWithdrawal|
txTypes|AstroPayDirectDeposit|
txTypes|AstroPayDirectWithdrawal|
txTypes|VenusPointDeposit|
txTypes|VenusPointWithdrawal|
txTypes|MiFinityEWalletDeposit|
txTypes|MiFinityEWalletWithdrawal|
txTypes|IWalletDeposit|
txTypes|IWalletWithdrawal|
txTypes|MuchBetterDeposit|
txTypes|MuchBetterWithdrawal|
txTypes|AstroPayBankWithdrawal|
txTypes|EutellerDeposit|
txTypes|EnvoyDeposit|
txTypes|EnvoyWithdrawal|
txTypes|TrustlyDeposit|
txTypes|TrustlyWithdrawal|
txTypes|BankDeposit|
txTypes|BankLocalWithdrawal|
txTypes|BankIBANWithdrawal|
txTypes|BankIntIBANWithdrawal|
txTypes|IdealDeposit|
txTypes|ChinaUnionPayDeposit|
txTypes|BankIntlWithdrawal|
txTypes|ChinaUnionPayWithdrawal|
txTypes|BoletoBancarioDeposit|
txTypes|PaysafecardDeposit|
txTypes|UkashDeposit|
txTypes|UkashWithdrawal|
txTypes|PaysafecardWithdrawal|
txTypes|CashlibDeposit|
txTypes|TicketPremiumDeposit|
txTypes|FlexepinDeposit|
txTypes|FunangaDeposit|
txTypes|VisaVoucherDeposit|
txTypes|GiftcardDeposit|
txTypes|PugglePayDeposit|
txTypes|PaylevoDeposit|
txTypes|YuuCollectDeposit|
txTypes|NeosurfVoucherDeposit|
txTypes|OxxoDeposit|
txTypes|SeqrDeposit|
txTypes|CryptoCurrencyDeposit|
txTypes|SeqrWithdrawal|
txTypes|SiruDeposit|
txTypes|SiruStatus|
txTypes|SiruPriceCalc|
txTypes|FortumoDeposit|
txTypes|BokuDeposit|
txTypes|BlikDeposit|
txTypes|PayGroundDeposit|
txTypes|SmsVoucherDeposit|
txTypes|QiwiDeposit|
txTypes|QiwiWithdrawal|
txTypes|AccentPayDeposit|
txTypes|AccentPayWithdrawal|
txTypes|WorldPayDeposit|
txTypes|WorldPayWithdrawal|
txTypes|PProDeposit|
txTypes|PProWithdrawal|
txTypes|EProPaymentWallDeposit|
txTypes|ApcoDeposit|
txTypes|SecureTradingDeposit|
txTypes|DotpayDeposit|
txTypes|Przelewy24Deposit|
txTypes|SweGiroDeposit|
txTypes|ToditoCashDeposit|
txTypes|TolaMobileDeposit|
txTypes|KluwpDeposit|
txTypes|TeleingresoDeposit|
txTypes|ManualChargeback|
txTypes|ManualRefund|
txTypes|ManualCancel|
txTypes|ManualVoid|
txTypes|ManualChargeBackWon|
txTypes|Refund|
txTypes|Cancel|
txTypes|Void|
txTypes|Capture|
psps|Entropay|
psps|PayPoint|
psps|PayLine|
psps|Realex|
psps|TicketSurf|
psps|Payvision|
psps|SwiftVoucher|
psps|Neosurf|
psps|Credorax|
psps|Wirecard|
psps|NxPay|
psps|EMP|
psps|Vamex|
psps|Payon|
psps|Pacnet|
psps|Borgun|
psps|WorldPay|
psps|PayEx|
psps|CC247|
psps|Computop|
psps|Ilixium|
psps|AstroPayCard|
psps|EMerchantPay|
psps|YuuPay|
psps|AlliedWallet|
psps|WorldPayHCG|
psps|Ochapay|
psps|Redbaron|
psps|Payr|
psps|Argus|
psps|Valitor|
psps|SafeCharge|
psps|Bambora|
psps|Dibs|
psps|Apco|
psps|ASTech|
psps|Fibonatix|
psps|DreamsPay|
psps|Clearhaus|
psps|Citigate|
psps|CreditGuard|
psps|Powerpay21|
psps|EMerchantPayWs|
psps|Kluwp|
psps|MiFinity|
psps|Ingenico|
psps|AltPayNet|
psps|BamboraGa|
psps|Payneteasy|
psps|EPay|
psps|CcMock|
psps|Neteller|
psps|Skrill|
psps|Paybox|
psps|ClickandBuy|
psps|PayPal|
psps|Mbankomat|
psps|Siru|
psps|IBanq|
psps|LavaPay|
psps|VenusPoint|
psps|IWallet|
psps|MuchBetter|
psps|Paysafecard|
psps|Ukash|
psps|Instadebit|
psps|IDebit|
psps|EcoPayz|
psps|Fortumo|
psps|AstroPayDirect|
psps|Boku|
psps|NeosurfVoucher|
psps|PayGround|
psps|SmsVoucher|
psps|Flexepin|
psps|Funanga|
psps|Trustly|
psps|Envoy|
psps|Euteller|
psps|Entercash|
psps|InPay|
psps|Poli|
psps|Sofort|
psps|Transferuj|
psps|Adyen|
psps|RapidPaymentsNetwork|
psps|ManualBanking|
psps|Citadel|
psps|Safetypay|
psps|EasyEft|
psps|Interac|
psps|AstroPayBank|
psps|PugglePay|
psps|Paylevo|
psps|Seqr|
psps|AccentPay|
psps|PPro|
psps|SecureTrading|
psps|Dotpay|
psps|Przelewy24|
psps|MobileGiro|
psps|ToditoCash|
psps|TolaMobile|
psps|Teleingreso|
psps|Bitpay|
psps|FraudGuard|
psps|FeatureSpace|
psps|Undefined|
psps|Unknown|
psps|Entropay|
psps|PayPoint|
psps|PayLine|
psps|Realex|
psps|TicketSurf|
psps|Payvision|
psps|SwiftVoucher|
psps|Neosurf|
psps|Credorax|
psps|Wirecard|
psps|NxPay|
psps|EMP|
psps|Vamex|
psps|Payon|
psps|Pacnet|
psps|Borgun|
psps|WorldPay|
psps|PayEx|
psps|CC247|
psps|Computop|
psps|Ilixium|
psps|AstroPayCard|
psps|EMerchantPay|
psps|YuuPay|
psps|AlliedWallet|
psps|WorldPayHCG|
psps|Ochapay|
psps|Redbaron|
psps|Payr|
psps|Argus|
psps|Valitor|
psps|SafeCharge|
psps|Bambora|
psps|Dibs|
psps|Apco|
psps|ASTech|
psps|Fibonatix|
psps|DreamsPay|
psps|Clearhaus|
psps|Citigate|
psps|CreditGuard|
psps|Powerpay21|
psps|EMerchantPayWs|
psps|Kluwp|
psps|MiFinity|
psps|Ingenico|
psps|AltPayNet|
psps|BamboraGa|
psps|Payneteasy|
psps|EPay|
psps|CcMock|
psps|Neteller|
psps|Skrill|
psps|Paybox|
psps|ClickandBuy|
psps|PayPal|
psps|Mbankomat|
psps|Siru|
psps|IBanq|
psps|LavaPay|
psps|VenusPoint|
psps|IWallet|
psps|MuchBetter|
psps|Paysafecard|
psps|Ukash|
psps|Instadebit|
psps|IDebit|
psps|EcoPayz|
psps|Fortumo|
psps|AstroPayDirect|
psps|Boku|
psps|NeosurfVoucher|
psps|PayGround|
psps|SmsVoucher|
psps|Flexepin|
psps|Funanga|
psps|Trustly|
psps|Envoy|
psps|Euteller|
psps|Entercash|
psps|InPay|
psps|Poli|
psps|Sofort|
psps|Transferuj|
psps|Adyen|
psps|RapidPaymentsNetwork|
psps|ManualBanking|
psps|Citadel|
psps|Safetypay|
psps|EasyEft|
psps|Interac|
psps|AstroPayBank|
psps|PugglePay|
psps|Paylevo|
psps|Seqr|
psps|AccentPay|
psps|PPro|
psps|SecureTrading|
psps|Dotpay|
psps|Przelewy24|
psps|MobileGiro|
psps|ToditoCash|
psps|TolaMobile|
psps|Teleingreso|
psps|Bitpay|
psps|FraudGuard|
psps|FeatureSpace|
psps|Undefined|
psps|Unknown|
initiatedPsps|Entropay|
initiatedPsps|PayPoint|
initiatedPsps|PayLine|
initiatedPsps|Realex|
initiatedPsps|TicketSurf|
initiatedPsps|Payvision|
initiatedPsps|SwiftVoucher|
initiatedPsps|Neosurf|
initiatedPsps|Credorax|
initiatedPsps|Wirecard|
initiatedPsps|NxPay|
initiatedPsps|EMP|
initiatedPsps|Vamex|
initiatedPsps|Payon|
initiatedPsps|Pacnet|
initiatedPsps|Borgun|
initiatedPsps|WorldPay|
initiatedPsps|PayEx|
initiatedPsps|CC247|
initiatedPsps|Computop|
initiatedPsps|Ilixium|
initiatedPsps|AstroPayCard|
initiatedPsps|EMerchantPay|
initiatedPsps|YuuPay|
initiatedPsps|AlliedWallet|
initiatedPsps|WorldPayHCG|
initiatedPsps|Ochapay|
initiatedPsps|Redbaron|
initiatedPsps|Payr|
initiatedPsps|Argus|
initiatedPsps|Valitor|
initiatedPsps|SafeCharge|
initiatedPsps|Bambora|
initiatedPsps|Dibs|
initiatedPsps|Apco|
initiatedPsps|ASTech|
initiatedPsps|Fibonatix|
initiatedPsps|DreamsPay|
initiatedPsps|Clearhaus|
initiatedPsps|Citigate|
initiatedPsps|CreditGuard|
initiatedPsps|Powerpay21|
initiatedPsps|EMerchantPayWs|
initiatedPsps|Kluwp|
initiatedPsps|MiFinity|
initiatedPsps|Ingenico|
initiatedPsps|AltPayNet|
initiatedPsps|BamboraGa|
initiatedPsps|Payneteasy|
initiatedPsps|EPay|
initiatedPsps|CcMock|
initiatedPsps|Neteller|
initiatedPsps|Skrill|
initiatedPsps|Paybox|
initiatedPsps|ClickandBuy|
initiatedPsps|PayPal|
initiatedPsps|Mbankomat|
initiatedPsps|Siru|
initiatedPsps|IBanq|
initiatedPsps|LavaPay|
initiatedPsps|VenusPoint|
initiatedPsps|IWallet|
initiatedPsps|MuchBetter|
initiatedPsps|Paysafecard|
initiatedPsps|Ukash|
initiatedPsps|Instadebit|
initiatedPsps|IDebit|
initiatedPsps|EcoPayz|
initiatedPsps|Fortumo|
initiatedPsps|AstroPayDirect|
initiatedPsps|Boku|
initiatedPsps|NeosurfVoucher|
initiatedPsps|PayGround|
initiatedPsps|SmsVoucher|
initiatedPsps|Flexepin|
initiatedPsps|Funanga|
initiatedPsps|Trustly|
initiatedPsps|Envoy|
initiatedPsps|Euteller|
initiatedPsps|Entercash|
initiatedPsps|InPay|
initiatedPsps|Poli|
initiatedPsps|Sofort|
initiatedPsps|Transferuj|
initiatedPsps|Adyen|
initiatedPsps|RapidPaymentsNetwork|
initiatedPsps|ManualBanking|
initiatedPsps|Citadel|
initiatedPsps|Safetypay|
initiatedPsps|EasyEft|
initiatedPsps|Interac|
initiatedPsps|AstroPayBank|
initiatedPsps|PugglePay|
initiatedPsps|Paylevo|
initiatedPsps|Seqr|
initiatedPsps|AccentPay|
initiatedPsps|PPro|
initiatedPsps|SecureTrading|
initiatedPsps|Dotpay|
initiatedPsps|Przelewy24|
initiatedPsps|MobileGiro|
initiatedPsps|ToditoCash|
initiatedPsps|TolaMobile|
initiatedPsps|Teleingreso|
initiatedPsps|Bitpay|
initiatedPsps|FraudGuard|
initiatedPsps|FeatureSpace|
initiatedPsps|Undefined|
initiatedPsps|Unknown|
initiatedPsps|Entropay|
initiatedPsps|PayPoint|
initiatedPsps|PayLine|
initiatedPsps|Realex|
initiatedPsps|TicketSurf|
initiatedPsps|Payvision|
initiatedPsps|SwiftVoucher|
initiatedPsps|Neosurf|
initiatedPsps|Credorax|
initiatedPsps|Wirecard|
initiatedPsps|NxPay|
initiatedPsps|EMP|
initiatedPsps|Vamex|
initiatedPsps|Payon|
initiatedPsps|Pacnet|
initiatedPsps|Borgun|
initiatedPsps|WorldPay|
initiatedPsps|PayEx|
initiatedPsps|CC247|
initiatedPsps|Computop|
initiatedPsps|Ilixium|
initiatedPsps|AstroPayCard|
initiatedPsps|EMerchantPay|
initiatedPsps|YuuPay|
initiatedPsps|AlliedWallet|
initiatedPsps|WorldPayHCG|
initiatedPsps|Ochapay|
initiatedPsps|Redbaron|
initiatedPsps|Payr|
initiatedPsps|Argus|
initiatedPsps|Valitor|
initiatedPsps|SafeCharge|
initiatedPsps|Bambora|
initiatedPsps|Dibs|
initiatedPsps|Apco|
initiatedPsps|ASTech|
initiatedPsps|Fibonatix|
initiatedPsps|DreamsPay|
initiatedPsps|Clearhaus|
initiatedPsps|Citigate|
initiatedPsps|CreditGuard|
initiatedPsps|Powerpay21|
initiatedPsps|EMerchantPayWs|
initiatedPsps|Kluwp|
initiatedPsps|MiFinity|
initiatedPsps|Ingenico|
initiatedPsps|AltPayNet|
initiatedPsps|BamboraGa|
initiatedPsps|Payneteasy|
initiatedPsps|EPay|
initiatedPsps|CcMock|
initiatedPsps|Neteller|
initiatedPsps|Skrill|
initiatedPsps|Paybox|
initiatedPsps|ClickandBuy|
initiatedPsps|PayPal|
initiatedPsps|Mbankomat|
initiatedPsps|Siru|
initiatedPsps|IBanq|
initiatedPsps|LavaPay|
initiatedPsps|VenusPoint|
initiatedPsps|IWallet|
initiatedPsps|MuchBetter|
initiatedPsps|Paysafecard|
initiatedPsps|Ukash|
initiatedPsps|Instadebit|
initiatedPsps|IDebit|
initiatedPsps|EcoPayz|
initiatedPsps|Fortumo|
initiatedPsps|AstroPayDirect|
initiatedPsps|Boku|
initiatedPsps|NeosurfVoucher|
initiatedPsps|PayGround|
initiatedPsps|SmsVoucher|
initiatedPsps|Flexepin|
initiatedPsps|Funanga|
initiatedPsps|Trustly|
initiatedPsps|Envoy|
initiatedPsps|Euteller|
initiatedPsps|Entercash|
initiatedPsps|InPay|
initiatedPsps|Poli|
initiatedPsps|Sofort|
initiatedPsps|Transferuj|
initiatedPsps|Adyen|
initiatedPsps|RapidPaymentsNetwork|
initiatedPsps|ManualBanking|
initiatedPsps|Citadel|
initiatedPsps|Safetypay|
initiatedPsps|EasyEft|
initiatedPsps|Interac|
initiatedPsps|AstroPayBank|
initiatedPsps|PugglePay|
initiatedPsps|Paylevo|
initiatedPsps|Seqr|
initiatedPsps|AccentPay|
initiatedPsps|PPro|
initiatedPsps|SecureTrading|
initiatedPsps|Dotpay|
initiatedPsps|Przelewy24|
initiatedPsps|MobileGiro|
initiatedPsps|ToditoCash|
initiatedPsps|TolaMobile|
initiatedPsps|Teleingreso|
initiatedPsps|Bitpay|
initiatedPsps|FraudGuard|
initiatedPsps|FeatureSpace|
initiatedPsps|Undefined|
initiatedPsps|Unknown|

> Example responses

```json
[
  {
    "accountHolderName": "test test",
    "amount": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "amountBase": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "authAmount": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "authAmountBase": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "blockedAccountReason": "250EAO",
    "bonusCode": "1111",
    "channelId": "12345",
    "created": "2017-04-27 14:10:38",
    "depositType": "Standard",
    "fee": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "feeBase": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "info": {},
    "initiatedPspAccount": "3DS",
    "initiatedPspId": 108,
    "ipAddr": "141.8.92.216",
    "ipCity": "Msida",
    "ipCountry": "MLT",
    "ipRegion": "string",
    "issuerCountry": "ZZZ",
    "kycStatus": "Accept",
    "lastUpdated": "2017-04-27 14:10:40",
    "maskedUserAccount": "23232*****232",
    "merchantAuthCode": "cc3056ec-735c-4ef6-8126-0b0d94b96b49",
    "merchantErrCode": "1001",
    "merchantId": 1980,
    "merchantTxId": "c15eef34-1f37-43a4-a19b-473dbef541ed",
    "merchantUserBal": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "merchantUserCat": "TEST",
    "merchantUserCountry": "AUS",
    "merchantUserEmail": "test@example.com",
    "merchantUserId": "TEST_USER",
    "originTxId": 193027,
    "pspAccount": "3DS",
    "pspFee": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "pspFeeBase": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "pspFraudScore": 0.02,
    "pspId": 108,
    "pspRefId": "C873789149330223994317",
    "pspService": "250EAO",
    "pspStatusCode": "PENDING",
    "pspTxAmount": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "pspUserRef": "1111",
    "reversedMerchantTxId": "250EAO",
    "reversedTxId": 1000,
    "rules": [
      "string"
    ],
    "statusCode": "SUCCESS",
    "suspectedAbuseReason": "250EAO",
    "txAmount": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "txAmountBase": {
      "amount": 0,
      "amountInFractionUnit": 0,
      "currency": "string",
      "currencyCode": "string",
      "currencyNumeric3Code": "string",
      "fractionDigits": 0,
      "negative": true,
      "positive": true,
      "zero": true
    },
    "updatedBy": "user1",
    "userPspAccountDetails": {
      "accountUuid": "string",
      "blockReason": "string",
      "description": "string",
      "directDebit": true,
      "expiryDate": "2017-11-06T10:24:36Z",
      "extAccountRefId": "string",
      "firstUsed": "2017-11-06T10:24:36Z",
      "hashedAccount": "string",
      "holder": "string",
      "id": 0,
      "lastSuccess": "2017-11-06T10:24:36Z",
      "lastUsed": "2017-11-06T10:24:36Z",
      "maskedAccount": "string",
      "merchantId": 0,
      "merchantUserId": "string",
      "new": true,
      "noFailedTx": 0,
      "noSuccessfulTx": 0,
      "providerType": "string",
      "startDate": "2017-11-06T10:24:36Z",
      "status": "ACTIVE",
      "storeAccount": true,
      "type": "CreditcardDeposit",
      "vaultData": {
        "property1": "string",
        "property2": "string"
      },
      "vaultIQData": {
        "property1": "string",
        "property2": "string"
      },
      "vaultIQUuid": "string",
      "vaultUuid": "string",
      "visibilityResetAllowed": true,
      "visible": true
    },
    "userPspAccountId": "404200******8008",
    "id": 193027,
    "txTypeInt": 108,
    "state": "SUCCESSFUL"
  }
]
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successfully found transactions|Inline
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for search request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[PaymentResponse](#schemapaymentresponse)]|false|No description
?? accountHolderName|string|false|Account holder name
?? amount|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? amountBase|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? authAmount|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? authAmountBase|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? blockedAccountReason|string|false|Blocked Account Reason
?? bonusCode|string|false|Optional bonus code.
?? channelId|string|false|Optional channel-id provided by merchant
?? created|string(date-time)|false|Date and time when transaction was created
?? depositType|string|false|Deposit Type
?? fee|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? feeBase|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? info|[StringBuilder](#schemastringbuilder)|false|No description
?? initiatedPspAccount|string|false|Provider account used in the transaction
?? initiatedPspId|integer(int32)|false|Representation of provider who initiated the transaction, e.g. Skrill, Neteller or PayPoint
?? ipAddr|string|false|IP Address
?? ipCity|string|false|IP City
?? ipCountry|string|false|IP Country
?? ipRegion|string|false|IP Region
?? issuerCountry|string|false|Optional info for credit cards .. Three letter iso standard
?? kycStatus|string|false|Know Your Customer (KYC) status. Value returned by merchant. Used for checking tx
?? lastUpdated|string(date-time)|false|Last date and time when transaction was updated
?? maskedUserAccount|string|false|User's account masked
?? merchantAuthCode|string|false|Merchant's authorization code from the authorize request
?? merchantErrCode|string|false|Merchant error code, e.g. verify user failed
?? merchantId|integer(int32)|false|Merchant id
?? merchantTxId|string|false|Merchant's tx id.
?? merchantUserBal|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? merchantUserCat|string|false|Merchant's user category
?? merchantUserCountry|string|false|Merchant user country
?? merchantUserEmail|string|false|Merchant user email
?? merchantUserId|string|false|Merchant's user id
?? originTxId|integer(int64)|false|Transaction id that is origin to this transaction
?? pspAccount|string|false|Provider account used in the transaction
?? pspFee|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? pspFeeBase|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? pspFraudScore|number(double)|false|Normalized PSP fraud score (0-10).
?? pspId|integer(int32)|false|Representation of provider who has processed the transaction, e.g. Skrill, Neteller or PayPoint
?? pspRefId|string|false|Provider reference id
?? pspService|string|false|Representation of provider's sub service which will be used to do a payment
?? pspStatusCode|string|false|Provider specific status code
?? pspTxAmount|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? pspUserRef|string|false|PSP User ref 
?? reversedMerchantTxId|string|false|Merchant transaction that have been reversed by this transaction 
?? reversedTxId|integer(int64)|false|Transaction id that have been reversed by this transaction
?? statusCode|string|false|Status code
?? suspectedAbuseReason|string|false|Suspected Abused Reason
?? txAmount|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? txAmountBase|[Money](#schemamoney)|false|No description
???? amount|number|false|No description
???? amountInFractionUnit|integer(int64)|false|No description
???? currency|string|false|No description
???? currencyCode|string|false|No description
???? currencyNumeric3Code|string|false|No description
???? fractionDigits|integer(int32)|false|No description
???? negative|boolean|false|No description
???? positive|boolean|false|No description
???? zero|boolean|false|No description
?? updatedBy|string|false|Optional last user took same action on the transactions
?? userPspAccountDetails|[UserPspAccountDetails](#schemauserpspaccountdetails)|false|No description
???? accountUuid|string|false|No description
???? blockReason|string|false|No description
???? description|string|false|No description
???? directDebit|boolean|false|No description
???? expiryDate|string(date-time)|false|No description
???? extAccountRefId|string|false|No description
???? firstUsed|string(date-time)|false|No description
???? hashedAccount|string|false|No description
???? holder|string|false|No description
???? id|integer(int64)|false|No description
???? lastSuccess|string(date-time)|false|No description
???? lastUsed|string(date-time)|false|No description
???? maskedAccount|string|false|No description
???? merchantId|integer(int32)|false|No description
???? merchantUserId|string|false|No description
???? new|boolean|false|No description
???? noFailedTx|integer(int32)|false|No description
???? noSuccessfulTx|integer(int32)|false|No description
???? providerType|string|false|No description
???? startDate|string(date-time)|false|No description
???? status|string|false|No description
???? storeAccount|boolean|false|No description
???? type|string|false|No description
???? vaultData|object|false|No description
???? vaultIQData|object|false|No description
???? vaultIQUuid|string|false|No description
???? vaultUuid|string|false|No description
???? visibilityResetAllowed|boolean|false|No description
???? visible|boolean|false|No description
?? userPspAccountId|integer(int64)|false|User PSP account unique id, reference to table 'user_psp_account.id
?? id|integer(int64)|false|Unique transaction id
?? txTypeInt|integer(int32)|false|Representation of transaction type, e.g. Skrill deposit, Neteller
?? state|string|false|Transaction state
?? rules|[string]|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

## approve

`POST /admin/v1/payments/approve/{txId}`

*approve*

This method is called to approve a transaction. This will send it on to the payment processor.

> Body parameter

```json
{
  "info": "Approve reason...",
  "tagId": "CP-1"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
txId|path|integer(int64)|true|txId
merchantId|query|string|true|merchantId
body|body|[ApproveRequest](#schemaapproverequest)|false|request
?? info|body|string|false|Any additional information to provide reason for approve. Maximum limit 200 characters.
?? tagId|body|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Approve, an example is <tags><entry><string>Approve</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>


> Example responses

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful approve|[PaymentsResponse](#schemapaymentsresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for refund request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

## doCapture

`POST /admin/v1/payments/capture/{txId}`

*doCapture*

Manually????capture????the????amount????of????an????authorized????transaction.????The
transaction????must????have????the????following????status????code:
SUCCESS_AUTO_CAPTURED????or
SUCCESS_CAPTURED????to????able????to????be????captured

> Body parameter

```json
{
  "info": "Capture reason...",
  "tagId": "CP-1"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
txId|path|integer(int64)|true|txId
merchantId|query|string|true|merchantId
body|body|[CaptureRequest](#schemacapturerequest)|false|request
?? info|body|string|false|Any additional information to provide reason for capture. Maximum limit 200 characters.
?? tagId|body|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Capture, an example is <tags><entry><string>Capture</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>


> Example responses

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful capture|[PaymentsResponse](#schemapaymentsresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for capture request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

## deny

`POST /admin/v1/payments/deny/{txId}`

*deny*

This method is called to deny a transaction.

> Body parameter

```json
{
  "info": "Deny reason...",
  "tagId": "CP-1"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
txId|path|integer(int64)|true|txId
merchantId|query|string|true|merchantId
body|body|[DenyRequest](#schemadenyrequest)|false|request
?? info|body|string|false|Any additional information to provide reason for deny. Maximum limit 200 characters.
?? tagId|body|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Deny, an example is <tags><entry><string>Deny</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>


> Example responses

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful deny|[PaymentsResponse](#schemapaymentsresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for refund request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

## onHold

`POST /admin/v1/payments/onhold/{txId}`

*onHold*

This method is called to set a transaction on hold

> Body parameter

```json
{
  "info": "On Hold reason...",
  "tagId": "CP-1"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
txId|path|integer(int64)|true|txId
merchantId|query|string|true|merchantId
body|body|[OnHoldRequest](#schemaonholdrequest)|false|request
?? info|body|string|false|Any additional information to provide reason for on hold. Maximum limit 200 characters.
?? tagId|body|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named On-Hold, an example is <tags><entry><string>On-Hold</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>


> Example responses

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful onHold|[PaymentsResponse](#schemapaymentsresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for refund request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

## doRefund

`POST /admin/v1/payments/refund/{txId}`

*doRefund*

This????will????attempt????to????refund or partial refund (if txAmount is set)??the??transaction??back??to??the??customer??by
sending????an????instruction????to????the????Payment????provider.????When????you????make????a
refund,????PaymentIQ????does????various????checks????to????ensure????that????the????financial
institution????accepts????refund????instructions????and????that????the????amount????to????be
refunded????is????still????available????for????that????payment.????If????it????is????permitted,????the
refund????request????is????scheduled????and????sent????to????the????appropriate????financial
institution.????Once????a????payment????is????processed,????the????customer????receives????the
refund????amount????requested.

> Body parameter

```json
{
  "info": "Refund reason...",
  "tagId": "CP-1",
  "txAmount": "2.35"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
txId|path|integer(int64)|true|txId
merchantId|query|string|true|merchantId
body|body|[RefundRequest](#schemarefundrequest)|false|request
?? info|body|string|false|Any additional information to provide reason for capture. Maximum limit 200 characters.
?? tagId|body|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Refund, an example is <tags><entry><string>Refund</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>
?? txAmount|body|string|false|The amount to partial refund


> Example responses

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful refund|[PaymentsResponse](#schemapaymentsresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for refund request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

## doVoid

`POST /admin/v1/payments/void/{txId}`

*doVoid*

Credit????card????transactions????can????be????cancelled????(void)????before????they????are
captured.????If????a????payment????is????captured,????the????customer????has????been????charged
and????you????cannot????use????this????process????and????should????consider????making????a????refund
instead.

> Body parameter

```json
{
  "info": "Void reason...",
  "tagId": "CP-1"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
txId|path|integer(int64)|true|txId
merchantId|query|string|true|merchantId
body|body|[VoidRequest](#schemavoidrequest)|false|request
?? info|body|string|false|Any additional information to provide reason for capture. Maximum limit 200 characters.
?? tagId|body|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Void, an example is <tags><entry><string>Void</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>


> Example responses

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
}
```
```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
}
```
```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful void|[PaymentsResponse](#schemapaymentsresponse)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ErrorResponse](#schemaerrorresponse)
401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized authentication|[UnauthorizedResponse](#schemaunauthorizedresponse)
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|User is not permitted to requested operation|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Transaction not found for void request|[ErrorResponse](#schemaerrorresponse)
409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Syntactically correct requests that still cannot be performed|[PaymentsErrorResponse](#schemapaymentserrorresponse)
500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: default )
</aside>

# Schemas

## ApproveRequest

<a name="schemaapproverequest"></a>

```json
{
  "info": "Approve reason...",
  "tagId": "CP-1"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
info|string|false|Any additional information to provide reason for approve. Maximum limit 200 characters.
tagId|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Approve, an example is <tags><entry><string>Approve</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>



## CaptureRequest

<a name="schemacapturerequest"></a>

```json
{
  "info": "Capture reason...",
  "tagId": "CP-1"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
info|string|false|Any additional information to provide reason for capture. Maximum limit 200 characters.
tagId|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Capture, an example is <tags><entry><string>Capture</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>



## DenyRequest

<a name="schemadenyrequest"></a>

```json
{
  "info": "Deny reason...",
  "tagId": "CP-1"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
info|string|false|Any additional information to provide reason for deny. Maximum limit 200 characters.
tagId|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Deny, an example is <tags><entry><string>Deny</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>



## ErrorResponse

<a name="schemaerrorresponse"></a>

```json
{
  "errorId": "657b10da-d2f9-4088-a948-bf190ef516b1-000002fd",
  "errorMessage": "Details about the specified error..."
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
errorId|string|false|Unique reference, for debugging purposes, of this error response
errorMessage|string|false|Provides details description about the error.



## Money

<a name="schemamoney"></a>

```json
{
  "amount": 0,
  "amountInFractionUnit": 0,
  "currency": "string",
  "currencyCode": "string",
  "currencyNumeric3Code": "string",
  "fractionDigits": 0,
  "negative": true,
  "positive": true,
  "zero": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
amount|number|false|No description
amountInFractionUnit|integer(int64)|false|No description
currency|string|false|No description
currencyCode|string|false|No description
currencyNumeric3Code|string|false|No description
fractionDigits|integer(int32)|false|No description
negative|boolean|false|No description
positive|boolean|false|No description
zero|boolean|false|No description



## OnHoldRequest

<a name="schemaonholdrequest"></a>

```json
{
  "info": "On Hold reason...",
  "tagId": "CP-1"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
info|string|false|Any additional information to provide reason for on hold. Maximum limit 200 characters.
tagId|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named On-Hold, an example is <tags><entry><string>On-Hold</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>



## PaymentResponse

<a name="schemapaymentresponse"></a>

```json
{
  "accountHolderName": "test test",
  "amount": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "amountBase": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "authAmount": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "authAmountBase": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "blockedAccountReason": "250EAO",
  "bonusCode": "1111",
  "channelId": "12345",
  "created": "2017-04-27 14:10:38",
  "depositType": "Standard",
  "fee": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "feeBase": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "info": {},
  "initiatedPspAccount": "3DS",
  "initiatedPspId": 108,
  "ipAddr": "141.8.92.216",
  "ipCity": "Msida",
  "ipCountry": "MLT",
  "ipRegion": "string",
  "issuerCountry": "ZZZ",
  "kycStatus": "Accept",
  "lastUpdated": "2017-04-27 14:10:40",
  "maskedUserAccount": "23232*****232",
  "merchantAuthCode": "cc3056ec-735c-4ef6-8126-0b0d94b96b49",
  "merchantErrCode": "1001",
  "merchantId": 1980,
  "merchantTxId": "c15eef34-1f37-43a4-a19b-473dbef541ed",
  "merchantUserBal": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "merchantUserCat": "TEST",
  "merchantUserCountry": "AUS",
  "merchantUserEmail": "test@example.com",
  "merchantUserId": "TEST_USER",
  "originTxId": 193027,
  "pspAccount": "3DS",
  "pspFee": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "pspFeeBase": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "pspFraudScore": 0.02,
  "pspId": 108,
  "pspRefId": "C873789149330223994317",
  "pspService": "250EAO",
  "pspStatusCode": "PENDING",
  "pspTxAmount": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "pspUserRef": "1111",
  "reversedMerchantTxId": "250EAO",
  "reversedTxId": 1000,
  "rules": [
    "string"
  ],
  "statusCode": "SUCCESS",
  "suspectedAbuseReason": "250EAO",
  "txAmount": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "txAmountBase": {
    "amount": 0,
    "amountInFractionUnit": 0,
    "currency": "string",
    "currencyCode": "string",
    "currencyNumeric3Code": "string",
    "fractionDigits": 0,
    "negative": true,
    "positive": true,
    "zero": true
  },
  "updatedBy": "user1",
  "userPspAccountDetails": {
    "accountUuid": "string",
    "blockReason": "string",
    "description": "string",
    "directDebit": true,
    "expiryDate": "2017-11-06T10:24:37Z",
    "extAccountRefId": "string",
    "firstUsed": "2017-11-06T10:24:37Z",
    "hashedAccount": "string",
    "holder": "string",
    "id": 0,
    "lastSuccess": "2017-11-06T10:24:37Z",
    "lastUsed": "2017-11-06T10:24:37Z",
    "maskedAccount": "string",
    "merchantId": 0,
    "merchantUserId": "string",
    "new": true,
    "noFailedTx": 0,
    "noSuccessfulTx": 0,
    "providerType": "string",
    "startDate": "2017-11-06T10:24:37Z",
    "status": "ACTIVE",
    "storeAccount": true,
    "type": "CreditcardDeposit",
    "vaultData": {
      "property1": "string",
      "property2": "string"
    },
    "vaultIQData": {
      "property1": "string",
      "property2": "string"
    },
    "vaultIQUuid": "string",
    "vaultUuid": "string",
    "visibilityResetAllowed": true,
    "visible": true
  },
  "userPspAccountId": "404200******8008",
  "id": 193027,
  "txTypeInt": 108,
  "state": "SUCCESSFUL"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
accountHolderName|string|false|Account holder name
amount|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
amountBase|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
authAmount|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
authAmountBase|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
blockedAccountReason|string|false|Blocked Account Reason
bonusCode|string|false|Optional bonus code.
channelId|string|false|Optional channel-id provided by merchant
created|string(date-time)|false|Date and time when transaction was created
depositType|string|false|Deposit Type
fee|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
feeBase|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
info|[StringBuilder](#schemastringbuilder)|false|No description
initiatedPspAccount|string|false|Provider account used in the transaction
initiatedPspId|integer(int32)|false|Representation of provider who initiated the transaction, e.g. Skrill, Neteller or PayPoint
ipAddr|string|false|IP Address
ipCity|string|false|IP City
ipCountry|string|false|IP Country
ipRegion|string|false|IP Region
issuerCountry|string|false|Optional info for credit cards .. Three letter iso standard
kycStatus|string|false|Know Your Customer (KYC) status. Value returned by merchant. Used for checking tx
lastUpdated|string(date-time)|false|Last date and time when transaction was updated
maskedUserAccount|string|false|User's account masked
merchantAuthCode|string|false|Merchant's authorization code from the authorize request
merchantErrCode|string|false|Merchant error code, e.g. verify user failed
merchantId|integer(int32)|false|Merchant id
merchantTxId|string|false|Merchant's tx id.
merchantUserBal|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
merchantUserCat|string|false|Merchant's user category
merchantUserCountry|string|false|Merchant user country
merchantUserEmail|string|false|Merchant user email
merchantUserId|string|false|Merchant's user id
originTxId|integer(int64)|false|Transaction id that is origin to this transaction
pspAccount|string|false|Provider account used in the transaction
pspFee|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
pspFeeBase|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
pspFraudScore|number(double)|false|Normalized PSP fraud score (0-10).
pspId|integer(int32)|false|Representation of provider who has processed the transaction, e.g. Skrill, Neteller or PayPoint
pspRefId|string|false|Provider reference id
pspService|string|false|Representation of provider's sub service which will be used to do a payment
pspStatusCode|string|false|Provider specific status code
pspTxAmount|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
pspUserRef|string|false|PSP User ref 
reversedMerchantTxId|string|false|Merchant transaction that have been reversed by this transaction 
reversedTxId|integer(int64)|false|Transaction id that have been reversed by this transaction
statusCode|string|false|Status code
suspectedAbuseReason|string|false|Suspected Abused Reason
txAmount|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
txAmountBase|[Money](#schemamoney)|false|No description
?? amount|number|false|No description
?? amountInFractionUnit|integer(int64)|false|No description
?? currency|string|false|No description
?? currencyCode|string|false|No description
?? currencyNumeric3Code|string|false|No description
?? fractionDigits|integer(int32)|false|No description
?? negative|boolean|false|No description
?? positive|boolean|false|No description
?? zero|boolean|false|No description
updatedBy|string|false|Optional last user took same action on the transactions
userPspAccountDetails|[UserPspAccountDetails](#schemauserpspaccountdetails)|false|No description
?? accountUuid|string|false|No description
?? blockReason|string|false|No description
?? description|string|false|No description
?? directDebit|boolean|false|No description
?? expiryDate|string(date-time)|false|No description
?? extAccountRefId|string|false|No description
?? firstUsed|string(date-time)|false|No description
?? hashedAccount|string|false|No description
?? holder|string|false|No description
?? id|integer(int64)|false|No description
?? lastSuccess|string(date-time)|false|No description
?? lastUsed|string(date-time)|false|No description
?? maskedAccount|string|false|No description
?? merchantId|integer(int32)|false|No description
?? merchantUserId|string|false|No description
?? new|boolean|false|No description
?? noFailedTx|integer(int32)|false|No description
?? noSuccessfulTx|integer(int32)|false|No description
?? providerType|string|false|No description
?? startDate|string(date-time)|false|No description
?? status|string|false|No description
?? storeAccount|boolean|false|No description
?? type|string|false|No description
?? vaultData|object|false|No description
?? vaultIQData|object|false|No description
?? vaultIQUuid|string|false|No description
?? vaultUuid|string|false|No description
?? visibilityResetAllowed|boolean|false|No description
?? visible|boolean|false|No description
userPspAccountId|integer(int64)|false|User PSP account unique id, reference to table 'user_psp_account.id
id|integer(int64)|false|Unique transaction id
txTypeInt|integer(int32)|false|Representation of transaction type, e.g. Skrill deposit, Neteller
state|string|false|Transaction state
rules|[string]|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
statusCode|SUCCESS|
statusCode|SUCCESS_WITHDRAWAL_APPROVAL|
statusCode|SUCCESS_WITHDRAWAL_AUTO_APPROVAL|
statusCode|SUCCESS_WAITING_CAPTURE|
statusCode|SUCCESS_WAITING_AUTO_CAPTURE|
statusCode|SUCCESS_AUTO_CAPTURED|
statusCode|SUCCESS_CAPTURED|
statusCode|REGISTERED|
statusCode|PROCESSING_PROVIDER|
statusCode|PROCESSING_MERCHANT|
statusCode|CONT_WITH_N3DS|
statusCode|REPROCESSING_PROVIDER|
statusCode|REPROCESSING_MERCHANT|
statusCode|WAITING_INPUT|
statusCode|WAITING_3D_SECURE|
statusCode|WAITING_DEPOSIT_CONFIRMATION|
statusCode|WAITING_NOTIFICATION|
statusCode|WAITING_DEPOSIT_APPROVAL|
statusCode|WAITING_WITHDRAWAL_APPROVAL|
statusCode|WAITING_DEPOSIT_AUTO_APPROVAL|
statusCode|WAITING_WITHDRAWAL_AUTO_APPROVAL|
statusCode|WAITING_DEPOSIT_ON_HOLD_APPROVAL|
statusCode|WAITING_WITHDRAWAL_ON_HOLD_APPROVAL|
statusCode|ERR_READ_TIMEOUT|
statusCode|ERR_REFERENCE_MISMATCH|
statusCode|ERR_INCONSISTENT_TRANSACTION|
statusCode|ERR_UNKNOWN_CALLBACK|
statusCode|ERR_IO_EXCEPTION|
statusCode|ERR_UNKNOWN_RESPONSE|
statusCode|ERR_SYSTEM_ERROR|
statusCode|ERR_FAILED_TO_CONNECT|
statusCode|ERR_DECLINED_BAD_REQUEST|
statusCode|ERR_DECLINED_FRAUD|
statusCode|ERR_DECLINED_NO_FUNDS|
statusCode|ERR_DECLINED_ACCOUNT_SUSPENDED|
statusCode|ERR_DECLINED_OTHER_REASON|
statusCode|ERR_DECLINED_CONTACT_SUPPORT|
statusCode|ERR_DECLINED_CONFIG_ERROR|
statusCode|ERR_NOT_AUTHENTICATED|
statusCode|ERR_INVALID_RESPONSE|
statusCode|ERR_DECLINED_REQ_BLOCKED|
statusCode|ERR_PSP_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_NOT_AUTHORIZED|
statusCode|ERR_RESPONSE_CODE_UNKNOWN|
statusCode|ERR_PSP_ACCOUNT_USED_BY_OTHER_USER|
statusCode|ERR_PSP_ACCOUNT_NOT_USED|
statusCode|ERR_TOO_MANY_PSP_ACCOUNTS|
statusCode|ERR_DECLINED_DUPLICATE_TX_ID|
statusCode|ERR_DECLINED_INVALID_ACCOUNT_NUMBER|
statusCode|ERR_MERCHANT_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_LIMIT_OVERDRAWN|
statusCode|ERR_MERCHANT_RESPONSE_CODE_UNKNOWN|
statusCode|ERR_DECLINED_NO_PROVIDER_FOUND|
statusCode|ERR_DECLINED_PROVIDER_ACCOUNT_CONFIG_ERROR|
statusCode|ERR_MERCHANT_INVALID_RESPONSE|
statusCode|ERR_DECLINED_3D_VALIDATION_FAILED|
statusCode|ERR_DECLINED_3D_EXPIRED|
statusCode|ERR_VAULTIQ_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_IP_BLOCKED|
statusCode|ERR_DECLINED_BIN_BLOCKED|
statusCode|ERR_VAULTIQ_UNKNOWN_ACCOUNT|
statusCode|ERR_DECLINED_KYC_BLOCK|
statusCode|ERR_DECLINED_KYC_USER_UNDER_AGE|
statusCode|ERR_DECLINED_KYC_CHECK_FAILED|
statusCode|ERR_DECLINED_BIC_BLOCK|
statusCode|ERR_DECLINED_EXPIRED|
statusCode|ERR_DECLINED_REPEAT_CANCELLED|
statusCode|ERR_DECLINED_CURRENCY_NOT_SUPPORTED|
statusCode|ERR_DECLINED_FRAUD_SCORE_THRESHOLD_EXCEEDED|
statusCode|ERR_DECLINED_MERCHANT_NOT_FOUND|
statusCode|ERR_DECLINED_MERCHANT_NOT_ENABLED|
statusCode|ERR_DECLINED_PROVIDER_NOT_ENABLED|
statusCode|ERR_DECLINED_UNDER_MAINTENANCE|
statusCode|ERR_NO_REFERRAL_TX_FOUND|
statusCode|ERR_DECLINE_TX_NOT_FOUND|
statusCode|ERR_DECLINE_COUNTRY_NOT_SUPPORTED|
statusCode|ERR_DECLINED_NOT_SUPPORTED_PAYMENT_METHOD_FRAUD|
statusCode|ERR_DECLINED_FRAUD_PROVIDER_ACCOUNT_CONFIG_ERROR|
statusCode|ERR_CANCELLED_BY_USER|
statusCode|ERR_CANCELLED_BY_MERCHANT|
statusCode|ERR_CANCELLED_BY_PSP|
?? status|ACTIVE|
?? status|INACTIVE|
?? status|NEW|
?? status|DELETED|
?? status|BLOCKED|
?? type|CreditcardDeposit|
?? type|CreditcardWithdrawal|
?? type|EntropayDeposit|
?? type|ICardDeposit|
?? type|ICardWithdrawal|
?? type|NetellerDeposit|
?? type|NetellerWithdrawal|
?? type|SkrillDeposit|
?? type|SkrillWithdrawal|
?? type|PayboxDeposit|
?? type|ClickandBuyDeposit|
?? type|ClickandBuyWithdrawal|
?? type|PayPalDeposit|
?? type|PayPalWithdrawal|
?? type|MbankomatDeposit|
?? type|IBanqDeposit|
?? type|IBanqWithdrawal|
?? type|LavaPayDeposit|
?? type|LavaPayWithdrawal|
?? type|InstadebitDeposit|
?? type|InstadebitWithdrawal|
?? type|IDebitDeposit|
?? type|IDebitWithdrawal|
?? type|EcoPayzDeposit|
?? type|EcoPayzWithdrawal|
?? type|AstroPayCardWithdrawal|
?? type|AstroPayDirectDeposit|
?? type|AstroPayDirectWithdrawal|
?? type|VenusPointDeposit|
?? type|VenusPointWithdrawal|
?? type|MiFinityEWalletDeposit|
?? type|MiFinityEWalletWithdrawal|
?? type|IWalletDeposit|
?? type|IWalletWithdrawal|
?? type|MuchBetterDeposit|
?? type|MuchBetterWithdrawal|
?? type|AstroPayBankWithdrawal|
?? type|EutellerDeposit|
?? type|EnvoyDeposit|
?? type|EnvoyWithdrawal|
?? type|TrustlyDeposit|
?? type|TrustlyWithdrawal|
?? type|BankDeposit|
?? type|BankLocalWithdrawal|
?? type|BankIBANWithdrawal|
?? type|BankIntIBANWithdrawal|
?? type|IdealDeposit|
?? type|ChinaUnionPayDeposit|
?? type|BankIntlWithdrawal|
?? type|ChinaUnionPayWithdrawal|
?? type|BoletoBancarioDeposit|
?? type|PaysafecardDeposit|
?? type|UkashDeposit|
?? type|UkashWithdrawal|
?? type|PaysafecardWithdrawal|
?? type|CashlibDeposit|
?? type|TicketPremiumDeposit|
?? type|FlexepinDeposit|
?? type|FunangaDeposit|
?? type|VisaVoucherDeposit|
?? type|GiftcardDeposit|
?? type|PugglePayDeposit|
?? type|PaylevoDeposit|
?? type|YuuCollectDeposit|
?? type|NeosurfVoucherDeposit|
?? type|OxxoDeposit|
?? type|SeqrDeposit|
?? type|CryptoCurrencyDeposit|
?? type|SeqrWithdrawal|
?? type|SiruDeposit|
?? type|SiruStatus|
?? type|SiruPriceCalc|
?? type|FortumoDeposit|
?? type|BokuDeposit|
?? type|BlikDeposit|
?? type|PayGroundDeposit|
?? type|SmsVoucherDeposit|
?? type|QiwiDeposit|
?? type|QiwiWithdrawal|
?? type|AccentPayDeposit|
?? type|AccentPayWithdrawal|
?? type|WorldPayDeposit|
?? type|WorldPayWithdrawal|
?? type|PProDeposit|
?? type|PProWithdrawal|
?? type|EProPaymentWallDeposit|
?? type|ApcoDeposit|
?? type|SecureTradingDeposit|
?? type|DotpayDeposit|
?? type|Przelewy24Deposit|
?? type|SweGiroDeposit|
?? type|ToditoCashDeposit|
?? type|TolaMobileDeposit|
?? type|KluwpDeposit|
?? type|TeleingresoDeposit|
?? type|ManualChargeback|
?? type|ManualRefund|
?? type|ManualCancel|
?? type|ManualVoid|
?? type|ManualChargeBackWon|
?? type|Refund|
?? type|Cancel|
?? type|Void|
?? type|Capture|
state|SUCCESSFUL|
state|REGISTERED|
state|PROCESSING|
state|WAITING_INPUT|
state|WAITING_APPROVAL|
state|FAILED|
state|INCONSISTENT|
state|CANCELLED|
state|REPROCESSING|


## PaymentsErrorResponse

<a name="schemapaymentserrorresponse"></a>

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "ERR_SYSTEM_ERROR",
  "pspStatusCode": "0_00",
  "state": "FAILED",
  "errorMessage": "Invalid transaction state, found current transaction status: FAILED. Expected transaction state to be SUCCESSFUL.",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|Transaction id
merchantId|integer(int32)|false|Merchant id
statusCode|string|false|Generic status codes, common for all providers. The property PSP status code contains   * the provider specific code. 
pspStatusCode|string|false|Psp status code
state|string|false|Payment transaction states
errorMessage|string|false|Error message that describes what went wrong
created|string(date-time)|false|Timestamp for created
lastUpdated|string(date-time)|false|Timestamp for updated


#### Enumerated Values

|Property|Value|
|---|---|
statusCode|SUCCESS|
statusCode|SUCCESS_WITHDRAWAL_APPROVAL|
statusCode|SUCCESS_WITHDRAWAL_AUTO_APPROVAL|
statusCode|SUCCESS_WAITING_CAPTURE|
statusCode|SUCCESS_WAITING_AUTO_CAPTURE|
statusCode|SUCCESS_AUTO_CAPTURED|
statusCode|SUCCESS_CAPTURED|
statusCode|REGISTERED|
statusCode|PROCESSING_PROVIDER|
statusCode|PROCESSING_MERCHANT|
statusCode|CONT_WITH_N3DS|
statusCode|REPROCESSING_PROVIDER|
statusCode|REPROCESSING_MERCHANT|
statusCode|WAITING_INPUT|
statusCode|WAITING_3D_SECURE|
statusCode|WAITING_DEPOSIT_CONFIRMATION|
statusCode|WAITING_NOTIFICATION|
statusCode|WAITING_DEPOSIT_APPROVAL|
statusCode|WAITING_WITHDRAWAL_APPROVAL|
statusCode|WAITING_DEPOSIT_AUTO_APPROVAL|
statusCode|WAITING_WITHDRAWAL_AUTO_APPROVAL|
statusCode|WAITING_DEPOSIT_ON_HOLD_APPROVAL|
statusCode|WAITING_WITHDRAWAL_ON_HOLD_APPROVAL|
statusCode|ERR_READ_TIMEOUT|
statusCode|ERR_REFERENCE_MISMATCH|
statusCode|ERR_INCONSISTENT_TRANSACTION|
statusCode|ERR_UNKNOWN_CALLBACK|
statusCode|ERR_IO_EXCEPTION|
statusCode|ERR_UNKNOWN_RESPONSE|
statusCode|ERR_SYSTEM_ERROR|
statusCode|ERR_FAILED_TO_CONNECT|
statusCode|ERR_DECLINED_BAD_REQUEST|
statusCode|ERR_DECLINED_FRAUD|
statusCode|ERR_DECLINED_NO_FUNDS|
statusCode|ERR_DECLINED_ACCOUNT_SUSPENDED|
statusCode|ERR_DECLINED_OTHER_REASON|
statusCode|ERR_DECLINED_CONTACT_SUPPORT|
statusCode|ERR_DECLINED_CONFIG_ERROR|
statusCode|ERR_NOT_AUTHENTICATED|
statusCode|ERR_INVALID_RESPONSE|
statusCode|ERR_DECLINED_REQ_BLOCKED|
statusCode|ERR_PSP_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_NOT_AUTHORIZED|
statusCode|ERR_RESPONSE_CODE_UNKNOWN|
statusCode|ERR_PSP_ACCOUNT_USED_BY_OTHER_USER|
statusCode|ERR_PSP_ACCOUNT_NOT_USED|
statusCode|ERR_TOO_MANY_PSP_ACCOUNTS|
statusCode|ERR_DECLINED_DUPLICATE_TX_ID|
statusCode|ERR_DECLINED_INVALID_ACCOUNT_NUMBER|
statusCode|ERR_MERCHANT_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_LIMIT_OVERDRAWN|
statusCode|ERR_MERCHANT_RESPONSE_CODE_UNKNOWN|
statusCode|ERR_DECLINED_NO_PROVIDER_FOUND|
statusCode|ERR_DECLINED_PROVIDER_ACCOUNT_CONFIG_ERROR|
statusCode|ERR_MERCHANT_INVALID_RESPONSE|
statusCode|ERR_DECLINED_3D_VALIDATION_FAILED|
statusCode|ERR_DECLINED_3D_EXPIRED|
statusCode|ERR_VAULTIQ_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_IP_BLOCKED|
statusCode|ERR_DECLINED_BIN_BLOCKED|
statusCode|ERR_VAULTIQ_UNKNOWN_ACCOUNT|
statusCode|ERR_DECLINED_KYC_BLOCK|
statusCode|ERR_DECLINED_KYC_USER_UNDER_AGE|
statusCode|ERR_DECLINED_KYC_CHECK_FAILED|
statusCode|ERR_DECLINED_BIC_BLOCK|
statusCode|ERR_DECLINED_EXPIRED|
statusCode|ERR_DECLINED_REPEAT_CANCELLED|
statusCode|ERR_DECLINED_CURRENCY_NOT_SUPPORTED|
statusCode|ERR_DECLINED_FRAUD_SCORE_THRESHOLD_EXCEEDED|
statusCode|ERR_DECLINED_MERCHANT_NOT_FOUND|
statusCode|ERR_DECLINED_MERCHANT_NOT_ENABLED|
statusCode|ERR_DECLINED_PROVIDER_NOT_ENABLED|
statusCode|ERR_DECLINED_UNDER_MAINTENANCE|
statusCode|ERR_NO_REFERRAL_TX_FOUND|
statusCode|ERR_DECLINE_TX_NOT_FOUND|
statusCode|ERR_DECLINE_COUNTRY_NOT_SUPPORTED|
statusCode|ERR_DECLINED_NOT_SUPPORTED_PAYMENT_METHOD_FRAUD|
statusCode|ERR_DECLINED_FRAUD_PROVIDER_ACCOUNT_CONFIG_ERROR|
statusCode|ERR_CANCELLED_BY_USER|
statusCode|ERR_CANCELLED_BY_MERCHANT|
statusCode|ERR_CANCELLED_BY_PSP|
state|SUCCESSFUL|
state|REGISTERED|
state|PROCESSING|
state|WAITING_INPUT|
state|WAITING_APPROVAL|
state|FAILED|
state|INCONSISTENT|
state|CANCELLED|
state|REPROCESSING|


## PaymentsResponse

<a name="schemapaymentsresponse"></a>

```json
{
  "id": 256616,
  "merchantId": 100000000,
  "statusCode": "SUCCESS",
  "pspStatusCode": "0_00",
  "state": "SUCCESSFUL",
  "created": "2017-09-15 00:00:00",
  "lastUpdated": "2017-09-16 00:00:00"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|Transaction id
merchantId|integer(int32)|false|Merchant id
statusCode|string|false|Generic status codes, common for all providers. The property PSP status code contains   * the provider specific code. 
pspStatusCode|string|false|Psp status code
state|string|false|Payment transaction states
created|string(date-time)|false|Timestamp for created
lastUpdated|string(date-time)|false|Timestamp for updated


#### Enumerated Values

|Property|Value|
|---|---|
statusCode|SUCCESS|
statusCode|SUCCESS_WITHDRAWAL_APPROVAL|
statusCode|SUCCESS_WITHDRAWAL_AUTO_APPROVAL|
statusCode|SUCCESS_WAITING_CAPTURE|
statusCode|SUCCESS_WAITING_AUTO_CAPTURE|
statusCode|SUCCESS_AUTO_CAPTURED|
statusCode|SUCCESS_CAPTURED|
statusCode|REGISTERED|
statusCode|PROCESSING_PROVIDER|
statusCode|PROCESSING_MERCHANT|
statusCode|CONT_WITH_N3DS|
statusCode|REPROCESSING_PROVIDER|
statusCode|REPROCESSING_MERCHANT|
statusCode|WAITING_INPUT|
statusCode|WAITING_3D_SECURE|
statusCode|WAITING_DEPOSIT_CONFIRMATION|
statusCode|WAITING_NOTIFICATION|
statusCode|WAITING_DEPOSIT_APPROVAL|
statusCode|WAITING_WITHDRAWAL_APPROVAL|
statusCode|WAITING_DEPOSIT_AUTO_APPROVAL|
statusCode|WAITING_WITHDRAWAL_AUTO_APPROVAL|
statusCode|WAITING_DEPOSIT_ON_HOLD_APPROVAL|
statusCode|WAITING_WITHDRAWAL_ON_HOLD_APPROVAL|
statusCode|ERR_READ_TIMEOUT|
statusCode|ERR_REFERENCE_MISMATCH|
statusCode|ERR_INCONSISTENT_TRANSACTION|
statusCode|ERR_UNKNOWN_CALLBACK|
statusCode|ERR_IO_EXCEPTION|
statusCode|ERR_UNKNOWN_RESPONSE|
statusCode|ERR_SYSTEM_ERROR|
statusCode|ERR_FAILED_TO_CONNECT|
statusCode|ERR_DECLINED_BAD_REQUEST|
statusCode|ERR_DECLINED_FRAUD|
statusCode|ERR_DECLINED_NO_FUNDS|
statusCode|ERR_DECLINED_ACCOUNT_SUSPENDED|
statusCode|ERR_DECLINED_OTHER_REASON|
statusCode|ERR_DECLINED_CONTACT_SUPPORT|
statusCode|ERR_DECLINED_CONFIG_ERROR|
statusCode|ERR_NOT_AUTHENTICATED|
statusCode|ERR_INVALID_RESPONSE|
statusCode|ERR_DECLINED_REQ_BLOCKED|
statusCode|ERR_PSP_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_NOT_AUTHORIZED|
statusCode|ERR_RESPONSE_CODE_UNKNOWN|
statusCode|ERR_PSP_ACCOUNT_USED_BY_OTHER_USER|
statusCode|ERR_PSP_ACCOUNT_NOT_USED|
statusCode|ERR_TOO_MANY_PSP_ACCOUNTS|
statusCode|ERR_DECLINED_DUPLICATE_TX_ID|
statusCode|ERR_DECLINED_INVALID_ACCOUNT_NUMBER|
statusCode|ERR_MERCHANT_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_LIMIT_OVERDRAWN|
statusCode|ERR_MERCHANT_RESPONSE_CODE_UNKNOWN|
statusCode|ERR_DECLINED_NO_PROVIDER_FOUND|
statusCode|ERR_DECLINED_PROVIDER_ACCOUNT_CONFIG_ERROR|
statusCode|ERR_MERCHANT_INVALID_RESPONSE|
statusCode|ERR_DECLINED_3D_VALIDATION_FAILED|
statusCode|ERR_DECLINED_3D_EXPIRED|
statusCode|ERR_VAULTIQ_OUT_OF_SERVICE|
statusCode|ERR_DECLINED_IP_BLOCKED|
statusCode|ERR_DECLINED_BIN_BLOCKED|
statusCode|ERR_VAULTIQ_UNKNOWN_ACCOUNT|
statusCode|ERR_DECLINED_KYC_BLOCK|
statusCode|ERR_DECLINED_KYC_USER_UNDER_AGE|
statusCode|ERR_DECLINED_KYC_CHECK_FAILED|
statusCode|ERR_DECLINED_BIC_BLOCK|
statusCode|ERR_DECLINED_EXPIRED|
statusCode|ERR_DECLINED_REPEAT_CANCELLED|
statusCode|ERR_DECLINED_CURRENCY_NOT_SUPPORTED|
statusCode|ERR_DECLINED_FRAUD_SCORE_THRESHOLD_EXCEEDED|
statusCode|ERR_DECLINED_MERCHANT_NOT_FOUND|
statusCode|ERR_DECLINED_MERCHANT_NOT_ENABLED|
statusCode|ERR_DECLINED_PROVIDER_NOT_ENABLED|
statusCode|ERR_DECLINED_UNDER_MAINTENANCE|
statusCode|ERR_NO_REFERRAL_TX_FOUND|
statusCode|ERR_DECLINE_TX_NOT_FOUND|
statusCode|ERR_DECLINE_COUNTRY_NOT_SUPPORTED|
statusCode|ERR_DECLINED_NOT_SUPPORTED_PAYMENT_METHOD_FRAUD|
statusCode|ERR_DECLINED_FRAUD_PROVIDER_ACCOUNT_CONFIG_ERROR|
statusCode|ERR_CANCELLED_BY_USER|
statusCode|ERR_CANCELLED_BY_MERCHANT|
statusCode|ERR_CANCELLED_BY_PSP|
state|SUCCESSFUL|
state|REGISTERED|
state|PROCESSING|
state|WAITING_INPUT|
state|WAITING_APPROVAL|
state|FAILED|
state|INCONSISTENT|
state|CANCELLED|
state|REPROCESSING|


## RefundRequest

<a name="schemarefundrequest"></a>

```json
{
  "info": "Refund reason...",
  "tagId": "CP-1",
  "txAmount": "2.35"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
info|string|false|Any additional information to provide reason for capture. Maximum limit 200 characters.
tagId|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Refund, an example is <tags><entry><string>Refund</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>
txAmount|string|false|The amount to partial refund



## StringBuilder

<a name="schemastringbuilder"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
undefined|object|false|No description



## UnauthorizedResponse

<a name="schemaunauthorizedresponse"></a>

```json
{
  "error": "invalid_token",
  "error_description": "Cannot convert access token to JSON"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
error|string|false|Provides what type of error it is.
error_description|string|false|Provides details description about the error.



## UserAccountResponse

<a name="schemauseraccountresponse"></a>

```json
{
  "id": 1,
  "merchantId": 1234,
  "accountUuid": "958acd6b-b386-4a2c-bead-e3ed49613d44",
  "merchantUserId": "ENVOY",
  "holder": "testuser",
  "type": "CreditcardDeposit",
  "providerType": "CREDITCARD",
  "hashedAccount": "958acd6b-b386-4a2c-bead-e3ed49613d44",
  "maskedAccount": "4444********1234",
  "startDate": "2020-01-01 00:00:00",
  "expiryDate": "2020-01-01 00:00:00",
  "firstUsed": "2020-01-01 00:00:00",
  "lastUsed": "2020-01-01 00:00:00",
  "lastSuccess": "2020-01-01 00:00:00",
  "noSuccessfulTx": 20,
  "noFailedTx": 10,
  "description": "string",
  "status": "ACTIVE"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer(int64)|false|User account id
merchantId|integer(int32)|false|Merchant id
accountUuid|string|false|Account UUID
merchantUserId|string|false|Merchant user id
holder|string|false|Card holder
type|string|false|Transaction type
providerType|string|false|Provider type
hashedAccount|string|false|Hashed account
maskedAccount|string|false|Masked account
startDate|string(date-time)|false|Date when account can first be used (if applicable)
expiryDate|string(date-time)|false|Date when account will expiry (if applicable)
firstUsed|string(date-time)|false|When account was first used
lastUsed|string(date-time)|false|When account was last used
lastSuccess|string(date-time)|false|When account had last successful tx
noSuccessfulTx|integer(int32)|false|No of successful transactions
noFailedTx|integer(int32)|false|No of failed transactions
description|string|false|Description for the use of psp account
status|string|false|User account status


#### Enumerated Values

|Property|Value|
|---|---|
type|CreditcardDeposit|
type|CreditcardWithdrawal|
type|EntropayDeposit|
type|ICardDeposit|
type|ICardWithdrawal|
type|NetellerDeposit|
type|NetellerWithdrawal|
type|SkrillDeposit|
type|SkrillWithdrawal|
type|PayboxDeposit|
type|ClickandBuyDeposit|
type|ClickandBuyWithdrawal|
type|PayPalDeposit|
type|PayPalWithdrawal|
type|MbankomatDeposit|
type|IBanqDeposit|
type|IBanqWithdrawal|
type|LavaPayDeposit|
type|LavaPayWithdrawal|
type|InstadebitDeposit|
type|InstadebitWithdrawal|
type|IDebitDeposit|
type|IDebitWithdrawal|
type|EcoPayzDeposit|
type|EcoPayzWithdrawal|
type|AstroPayCardWithdrawal|
type|AstroPayDirectDeposit|
type|AstroPayDirectWithdrawal|
type|VenusPointDeposit|
type|VenusPointWithdrawal|
type|MiFinityEWalletDeposit|
type|MiFinityEWalletWithdrawal|
type|IWalletDeposit|
type|IWalletWithdrawal|
type|MuchBetterDeposit|
type|MuchBetterWithdrawal|
type|AstroPayBankWithdrawal|
type|EutellerDeposit|
type|EnvoyDeposit|
type|EnvoyWithdrawal|
type|TrustlyDeposit|
type|TrustlyWithdrawal|
type|BankDeposit|
type|BankLocalWithdrawal|
type|BankIBANWithdrawal|
type|BankIntIBANWithdrawal|
type|IdealDeposit|
type|ChinaUnionPayDeposit|
type|BankIntlWithdrawal|
type|ChinaUnionPayWithdrawal|
type|BoletoBancarioDeposit|
type|PaysafecardDeposit|
type|UkashDeposit|
type|UkashWithdrawal|
type|PaysafecardWithdrawal|
type|CashlibDeposit|
type|TicketPremiumDeposit|
type|FlexepinDeposit|
type|FunangaDeposit|
type|VisaVoucherDeposit|
type|GiftcardDeposit|
type|PugglePayDeposit|
type|PaylevoDeposit|
type|YuuCollectDeposit|
type|NeosurfVoucherDeposit|
type|OxxoDeposit|
type|SeqrDeposit|
type|CryptoCurrencyDeposit|
type|SeqrWithdrawal|
type|SiruDeposit|
type|SiruStatus|
type|SiruPriceCalc|
type|FortumoDeposit|
type|BokuDeposit|
type|BlikDeposit|
type|PayGroundDeposit|
type|SmsVoucherDeposit|
type|QiwiDeposit|
type|QiwiWithdrawal|
type|AccentPayDeposit|
type|AccentPayWithdrawal|
type|WorldPayDeposit|
type|WorldPayWithdrawal|
type|PProDeposit|
type|PProWithdrawal|
type|EProPaymentWallDeposit|
type|ApcoDeposit|
type|SecureTradingDeposit|
type|DotpayDeposit|
type|Przelewy24Deposit|
type|SweGiroDeposit|
type|ToditoCashDeposit|
type|TolaMobileDeposit|
type|KluwpDeposit|
type|TeleingresoDeposit|
type|ManualChargeback|
type|ManualRefund|
type|ManualCancel|
type|ManualVoid|
type|ManualChargeBackWon|
type|Refund|
type|Cancel|
type|Void|
type|Capture|
providerType|ACCENTPAY|
providerType|BANK|
providerType|BANKIBAN|
providerType|BANKINTIBAN|
providerType|BANKINTL|
providerType|BANKLOCAL|
providerType|CREDITCARD|
providerType|NETELLER|
providerType|SKRILL|
providerType|ENVOY|
providerType|PAYSAFECARD|
providerType|UKASH|
providerType|PAYBOX|
providerType|PUGGLEPAY|
providerType|CLICKANDBUY|
providerType|PAYPAL|
providerType|MBANKOMAT|
providerType|PAYLEVO|
providerType|SIRU|
providerType|WORLDPAY|
providerType|IBANQ|
providerType|IDEAL|
providerType|LAVAPAY|
providerType|INSTADEBIT|
providerType|IDEBIT|
providerType|ECOPAYZ|
providerType|FORTUMO|
providerType|ASTROPAYCARD|
providerType|ASTROPAYDIRECT|
providerType|PPRO|
providerType|YUUCOLLECT|
providerType|BOKU|
providerType|NEOSURFVOUCHER|
providerType|CHINAUNIONPAY|
providerType|CITADEL|
providerType|PRZELEWY24|
providerType|PAYGROUND|
providerType|TELEINGRESO|
providerType|VENUSPOINT|
providerType|ENTROPAY|
providerType|MOBILEGIRO|
providerType|SMSVOUCHER|
providerType|TODITOCASH|
providerType|TICKETPREMIUM|
providerType|QIWI|
providerType|ICARD|
providerType|TOLAMOBILE|
providerType|FLEXEPIN|
providerType|FUNANGA|
providerType|VISAVOUCHER|
providerType|GIFTCARD|
providerType|MIFINITY|
providerType|OXXO|
providerType|IWALLET|
providerType|SEQR|
providerType|BOLETO|
providerType|CRYPTOCURRENCY|
providerType|MUCHBETTER|
providerType|KLUWP|
providerType|ASTROPAYBANK|
providerType|INTERNAL_CORRECTION|
providerType|EXTERNAL_CORRECTION|
providerType|INTERNAL|
providerType|EUTELLER|
providerType|TRUSTLY|
providerType|EPRO|
providerType|CASHLIB|
providerType|APCO|
providerType|SECURETRADING|
providerType|DOTPAY|
providerType|BLIK|
providerType|UNKNOWN|
status|ACTIVE|
status|INACTIVE|
status|NEW|
status|DELETED|
status|BLOCKED|


## UserPspAccountDetails

<a name="schemauserpspaccountdetails"></a>

```json
{
  "accountUuid": "string",
  "blockReason": "string",
  "description": "string",
  "directDebit": true,
  "expiryDate": "2017-11-06T10:24:37Z",
  "extAccountRefId": "string",
  "firstUsed": "2017-11-06T10:24:37Z",
  "hashedAccount": "string",
  "holder": "string",
  "id": 0,
  "lastSuccess": "2017-11-06T10:24:37Z",
  "lastUsed": "2017-11-06T10:24:37Z",
  "maskedAccount": "string",
  "merchantId": 0,
  "merchantUserId": "string",
  "new": true,
  "noFailedTx": 0,
  "noSuccessfulTx": 0,
  "providerType": "string",
  "startDate": "2017-11-06T10:24:37Z",
  "status": "ACTIVE",
  "storeAccount": true,
  "type": "CreditcardDeposit",
  "vaultData": {
    "property1": "string",
    "property2": "string"
  },
  "vaultIQData": {
    "property1": "string",
    "property2": "string"
  },
  "vaultIQUuid": "string",
  "vaultUuid": "string",
  "visibilityResetAllowed": true,
  "visible": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
accountUuid|string|false|No description
blockReason|string|false|No description
description|string|false|No description
directDebit|boolean|false|No description
expiryDate|string(date-time)|false|No description
extAccountRefId|string|false|No description
firstUsed|string(date-time)|false|No description
hashedAccount|string|false|No description
holder|string|false|No description
id|integer(int64)|false|No description
lastSuccess|string(date-time)|false|No description
lastUsed|string(date-time)|false|No description
maskedAccount|string|false|No description
merchantId|integer(int32)|false|No description
merchantUserId|string|false|No description
new|boolean|false|No description
noFailedTx|integer(int32)|false|No description
noSuccessfulTx|integer(int32)|false|No description
providerType|string|false|No description
startDate|string(date-time)|false|No description
status|string|false|No description
storeAccount|boolean|false|No description
type|string|false|No description
vaultData|object|false|No description
vaultIQData|object|false|No description
vaultIQUuid|string|false|No description
vaultUuid|string|false|No description
visibilityResetAllowed|boolean|false|No description
visible|boolean|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
status|ACTIVE|
status|INACTIVE|
status|NEW|
status|DELETED|
status|BLOCKED|
type|CreditcardDeposit|
type|CreditcardWithdrawal|
type|EntropayDeposit|
type|ICardDeposit|
type|ICardWithdrawal|
type|NetellerDeposit|
type|NetellerWithdrawal|
type|SkrillDeposit|
type|SkrillWithdrawal|
type|PayboxDeposit|
type|ClickandBuyDeposit|
type|ClickandBuyWithdrawal|
type|PayPalDeposit|
type|PayPalWithdrawal|
type|MbankomatDeposit|
type|IBanqDeposit|
type|IBanqWithdrawal|
type|LavaPayDeposit|
type|LavaPayWithdrawal|
type|InstadebitDeposit|
type|InstadebitWithdrawal|
type|IDebitDeposit|
type|IDebitWithdrawal|
type|EcoPayzDeposit|
type|EcoPayzWithdrawal|
type|AstroPayCardWithdrawal|
type|AstroPayDirectDeposit|
type|AstroPayDirectWithdrawal|
type|VenusPointDeposit|
type|VenusPointWithdrawal|
type|MiFinityEWalletDeposit|
type|MiFinityEWalletWithdrawal|
type|IWalletDeposit|
type|IWalletWithdrawal|
type|MuchBetterDeposit|
type|MuchBetterWithdrawal|
type|AstroPayBankWithdrawal|
type|EutellerDeposit|
type|EnvoyDeposit|
type|EnvoyWithdrawal|
type|TrustlyDeposit|
type|TrustlyWithdrawal|
type|BankDeposit|
type|BankLocalWithdrawal|
type|BankIBANWithdrawal|
type|BankIntIBANWithdrawal|
type|IdealDeposit|
type|ChinaUnionPayDeposit|
type|BankIntlWithdrawal|
type|ChinaUnionPayWithdrawal|
type|BoletoBancarioDeposit|
type|PaysafecardDeposit|
type|UkashDeposit|
type|UkashWithdrawal|
type|PaysafecardWithdrawal|
type|CashlibDeposit|
type|TicketPremiumDeposit|
type|FlexepinDeposit|
type|FunangaDeposit|
type|VisaVoucherDeposit|
type|GiftcardDeposit|
type|PugglePayDeposit|
type|PaylevoDeposit|
type|YuuCollectDeposit|
type|NeosurfVoucherDeposit|
type|OxxoDeposit|
type|SeqrDeposit|
type|CryptoCurrencyDeposit|
type|SeqrWithdrawal|
type|SiruDeposit|
type|SiruStatus|
type|SiruPriceCalc|
type|FortumoDeposit|
type|BokuDeposit|
type|BlikDeposit|
type|PayGroundDeposit|
type|SmsVoucherDeposit|
type|QiwiDeposit|
type|QiwiWithdrawal|
type|AccentPayDeposit|
type|AccentPayWithdrawal|
type|WorldPayDeposit|
type|WorldPayWithdrawal|
type|PProDeposit|
type|PProWithdrawal|
type|EProPaymentWallDeposit|
type|ApcoDeposit|
type|SecureTradingDeposit|
type|DotpayDeposit|
type|Przelewy24Deposit|
type|SweGiroDeposit|
type|ToditoCashDeposit|
type|TolaMobileDeposit|
type|KluwpDeposit|
type|TeleingresoDeposit|
type|ManualChargeback|
type|ManualRefund|
type|ManualCancel|
type|ManualVoid|
type|ManualChargeBackWon|
type|Refund|
type|Cancel|
type|Void|
type|Capture|


## VoidRequest

<a name="schemavoidrequest"></a>

```json
{
  "info": "Void reason...",
  "tagId": "CP-1"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
info|string|false|Any additional information to provide reason for capture. Maximum limit 200 characters.
tagId|string|false|Tag id, you need to predefine tags in MerchantConfig.The tag must be named Void, an example is <tags><entry><string>Void</string><list><tag><id>CP-1</id><name>Other reason</name></tag></list></entry></tags>





