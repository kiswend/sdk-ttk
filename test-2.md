
# Test with auto accept party and and


Set the SDK config to disable auto accept party and quote
```
AUTO_ACCEPT_QUOTES=true
AUTO_ACCEPT_PARTY=true
```

## Test


## Discovery

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


```json
{
  "from": {
    "displayName": "John Doe",
    "idType": "MSISDN",
    "idValue": "123456789"
  },
  "to": {
    "idType": "PERSONAL_ID",
    "idValue": "22912345678",
    "fspId": "testingtoolkitdfsp",
    "extensionList": [
      {
        "incididunt_b": 16020025,
        "key": "dolor aute aliqui",
        "value": "consectetur fugiat reprehenderit incididunt Ut"
      },
      {
        "irure31b": -47707669.57588215,
        "tempor_2a": 8957787,
        "est_ad0": -79914555,
        "key": "moll",
        "value": "labore nostrud in occaecat"
      }
    ],
    "firstName": "Daniel",
    "middleName": "G",
    "lastName": "Lopez",
    "dateOfBirth": "1908-11-07"
  },
  "amountType": "SEND",
  "currency": "XOF",
  "amount": "100",
  "transactionType": "TRANSFER",
  "note": "testpayment",
  "homeTransactionId": "067B0073-A138-42CA-966D-2D2B7BDD6400",
  "transferId": "01KM0C006Q7XXR16H499P7NQQT",
  "traceId": "27af9bec343adaf86718176f107c6aeb",
  "currentState": "WAITING_FOR_PARTY_ACCEPTANCE",
  "initiatedTimestamp": "2026-03-18T11:41:16.390Z",
  "direction": "OUTBOUND",
  "getPartiesRequest": {
    "withCredentials": false,
    "transitional": {
      "clarifyTimeoutError": true
    },
    "method": "GET",
    "baseURL": "http://ml-testing-toolkit:4040",
    "url": "/parties/PERSONAL_ID/22912345678",
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:41:16 GMT",
      "fspiop-source": "itk-load-test-dfsp",
      "Authorization": "Bearer 7718fa9b-be13-3fe7-87f0-a12cf1628168",
      "accept": "application/vnd.interoperability.parties+json;version=1",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-302cf286e6fc3060-01"
    },
    "httpAgent": "[REDACTED]"
  },
  "getPartiesResponse": {
    "body": {
      "aliquip1f0": true,
      "dolorc6": 39936739.72606525,
      "commodo_42": 62944036.36199194,
      "ad_a": 48410893.60020962,
      "consequate3": "tempor",
      "party": {
        "partyIdInfo": {
          "partyIdType": "PERSONAL_ID",
          "partyIdentifier": "22912345678",
          "fspId": "testingtoolkitdfsp",
          "extensionList": {
            "ut_b6": "Ut Duis ex dolor commodo",
            "extension": [
              {
                "incididunt_b": 16020025,
                "key": "dolor aute aliqui",
                "value": "consectetur fugiat reprehenderit incididunt Ut"
              },
              {
                "irure31b": -47707669.57588215,
                "tempor_2a": 8957787,
                "est_ad0": -79914555,
                "key": "moll",
                "value": "labore nostrud in occaecat"
              }
            ]
          }
        },
        "merchantClassificationCode": "94",
        "name": "-, ,Cput-a.k{CgcPo_tiukMduiJcdul't,e'k=MucetgPduCriror_{ulcap .re}i}kliM",
        "personalInfo": {
          "complexName": {
            "firstName": "Daniel",
            "middleName": "G",
            "lastName": "Lopez"
          },
          "dateOfBirth": "1908-11-07"
        }
      }
    },
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:41:16 GMT",
      "x-forwarded-for": "in dolor dolore",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "consequat",
      "fspiop-signature": "voluptate minim cupidatat mollit",
      "fspiop-uri": "sed mollit quis",
      "fspiop-http-method": "fugiat aliquip et",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-302cf286e6fc3060-01",
      "user-agent": "axios/1.13.2",
      "content-length": 772,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    }
  }
}
```


## Agreement of terms

```bash
curl -X PUT \
  http://localhost:4001/transfers/01KM0C006Q7XXR16H499P7NQQT \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
  "acceptParty": true
}' | jq .

```

