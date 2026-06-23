# Retrieve credit card by customer ID

## Endpoint
**GET** `v1/credit-card-customer-details`

## Request

```cURL
curl -L --request GET \
--url https://6a32b6dac6ca2aee43857dc6.mockapi.io/credit-card-customers-api/v1/credit-card-customer-details/:id \
--header 'Accept: */*'
```

## Response
```json
200 Ok
```

## Parameters

|Parameter|Type|Required| Description |
|---------|----|--------|-------------|
| id | Number | Yes | Customer ID |