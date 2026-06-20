
# Test with dedicated endpoints


Set the SDK config to disable auto accept party and quote
```
AUTO_ACCEPT_QUOTES=true
AUTO_ACCEPT_PARTY=true
```


## Discovery


```bash
curl http://localhost:4001/parties/MSISDN/22912345678 | jq .
```

```json
{
  "party": {
    "body": {
      "partyIdInfo": {
        "partyIdType": "MSISDN",
        "partyIdentifier": "22912345678",
        "fspId": "testingtoolkitdfsp",
        "extensionList": {
          "extension": [
            {
              "velit2": 54596989,
              "laborum_3_": true,
              "nostrudf": -42985379,
              "key": "proident",
              "value": "dolo"
            },
            {
              "key": "aliquip pariat",
              "value": "laborum Ut"
            }
          ]
        }
      },
      "merchantClassificationCode": "901",
      "name": "pPJrJo,iJuadg.d='Je..g P-C_ tL{tnnCCl-'kolle}gkMCtlpL_ccrCkrd.ipoPn=Jl cne}-.kJkJCJCgJp",
      "personalInfo": {
        "complexName": {
          "firstName": "Michael",
          "middleName": "G",
          "lastName": "Jones"
        },
        "dateOfBirth": "1985-06-12"
      }
    },
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 12:02:31 GMT",
      "x-forwarded-for": "nulla ullamco",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "occaecat amet",
      "fspiop-signature": "amet dolor nisi",
      "fspiop-uri": "cillum sit occaecat do",
      "fspiop-http-method": "proident aliqua",
      "traceparent": "00-ccdd57a23c5ec3735f7739a33862b6-0123456789abcdef0-00",
      "user-agent": "axios/1.13.2",
      "content-length": 547,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    }
  },
  "currentState": "COMPLETED"
}
```


## Agreement of terms

```bash
curl -X POST \
  http://localhost:4001/quotes \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
    "fspId": "testingtoolkitdfsp",
    "quotesPostRequest": {
      "quoteId": "b51ec534-ee48-4575-b6a9-ead2955b8069",
      "transactionId": "a8323bc6-c228-4df2-ae82-e5a997baf899",
      "payer": {
        "partyIdInfo": {
          "partyIdType": "MSISDN",
          "partyIdentifier": "123456789",
          "fspId": "itk-load-test-dfsp"
        },
        "name": "John Doe"
      },
      "payee": {
        "partyIdInfo": {
          "partyIdType": "PERSONAL_ID",
          "partyIdentifier": "22912345678",
          "fspId": "testingtoolkitdfsp"
        }
      },
      "amountType": "SEND",
      "amount": {
        "currency": "XOF",
        "amount": "100"
      },
      "transactionType": {
        "scenario": "TRANSFER",
        "initiator": "PAYER",
        "initiatorType": "CONSUMER"
      },
      "note": "testpayment"
    }
  }' | jq .

```


```json
{
  "quotes": {
    "body": {
      "transferAmount": {
        "currency": "XOF",
        "amount": "100"
      },
      "payeeReceiveAmount": {
        "currency": "XOF",
        "amount": "99.7"
      },
      "payeeFspFee": {
        "currency": "XOF",
        "amount": "0.5"
      },
      "payeeFspCommission": {
        "essee": 73519444,
        "pariatur_6": 63668610,
        "id_f6_": -67114717.2794945,
        "currency": "XOF",
        "amount": "0.2"
      },
      "expiration": "2026-03-19T12:15:51.687Z",
      "geoCode": {
        "voluptate0d": "pariatur consequat",
        "magna_9a": -32559588,
        "aliquip_77f": -48488091,
        "cillum_3": true,
        "velit_1a": -85018185,
        "latitude": "+90.00000",
        "longitude": "180.00"
      },
      "ilpPacket": "AYIC7AAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggKzZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pWVRnek1qTmlZell0WXpJeU9DMDBaR1l5TFdGbE9ESXRaVFZoT1RrM1ltRm1PRGs1SWl3aWNYVnZkR1ZKWkNJNkltSTFNV1ZqTlRNMExXVmxORGd0TkRVM05TMWlObUU1TFdWaFpESTVOVFZpT0RBMk9TSXNJbkJoZVdWbElqcDdJbkJoY25SNVNXUkpibVp2SWpwN0luQmhjblI1U1dSVWVYQmxJam9pVUVWU1UwOU9RVXhmU1VRaUxDSndZWEowZVVsa1pXNTBhV1pwWlhJaU9pSXlNamt4TWpNME5UWTNPQ0lzSW1aemNFbGtJam9pZEdWemRHbHVaM1J2YjJ4cmFYUmtabk53SW4xOUxDSndZWGxsY2lJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJazFUU1ZORVRpSXNJbkJoY25SNVNXUmxiblJwWm1sbGNpSTZJakV5TXpRMU5qYzRPU0lzSW1aemNFbGtJam9pYVhSckxXeHZZV1F0ZEdWemRDMWtabk53SW4wc0ltNWhiV1VpT2lKS2IyaHVJRVJ2WlNKOUxDSmhiVzkxYm5RaU9uc2lZM1Z5Y21WdVkza2lPaUpZVDBZaUxDSmhiVzkxYm5RaU9pSXhNREFpZlN3aWRISmhibk5oWTNScGIyNVVlWEJsSWpwN0luTmpaVzVoY21sdklqb2lWRkpCVGxOR1JWSWlMQ0pwYm1sMGFXRjBiM0lpT2lKUVFWbEZVaUlzSW1sdWFYUnBZWFJ2Y2xSNWNHVWlPaUpEVDA1VFZVMUZVaUo5TENKbGVIQnBjbUYwYVc5dUlqb2lNakF5Tmkwd015MHhPVlF4TWpveE5UbzFNUzQyT0RkYUluMAA",
      "condition": "tzmNbeISpQzT6Lcge3p8bVqZcj9Ud_3vogztskGa7Lc"
    },
    "headers": {
      "content-type": "application/vnd.interoperability.quotes+json;version=1.1",
      "date": "Wed, 18 Mar 2026 12:15:51 GMT",
      "x-forwarded-for": "quis cupidatat deserunt",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "nisi",
      "fspiop-signature": "consequat enim ut",
      "fspiop-uri": "deserunt in amet occaecat aute",
      "fspiop-http-method": "aliqua dolor in reprehenderit nulla",
      "traceparent": "00-ccdd9bc0f01271b637e6d095441a86-0123456789abcdef0-00",
      "user-agent": "axios/1.13.2",
      "content-length": 1566,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    },
    "originalIso20022QuoteResponse": {}
  },
  "currentState": "COMPLETED"
}
```




