# Delete credit card customer

## Endpoint

**DELETE** `v1//credit-card-customer-details/:id`

## Description
Delete a credit card customer.

## Parameters

|Parameter|Type|Required| Description |
|---------|----|--------|-------------|
| id | Number | Yes | Customer ID |

## Request

```curl
curl -L --request DELETE \
--url https://6a32b6dac6ca2aee43857dc6.mockapi.io/credit-card-customers-api/v1/credit-card-customer-details/:id \
--header 'Accept: */*'

```
## Response
```json
200 Ok
```

