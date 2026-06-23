# Update credit card customer details

## Endpoint

**PUT** `v1/credit-card-customer-details/:id`

## Description
Update a credit card customer details.

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

```cURL
curl -L --request PUT \
--url https://6a32b6dac6ca2aee43857dc6.mockapi.io/credit-card-customers-api/v1/credit-card-customer-details/:id \
--header 'Accept: */*'
-- data {
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

## Response
```json
200 Ok
```
