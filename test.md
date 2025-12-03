
- **Port 4000**: Inbound API (receives requests from Mojaloop)
- **Port 4001**: Outbound API (sends requests to Mojaloop) - **Use this for transfers**
- **Port 4002**: Test API


```bash
curl http://localhost:4001/parties/MSISDN/22912345678


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
        "idType": "MSISDN",
        "idValue": "22912345678"
    },
    "amountType": "SEND",
    "currency": "USD",
    "amount": "100",
    "transactionType": "TRANSFER",
    "note": "testpayment",
    "homeTransactionId": "'$(uuidgen || echo "test-$(date +%s)")'"
  }' | jq .

```