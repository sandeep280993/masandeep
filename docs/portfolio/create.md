
# Create Credit Card

## Endpoint

**POST** `v1/credit-card-customer-details`

## Description
Create a new credit card customer.

## Parameters

|Parameter|Type|Required| Description |
|---------|----|--------|-------------|
| id | Number | Yes | Customer ID |
| name  | String | Yes | Customer name|
| creditCardIssuer| String| Optional| Credit card issuer|
| buildingNumber | Number| Yes | Building number|
| streetName | String| Yes | Street name|
| cityName | String| Yes | City|
| account | Number| Yes | Account number|
| country | String | Yes | country|

## Request

```curl
curl -L --request POST \
--url https://cisco-onc-ip:8443/onc-alarm-service/v2/network-alarms \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--data '{
        "name": "Laura Gutkowski",
        "creditCardIssuer": "mastercard",
        "buildingNumber": "23",
        "streetName": "Althea Bypass",
        "cityName": "Narcisostead",
        "account": "46271433",
        "country": "Central African Republic",
        "id": "14"
    }'

```
## Response
```json
200 Ok
{
        "name": "Laura Gutkowski",
        "creditCardIssuer": "mastercard",
        "buildingNumber": "23",
        "streetName": "Althea Bypass",
        "cityName": "Narcisostead",
        "account": "46271433",
        "country": "Central African Republic",
        "id": "14"
    }
```