```json
{
  "from": {
    "displayName": "John Doe",
    "idType": "MSISDN",
    "idValue": "123456789"
  },
  "to": {
    "idType": "PERSONAL_ID",
    "idValue": "22912345678",
    "fspId": "testingtoolkitdfsp",
    "extensionList": [
      {
        "incididunt_b": 16020025,
        "key": "dolor aute aliqui",
        "value": "consectetur fugiat reprehenderit incididunt Ut"
      },
      {
        "irure31b": -47707669.57588215,
        "tempor_2a": 8957787,
        "est_ad0": -79914555,
        "key": "moll",
        "value": "labore nostrud in occaecat"
      }
    ],
    "firstName": "Daniel",
    "middleName": "G",
    "lastName": "Lopez",
    "dateOfBirth": "1908-11-07"
  },
  "amountType": "SEND",
  "currency": "XOF",
  "amount": "100",
  "transactionType": "TRANSFER",
  "note": "testpayment",
  "homeTransactionId": "067B0073-A138-42CA-966D-2D2B7BDD6400",
  "transferId": "01KM0C006Q7XXR16H499P7NQQT",
  "traceId": "27af9bec343adaf86718176f107c6aeb",
  "currentState": "WAITING_FOR_QUOTE_ACCEPTANCE",
  "initiatedTimestamp": "2026-03-18T11:41:16.390Z",
  "direction": "OUTBOUND",
  "getPartiesRequest": {
    "withCredentials": false,
    "transitional": {
      "clarifyTimeoutError": true
    },
    "method": "GET",
    "baseURL": "http://ml-testing-toolkit:4040",
    "url": "/parties/PERSONAL_ID/22912345678",
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:41:16 GMT",
      "fspiop-source": "itk-load-test-dfsp",
      "Authorization": "Bearer 7718fa9b-be13-3fe7-87f0-a12cf1628168",
      "accept": "application/vnd.interoperability.parties+json;version=1",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-302cf286e6fc3060-01"
    },
    "httpAgent": "[REDACTED]"
  },
  "getPartiesResponse": {
    "body": {
      "aliquip1f0": true,
      "dolorc6": 39936739.72606525,
      "commodo_42": 62944036.36199194,
      "ad_a": 48410893.60020962,
      "consequate3": "tempor",
      "party": {
        "partyIdInfo": {
          "partyIdType": "PERSONAL_ID",
          "partyIdentifier": "22912345678",
          "fspId": "testingtoolkitdfsp",
          "extensionList": {
            "ut_b6": "Ut Duis ex dolor commodo",
            "extension": [
              {
                "incididunt_b": 16020025,
                "key": "dolor aute aliqui",
                "value": "consectetur fugiat reprehenderit incididunt Ut"
              },
              {
                "irure31b": -47707669.57588215,
                "tempor_2a": 8957787,
                "est_ad0": -79914555,
                "key": "moll",
                "value": "labore nostrud in occaecat"
              }
            ]
          }
        },
        "merchantClassificationCode": "94",
        "name": "-, ,Cput-a.k{CgcPo_tiukMduiJcdul't,e'k=MucetgPduCriror_{ulcap .re}i}kliM",
        "personalInfo": {
          "complexName": {
            "firstName": "Daniel",
            "middleName": "G",
            "lastName": "Lopez"
          },
          "dateOfBirth": "1908-11-07"
        }
      }
    },
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:41:16 GMT",
      "x-forwarded-for": "in dolor dolore",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "consequat",
      "fspiop-signature": "voluptate minim cupidatat mollit",
      "fspiop-uri": "sed mollit quis",
      "fspiop-http-method": "fugiat aliquip et",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-302cf286e6fc3060-01",
      "user-agent": "axios/1.13.2",
      "content-length": 772,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    }
  },
  "acceptParty": true,
  "quoteId": "01KM0CSWD9BC86G4HPYJYAXQYM",
  "quoteRequest": {
    "body": {
      "quoteId": "01KM0CSWD9BC86G4HPYJYAXQYM",
      "transactionId": "01KM0C006Q7XXR16H499P7NQQT",
      "amountType": "SEND",
      "amount": {
        "currency": "XOF",
        "amount": "100"
      },
      "expiration": "2026-03-18T11:56:24.459Z",
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
          "fspId": "testingtoolkitdfsp",
          "extensionList": {
            "extension": [
              {
                "incididunt_b": 16020025,
                "key": "dolor aute aliqui",
                "value": "consectetur fugiat reprehenderit incididunt Ut"
              },
              {
                "irure31b": -47707669.57588215,
                "tempor_2a": 8957787,
                "est_ad0": -79914555,
                "key": "moll",
                "value": "labore nostrud in occaecat"
              }
            ]
          }
        },
        "personalInfo": {
          "complexName": {
            "firstName": "Daniel",
            "middleName": "G",
            "lastName": "Lopez"
          },
          "dateOfBirth": "1908-11-07"
        }
      },
      "transactionType": {
        "scenario": "TRANSFER",
        "initiator": "PAYER",
        "initiatorType": "CONSUMER"
      },
      "note": "testpayment"
    },
    "headers": {
      "content-type": "application/vnd.interoperability.quotes+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:55:24 GMT",
      "fspiop-source": "itk-load-test-dfsp",
      "fspiop-destination": "testingtoolkitdfsp",
      "Authorization": "Bearer 7718fa9b-be13-3fe7-87f0-a12cf1628168",
      "accept": "application/vnd.interoperability.quotes+json;version=1",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-f099b8651cce1721-01",
      "fspiop-http-method": "POST",
      "fspiop-uri": "/quotes",
      "fspiop-signature": "{\"signature\":\"IKtglMGj-u6YW0tmg_ZI5HVdNWYluzBMV-PPlgtpuVZQu00GuIaeNBssJnYaZ0knGZu02qS4EAR1lssprZSibS3rZj69nIi28NjU9n3hgv2fUhmF6ym0SsE-Zb-gBdO0hjbVDCqsC6nEAa0irUnEoilNesS1vTZ2qnFWejdmuxCB_wdnw3omlmk7KqWg2BHzU1EdILbYzwInChui59h1MVQRZgIVa4xCEq9Iju14gcyAT3crBBv8KsL0XgwSf7JFS8gGGQ5cTZuBCyzxgUXz6KHEACEET9oU1rVMRtTb4Mewl0wQV8ssL6omqoE_3MJi7xqN_SEDr4vXB-AB7RAVSw\",\"protectedHeader\":\"eyJhbGciOiJSUzI1NiIsIkZTUElPUC1VUkkiOiIvcXVvdGVzIiwiRlNQSU9QLUhUVFAtTWV0aG9kIjoiUE9TVCIsIkZTUElPUC1Tb3VyY2UiOiJpdGstbG9hZC10ZXN0LWRmc3AiLCJGU1BJT1AtRGVzdGluYXRpb24iOiJ0ZXN0aW5ndG9vbGtpdGRmc3AiLCJEYXRlIjoiV2VkLCAxOCBNYXIgMjAyNiAxMTo1NToyNCBHTVQifQ\"}"
    }
  },
  "quoteResponse": {
    "headers": {
      "content-type": "application/vnd.interoperability.quotes+json;version=1.1",
      "date": "Wed, 18 Mar 2026 11:55:24 GMT",
      "x-forwarded-for": "ut laboris culpa",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "eiusmod ullamco laborum nulla",
      "fspiop-signature": "ex Lorem reprehenderit anim",
      "fspiop-uri": "nisi ut in velit",
      "fspiop-http-method": "anim qui consectetur consequat aute",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-f099b8651cce1721-01",
      "user-agent": "axios/1.13.2",
      "content-length": 2561,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    },
    "body": {
      "transferAmount": {
        "laborisac": "Duis ipsum magna velit",
        "tempor_1_7": -53648890.13257543,
        "currency": "XOF",
        "amount": "100"
      },
      "payeeReceiveAmount": {
        "elit53": "dolore id nulla exercitation est",
        "temporf_2": true,
        "currency": "XOF",
        "amount": "99.7"
      },
      "payeeFspFee": {
        "voluptate5b_": -41674773.13649335,
        "elitc": -46609370.33679504,
        "cupidatat_c7_": 69811666,
        "magna_461": -8336973.924918741,
        "currency": "XOF",
        "amount": "0.5"
      },
      "payeeFspCommission": {
        "reprehenderit07b": -83920288.9285771,
        "sint_62": -65111867.33724066,
        "currency": "XOF",
        "amount": "0.2"
      },
      "expiration": "2026-03-19T11:55:25.210Z",
      "geoCode": {
        "ea_c": -2270268,
        "aliquip_5": -91680878.7135845,
        "elit_0": 70505874.76877683,
        "exercitation_9e": "pariatur Duis qui",
        "latitude": "8.7",
        "longitude": "180"
      },
      "ilpPacket": "AYIFKAAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggTvZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pTURGTFRUQkRNREEyVVRkWVdGSXhOa2cwT1RsUU4wNVJVVlFpTENKeGRXOTBaVWxrSWpvaU1ERkxUVEJEVTFkRU9VSkRPRFpITkVoUVdVcFpRVmhSV1UwaUxDSndZWGxsWlNJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJbEJGVWxOUFRrRk1YMGxFSWl3aWNHRnlkSGxKWkdWdWRHbG1hV1Z5SWpvaU1qSTVNVEl6TkRVMk56Z2lMQ0ptYzNCSlpDSTZJblJsYzNScGJtZDBiMjlzYTJsMFpHWnpjQ0lzSW1WNGRHVnVjMmx2Ymt4cGMzUWlPbnNpWlhoMFpXNXphVzl1SWpwYmV5SnBibU5wWkdsa2RXNTBYMklpT2pFMk1ESXdNREkxTENKclpYa2lPaUprYjJ4dmNpQmhkWFJsSUdGc2FYRjFhU0lzSW5aaGJIVmxJam9pWTI5dWMyVmpkR1YwZFhJZ1puVm5hV0YwSUhKbGNISmxhR1Z1WkdWeWFYUWdhVzVqYVdScFpIVnVkQ0JWZENKOUxIc2lhWEoxY21Vek1XSWlPaTAwTnpjd056WTJPUzQxTnpVNE9ESXhOU3dpZEdWdGNHOXlYekpoSWpvNE9UVTNOemczTENKbGMzUmZZV1F3SWpvdE56azVNVFExTlRVc0ltdGxlU0k2SW0xdmJHd2lMQ0oyWVd4MVpTSTZJbXhoWW05eVpTQnViM04wY25Wa0lHbHVJRzlqWTJGbFkyRjBJbjFkZlgwc0luQmxjbk52Ym1Gc1NXNW1ieUk2ZXlKamIyMXdiR1Y0VG1GdFpTSTZleUptYVhKemRFNWhiV1VpT2lKRVlXNXBaV3dpTENKdGFXUmtiR1ZPWVcxbElqb2lSeUlzSW14aGMzUk9ZVzFsSWpvaVRHOXdaWG9pZlN3aVpHRjBaVTltUW1seWRHZ2lPaUl4T1RBNExURXhMVEEzSW4xOUxDSndZWGxsY2lJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJazFUU1ZORVRpSXNJbkJoY25SNVNXUmxiblJwWm1sbGNpSTZJakV5TXpRMU5qYzRPU0lzSW1aemNFbGtJam9pYVhSckxXeHZZV1F0ZEdWemRDMWtabk53SW4wc0ltNWhiV1VpT2lKS2IyaHVJRVJ2WlNKOUxDSmhiVzkxYm5RaU9uc2liR0ZpYjNKcGMyRmpJam9pUkhWcGN5QnBjSE4xYlNCdFlXZHVZU0IyWld4cGRDSXNJblJsYlhCdmNsOHhYemNpT2kwMU16WTBPRGc1TUM0eE16STFOelUwTXl3aVkzVnljbVZ1WTNraU9pSllUMFlpTENKaGJXOTFiblFpT2lJeE1EQWlmU3dpZEhKaGJuTmhZM1JwYjI1VWVYQmxJanA3SW5OalpXNWhjbWx2SWpvaVZGSkJUbE5HUlZJaUxDSnBibWwwYVdGMGIzSWlPaUpRUVZsRlVpSXNJbWx1YVhScFlYUnZjbFI1Y0dVaU9pSkRUMDVUVlUxRlVpSjlMQ0psZUhCcGNtRjBhVzl1SWpvaU1qQXlOaTB3TXkweE9WUXhNVG8xTlRveU5TNHlNVEJhSW4wAA",
      "condition": "w8LgwMlLWH8kJ87uxsi1fhotAmK2-CILaI68R2U1NLM"
    },
    "originalIso20022QuoteResponse": {}
  },
  "quoteResponseSource": "testingtoolkitdfsp"
}
```