## Transfer

```bash
curl -X POST \
  http://localhost:4001/simpleTransfers \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
    "fspId": "testingtoolkitdfsp",
    "transfersPostRequest": {
      "transferId": "c72ec534-ee48-4575-b6a9-ead2955b8999",
      "payerFsp": "itk-load-test-dfsp",
      "payeeFsp": "testingtoolkitdfsp",
      "amount": {
        "currency": "XOF",
        "amount": "100"
      },
      "ilpPacket": "AYIC7AAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggKzZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pWVRnek1qTmlZell0WXpJeU9DMDBaR1l5TFdGbE9ESXRaVFZoT1RrM1ltRm1PRGs1SWl3aWNYVnZkR1ZKWkNJNkltSTFNV1ZqTlRNMExXVmxORGd0TkRVM05TMWlObUU1TFdWaFpESTVOVFZpT0RBMk9TSXNJbkJoZVdWbElqcDdJbkJoY25SNVNXUkpibVp2SWpwN0luQmhjblI1U1dSVWVYQmxJam9pVUVWU1UwOU9RVXhmU1VRaUxDSndZWEowZVVsa1pXNTBhV1pwWlhJaU9pSXlNamt4TWpNME5UWTNPQ0lzSW1aemNFbGtJam9pZEdWemRHbHVaM1J2YjJ4cmFYUmtabk53SW4xOUxDSndZWGxsY2lJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJazFUU1ZORVRpSXNJbkJoY25SNVNXUmxiblJwWm1sbGNpSTZJakV5TXpRMU5qYzRPU0lzSW1aemNFbGtJam9pYVhSckxXeHZZV1F0ZEdWemRDMWtabk53SW4wc0ltNWhiV1VpT2lKS2IyaHVJRVJ2WlNKOUxDSmhiVzkxYm5RaU9uc2lZM1Z5Y21WdVkza2lPaUpZVDBZaUxDSmhiVzkxYm5RaU9pSXhNREFpZlN3aWRISmhibk5oWTNScGIyNVVlWEJsSWpwN0luTmpaVzVoY21sdklqb2lWRkpCVGxOR1JWSWlMQ0pwYm1sMGFXRjBiM0lpT2lKUVFWbEZVaUlzSW1sdWFYUnBZWFJ2Y2xSNWNHVWlPaUpEVDA1VFZVMUZVaUo5TENKbGVIQnBjbUYwYVc5dUlqb2lNakF5Tmkwd015MHhPVlF4TWpveE5UbzFNUzQyT0RkYUluMAA",
      "condition": "tzmNbeISpQzT6Lcge3p8bVqZcj9Ud_3vogztskGa7Lc",
      "expiration": "2026-03-19T12:15:51.687Z"
    }
  }' | jq .
```


```json
{
  "transfer": {
    "body": {
      "fulfilment": "4lOUtGn4OUK12foXiNUDS0vM4cL7JlgUt4ndCZVALyw",
      "completedTimestamp": "2026-03-18T12:17:10.685Z",
      "transferState": "COMMITTED"
    },
    "headers": {
      "content-type": "application/vnd.interoperability.transfers+json;version=1.1",
      "date": "Wed, 18 Mar 2026 12:17:09 GMT",
      "x-forwarded-for": "aute irure nisi in dolore",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "non laboris dolore amet nisi",
      "fspiop-signature": "ut voluptate sunt labore sit",
      "fspiop-uri": "et voluptate fugiat dolore ut",
      "fspiop-http-method": "nulla do anim sint",
      "traceparent": "00-ccdd903287cc8de1edd0b073ae5781-0123456789abcdef0-00",
      "user-agent": "axios/1.13.2",
      "content-length": 136,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    }
  },
  "currentState": "COMPLETED"
}
```