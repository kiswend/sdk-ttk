
# Test with auto accept party and and

```
# SDK config
AUTO_ACCEPT_QUOTES=true
AUTO_ACCEPT_PARTY=true
```

# Test

```bash
curl -X POST \
  http://localhost:4001/transfers \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
    "from": {
        "displayName": "John Doe",
        "idType": "MSISDN", 
        "idValue": "123456789"
    },
    "to": {
        "idType": "PERSONAL_ID",
        "idValue": "22912345678"
    },
    "amountType": "SEND",
    "currency": "XOF",
    "amount": "100",
    "transactionType": "TRANSFER",
    "note": "testpayment",
    "homeTransactionId": "'$(uuidgen || echo "test-$(date +%s)")'"
  }' | jq .

```

https://docs.mojaloop.io/api/fspiop/v1.1/api-definition.html#partyidtype-enum


```json

```