## Transfer

```bash
curl -X PUT \
  http://localhost:4001/transfers/01KM0C006Q7XXR16H499P7NQQT \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
  "acceptQuote": true
}' | jq .

```

```json
{
  "from": {
    "displayName": "John Doe",
    "idType": "MSISDN",
    "idValue": "123456789"
  },
  "to": {
    "idType": "PERSONAL_ID",
    "idValue": "22912345678",
    "fspId": "testingtoolkitdfsp",
    "extensionList": [
      {
        "incididunt_b": 16020025,
        "key": "dolor aute aliqui",
        "value": "consectetur fugiat reprehenderit incididunt Ut"
      },
      {
        "irure31b": -47707669.57588215,
        "tempor_2a": 8957787,
        "est_ad0": -79914555,
        "key": "moll",
        "value": "labore nostrud in occaecat"
      }
    ],
    "firstName": "Daniel",
    "middleName": "G",
    "lastName": "Lopez",
    "dateOfBirth": "1908-11-07"
  },
  "amountType": "SEND",
  "currency": "XOF",
  "amount": "100",
  "transactionType": "TRANSFER",
  "note": "testpayment",
  "homeTransactionId": "067B0073-A138-42CA-966D-2D2B7BDD6400",
  "transferId": "01KM0C006Q7XXR16H499P7NQQT",
  "traceId": "27af9bec343adaf86718176f107c6aeb",
  "currentState": "COMPLETED",
  "initiatedTimestamp": "2026-03-18T11:41:16.390Z",
  "direction": "OUTBOUND",
  "getPartiesRequest": {
    "withCredentials": false,
    "transitional": {
      "clarifyTimeoutError": true
    },
    "method": "GET",
    "baseURL": "http://ml-testing-toolkit:4040",
    "url": "/parties/PERSONAL_ID/22912345678",
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:41:16 GMT",
      "fspiop-source": "itk-load-test-dfsp",
      "Authorization": "Bearer 7718fa9b-be13-3fe7-87f0-a12cf1628168",
      "accept": "application/vnd.interoperability.parties+json;version=1",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-302cf286e6fc3060-01"
    },
    "httpAgent": "[REDACTED]"
  },
  "getPartiesResponse": {
    "body": {
      "aliquip1f0": true,
      "dolorc6": 39936739.72606525,
      "commodo_42": 62944036.36199194,
      "ad_a": 48410893.60020962,
      "consequate3": "tempor",
      "party": {
        "partyIdInfo": {
          "partyIdType": "PERSONAL_ID",
          "partyIdentifier": "22912345678",
          "fspId": "testingtoolkitdfsp",
          "extensionList": {
            "ut_b6": "Ut Duis ex dolor commodo",
            "extension": [
              {
                "incididunt_b": 16020025,
                "key": "dolor aute aliqui",
                "value": "consectetur fugiat reprehenderit incididunt Ut"
              },
              {
                "irure31b": -47707669.57588215,
                "tempor_2a": 8957787,
                "est_ad0": -79914555,
                "key": "moll",
                "value": "labore nostrud in occaecat"
              }
            ]
          }
        },
        "merchantClassificationCode": "94",
        "name": "-, ,Cput-a.k{CgcPo_tiukMduiJcdul't,e'k=MucetgPduCriror_{ulcap .re}i}kliM",
        "personalInfo": {
          "complexName": {
            "firstName": "Daniel",
            "middleName": "G",
            "lastName": "Lopez"
          },
          "dateOfBirth": "1908-11-07"
        }
      }
    },
    "headers": {
      "content-type": "application/vnd.interoperability.parties+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:41:16 GMT",
      "x-forwarded-for": "in dolor dolore",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "consequat",
      "fspiop-signature": "voluptate minim cupidatat mollit",
      "fspiop-uri": "sed mollit quis",
      "fspiop-http-method": "fugiat aliquip et",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-302cf286e6fc3060-01",
      "user-agent": "axios/1.13.2",
      "content-length": 772,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    }
  },
  "acceptParty": true,
  "quoteId": "01KM0CSWD9BC86G4HPYJYAXQYM",
  "quoteRequest": {
    "body": {
      "quoteId": "01KM0CSWD9BC86G4HPYJYAXQYM",
      "transactionId": "01KM0C006Q7XXR16H499P7NQQT",
      "amountType": "SEND",
      "amount": {
        "currency": "XOF",
        "amount": "100"
      },
      "expiration": "2026-03-18T11:56:24.459Z",
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
          "fspId": "testingtoolkitdfsp",
          "extensionList": {
            "extension": [
              {
                "incididunt_b": 16020025,
                "key": "dolor aute aliqui",
                "value": "consectetur fugiat reprehenderit incididunt Ut"
              },
              {
                "irure31b": -47707669.57588215,
                "tempor_2a": 8957787,
                "est_ad0": -79914555,
                "key": "moll",
                "value": "labore nostrud in occaecat"
              }
            ]
          }
        },
        "personalInfo": {
          "complexName": {
            "firstName": "Daniel",
            "middleName": "G",
            "lastName": "Lopez"
          },
          "dateOfBirth": "1908-11-07"
        }
      },
      "transactionType": {
        "scenario": "TRANSFER",
        "initiator": "PAYER",
        "initiatorType": "CONSUMER"
      },
      "note": "testpayment"
    },
    "headers": {
      "content-type": "application/vnd.interoperability.quotes+json;version=1.0",
      "date": "Wed, 18 Mar 2026 11:55:24 GMT",
      "fspiop-source": "itk-load-test-dfsp",
      "fspiop-destination": "testingtoolkitdfsp",
      "Authorization": "Bearer 7718fa9b-be13-3fe7-87f0-a12cf1628168",
      "accept": "application/vnd.interoperability.quotes+json;version=1",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-f099b8651cce1721-01",
      "fspiop-http-method": "POST",
      "fspiop-uri": "/quotes",
      "fspiop-signature": "{\"signature\":\"IKtglMGj-u6YW0tmg_ZI5HVdNWYluzBMV-PPlgtpuVZQu00GuIaeNBssJnYaZ0knGZu02qS4EAR1lssprZSibS3rZj69nIi28NjU9n3hgv2fUhmF6ym0SsE-Zb-gBdO0hjbVDCqsC6nEAa0irUnEoilNesS1vTZ2qnFWejdmuxCB_wdnw3omlmk7KqWg2BHzU1EdILbYzwInChui59h1MVQRZgIVa4xCEq9Iju14gcyAT3crBBv8KsL0XgwSf7JFS8gGGQ5cTZuBCyzxgUXz6KHEACEET9oU1rVMRtTb4Mewl0wQV8ssL6omqoE_3MJi7xqN_SEDr4vXB-AB7RAVSw\",\"protectedHeader\":\"eyJhbGciOiJSUzI1NiIsIkZTUElPUC1VUkkiOiIvcXVvdGVzIiwiRlNQSU9QLUhUVFAtTWV0aG9kIjoiUE9TVCIsIkZTUElPUC1Tb3VyY2UiOiJpdGstbG9hZC10ZXN0LWRmc3AiLCJGU1BJT1AtRGVzdGluYXRpb24iOiJ0ZXN0aW5ndG9vbGtpdGRmc3AiLCJEYXRlIjoiV2VkLCAxOCBNYXIgMjAyNiAxMTo1NToyNCBHTVQifQ\"}"
    }
  },
  "quoteResponse": {
    "headers": {
      "content-type": "application/vnd.interoperability.quotes+json;version=1.1",
      "date": "Wed, 18 Mar 2026 11:55:24 GMT",
      "x-forwarded-for": "ut laboris culpa",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "eiusmod ullamco laborum nulla",
      "fspiop-signature": "ex Lorem reprehenderit anim",
      "fspiop-uri": "nisi ut in velit",
      "fspiop-http-method": "anim qui consectetur consequat aute",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-f099b8651cce1721-01",
      "user-agent": "axios/1.13.2",
      "content-length": 2561,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    },
    "body": {
      "transferAmount": {
        "laborisac": "Duis ipsum magna velit",
        "tempor_1_7": -53648890.13257543,
        "currency": "XOF",
        "amount": "100"
      },
      "payeeReceiveAmount": {
        "elit53": "dolore id nulla exercitation est",
        "temporf_2": true,
        "currency": "XOF",
        "amount": "99.7"
      },
      "payeeFspFee": {
        "voluptate5b_": -41674773.13649335,
        "elitc": -46609370.33679504,
        "cupidatat_c7_": 69811666,
        "magna_461": -8336973.924918741,
        "currency": "XOF",
        "amount": "0.5"
      },
      "payeeFspCommission": {
        "reprehenderit07b": -83920288.9285771,
        "sint_62": -65111867.33724066,
        "currency": "XOF",
        "amount": "0.2"
      },
      "expiration": "2026-03-19T11:55:25.210Z",
      "geoCode": {
        "ea_c": -2270268,
        "aliquip_5": -91680878.7135845,
        "elit_0": 70505874.76877683,
        "exercitation_9e": "pariatur Duis qui",
        "latitude": "8.7",
        "longitude": "180"
      },
      "ilpPacket": "AYIFKAAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggTvZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pTURGTFRUQkRNREEyVVRkWVdGSXhOa2cwT1RsUU4wNVJVVlFpTENKeGRXOTBaVWxrSWpvaU1ERkxUVEJEVTFkRU9VSkRPRFpITkVoUVdVcFpRVmhSV1UwaUxDSndZWGxsWlNJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJbEJGVWxOUFRrRk1YMGxFSWl3aWNHRnlkSGxKWkdWdWRHbG1hV1Z5SWpvaU1qSTVNVEl6TkRVMk56Z2lMQ0ptYzNCSlpDSTZJblJsYzNScGJtZDBiMjlzYTJsMFpHWnpjQ0lzSW1WNGRHVnVjMmx2Ymt4cGMzUWlPbnNpWlhoMFpXNXphVzl1SWpwYmV5SnBibU5wWkdsa2RXNTBYMklpT2pFMk1ESXdNREkxTENKclpYa2lPaUprYjJ4dmNpQmhkWFJsSUdGc2FYRjFhU0lzSW5aaGJIVmxJam9pWTI5dWMyVmpkR1YwZFhJZ1puVm5hV0YwSUhKbGNISmxhR1Z1WkdWeWFYUWdhVzVqYVdScFpIVnVkQ0JWZENKOUxIc2lhWEoxY21Vek1XSWlPaTAwTnpjd056WTJPUzQxTnpVNE9ESXhOU3dpZEdWdGNHOXlYekpoSWpvNE9UVTNOemczTENKbGMzUmZZV1F3SWpvdE56azVNVFExTlRVc0ltdGxlU0k2SW0xdmJHd2lMQ0oyWVd4MVpTSTZJbXhoWW05eVpTQnViM04wY25Wa0lHbHVJRzlqWTJGbFkyRjBJbjFkZlgwc0luQmxjbk52Ym1Gc1NXNW1ieUk2ZXlKamIyMXdiR1Y0VG1GdFpTSTZleUptYVhKemRFNWhiV1VpT2lKRVlXNXBaV3dpTENKdGFXUmtiR1ZPWVcxbElqb2lSeUlzSW14aGMzUk9ZVzFsSWpvaVRHOXdaWG9pZlN3aVpHRjBaVTltUW1seWRHZ2lPaUl4T1RBNExURXhMVEEzSW4xOUxDSndZWGxsY2lJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJazFUU1ZORVRpSXNJbkJoY25SNVNXUmxiblJwWm1sbGNpSTZJakV5TXpRMU5qYzRPU0lzSW1aemNFbGtJam9pYVhSckxXeHZZV1F0ZEdWemRDMWtabk53SW4wc0ltNWhiV1VpT2lKS2IyaHVJRVJ2WlNKOUxDSmhiVzkxYm5RaU9uc2liR0ZpYjNKcGMyRmpJam9pUkhWcGN5QnBjSE4xYlNCdFlXZHVZU0IyWld4cGRDSXNJblJsYlhCdmNsOHhYemNpT2kwMU16WTBPRGc1TUM0eE16STFOelUwTXl3aVkzVnljbVZ1WTNraU9pSllUMFlpTENKaGJXOTFiblFpT2lJeE1EQWlmU3dpZEhKaGJuTmhZM1JwYjI1VWVYQmxJanA3SW5OalpXNWhjbWx2SWpvaVZGSkJUbE5HUlZJaUxDSnBibWwwYVdGMGIzSWlPaUpRUVZsRlVpSXNJbWx1YVhScFlYUnZjbFI1Y0dVaU9pSkRUMDVUVlUxRlVpSjlMQ0psZUhCcGNtRjBhVzl1SWpvaU1qQXlOaTB3TXkweE9WUXhNVG8xTlRveU5TNHlNVEJhSW4wAA",
      "condition": "w8LgwMlLWH8kJ87uxsi1fhotAmK2-CILaI68R2U1NLM"
    },
    "originalIso20022QuoteResponse": {}
  },
  "quoteResponseSource": "testingtoolkitdfsp",
  "acceptQuote": true,
  "prepare": {
    "body": {
      "transferId": "01KM0C006Q7XXR16H499P7NQQT",
      "payeeFsp": "testingtoolkitdfsp",
      "payerFsp": "itk-load-test-dfsp",
      "amount": {
        "currency": "XOF",
        "amount": "100"
      },
      "ilpPacket": "AYIFKAAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggTvZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pTURGTFRUQkRNREEyVVRkWVdGSXhOa2cwT1RsUU4wNVJVVlFpTENKeGRXOTBaVWxrSWpvaU1ERkxUVEJEVTFkRU9VSkRPRFpITkVoUVdVcFpRVmhSV1UwaUxDSndZWGxsWlNJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJbEJGVWxOUFRrRk1YMGxFSWl3aWNHRnlkSGxKWkdWdWRHbG1hV1Z5SWpvaU1qSTVNVEl6TkRVMk56Z2lMQ0ptYzNCSlpDSTZJblJsYzNScGJtZDBiMjlzYTJsMFpHWnpjQ0lzSW1WNGRHVnVjMmx2Ymt4cGMzUWlPbnNpWlhoMFpXNXphVzl1SWpwYmV5SnBibU5wWkdsa2RXNTBYMklpT2pFMk1ESXdNREkxTENKclpYa2lPaUprYjJ4dmNpQmhkWFJsSUdGc2FYRjFhU0lzSW5aaGJIVmxJam9pWTI5dWMyVmpkR1YwZFhJZ1puVm5hV0YwSUhKbGNISmxhR1Z1WkdWeWFYUWdhVzVqYVdScFpIVnVkQ0JWZENKOUxIc2lhWEoxY21Vek1XSWlPaTAwTnpjd056WTJPUzQxTnpVNE9ESXhOU3dpZEdWdGNHOXlYekpoSWpvNE9UVTNOemczTENKbGMzUmZZV1F3SWpvdE56azVNVFExTlRVc0ltdGxlU0k2SW0xdmJHd2lMQ0oyWVd4MVpTSTZJbXhoWW05eVpTQnViM04wY25Wa0lHbHVJRzlqWTJGbFkyRjBJbjFkZlgwc0luQmxjbk52Ym1Gc1NXNW1ieUk2ZXlKamIyMXdiR1Y0VG1GdFpTSTZleUptYVhKemRFNWhiV1VpT2lKRVlXNXBaV3dpTENKdGFXUmtiR1ZPWVcxbElqb2lSeUlzSW14aGMzUk9ZVzFsSWpvaVRHOXdaWG9pZlN3aVpHRjBaVTltUW1seWRHZ2lPaUl4T1RBNExURXhMVEEzSW4xOUxDSndZWGxsY2lJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJazFUU1ZORVRpSXNJbkJoY25SNVNXUmxiblJwWm1sbGNpSTZJakV5TXpRMU5qYzRPU0lzSW1aemNFbGtJam9pYVhSckxXeHZZV1F0ZEdWemRDMWtabk53SW4wc0ltNWhiV1VpT2lKS2IyaHVJRVJ2WlNKOUxDSmhiVzkxYm5RaU9uc2liR0ZpYjNKcGMyRmpJam9pUkhWcGN5QnBjSE4xYlNCdFlXZHVZU0IyWld4cGRDSXNJblJsYlhCdmNsOHhYemNpT2kwMU16WTBPRGc1TUM0eE16STFOelUwTXl3aVkzVnljbVZ1WTNraU9pSllUMFlpTENKaGJXOTFiblFpT2lJeE1EQWlmU3dpZEhKaGJuTmhZM1JwYjI1VWVYQmxJanA3SW5OalpXNWhjbWx2SWpvaVZGSkJUbE5HUlZJaUxDSnBibWwwYVdGMGIzSWlPaUpRUVZsRlVpSXNJbWx1YVhScFlYUnZjbFI1Y0dVaU9pSkRUMDVUVlUxRlVpSjlMQ0psZUhCcGNtRjBhVzl1SWpvaU1qQXlOaTB3TXkweE9WUXhNVG8xTlRveU5TNHlNVEJhSW4wAA",
      "condition": "w8LgwMlLWH8kJ87uxsi1fhotAmK2-CILaI68R2U1NLM",
      "expiration": "2026-03-18T11:57:38.977Z"
    },
    "headers": {
      "content-type": "application/vnd.interoperability.transfers+json;version=1.1",
      "date": "Wed, 18 Mar 2026 11:56:38 GMT",
      "fspiop-source": "itk-load-test-dfsp",
      "fspiop-destination": "testingtoolkitdfsp",
      "Authorization": "Bearer 7718fa9b-be13-3fe7-87f0-a12cf1628168",
      "accept": "application/vnd.interoperability.transfers+json;version=1",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-f53853c1ad9dc170-01",
      "fspiop-http-method": "POST",
      "fspiop-uri": "/transfers",
      "fspiop-signature": "{\"signature\":\"x99fW-nyHGgf-5ShqqVbbt3DnqIj7gQIhyyV3xL1bK0qlQu7dK8MLnuyyP2zwOF1Mw4Hr9E-VaxJhaCrRd6SjGZrJUPJbT7RH1bmzYgxFy6xLcQaUk-zpJhfQ0qowprpRj6vjJ3DdrCKc09pKHFfPMZh1eT8hwkgGTm3T7sh9gaPIooyPJGd-kbOvuIb5pzej9zCf7haHYrJLoOh-CrwAkCYRq2WSwUF54MleiAismm9Cc80mztRzQad2ObHYBu6C8F56L-5hpzoQTUENMZFqWfgbK1naybEVIdr6G2HCyJtGXD2nCnAetxFJ2E7L9ky7ExHcoZGYLNYz0WmPUNScA\",\"protectedHeader\":\"eyJhbGciOiJSUzI1NiIsIkZTUElPUC1VUkkiOiIvdHJhbnNmZXJzIiwiRlNQSU9QLUhUVFAtTWV0aG9kIjoiUE9TVCIsIkZTUElPUC1Tb3VyY2UiOiJpdGstbG9hZC10ZXN0LWRmc3AiLCJGU1BJT1AtRGVzdGluYXRpb24iOiJ0ZXN0aW5ndG9vbGtpdGRmc3AiLCJEYXRlIjoiV2VkLCAxOCBNYXIgMjAyNiAxMTo1NjozOCBHTVQifQ\"}"
    }
  },
  "fulfil": {
    "body": {
      "fulfilment": "b0BvdJjuwARY3my-ar4kOGz-kWhKNnLG_7xa5g-MumE",
      "completedTimestamp": "2026-03-18T11:56:40.313Z",
      "transferState": "COMMITTED"
    },
    "headers": {
      "content-type": "application/vnd.interoperability.transfers+json;version=1.1",
      "date": "Wed, 18 Mar 2026 11:56:38 GMT",
      "x-forwarded-for": "dolor aliquip",
      "fspiop-source": "testingtoolkitdfsp",
      "fspiop-destination": "itk-load-test-dfsp",
      "fspiop-encryption": "dolore velit",
      "fspiop-signature": "irure nisi eiusmod sunt quis",
      "fspiop-uri": "amet",
      "fspiop-http-method": "fugiat ea in labore",
      "traceparent": "00-27af9bec343adaf86718176f107c6aeb-f53853c1ad9dc170-01",
      "user-agent": "axios/1.13.2",
      "content-length": 136,
      "accept-encoding": "gzip, compress, deflate, br",
      "host": "mojaloop-connector-load-test:4000",
      "connection": "keep-alive"
    }
  }
}
```