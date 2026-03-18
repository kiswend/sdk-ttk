curl -X POST \
  http://localhost:4001/bulkQuotes \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
    "bulkQuoteId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
    "homeTransactionId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
    "from": {
        "displayName": "Bulk Sender DFSP A",
        "idType": "MSISDN", 
        "idValue": "123456789"
    },
    "individualQuotes": [
        {
            "quoteId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
            "to": {
                "idType": "PERSONAL_ID",
                "idValue": "22912345678"
            },
            "amountType": "SEND",
            "currency": "USD",
            "amount": "100.5",
            "transactionType": "TRANSFER",
            "note": "Bulk Quote Item 1: Invoice 456"
        },
        {
            "quoteId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
            "to": {
                "idType": "MSISDN",
                "idValue": "987654321"
            },
            "amountType": "SEND",
            "currency": "USD",
            "amount": "50",
            "transactionType": "TRANSFER",
            "note": "Bulk Quote Item 2: Salary Advance"
        }
    ]
}'














curl -X POST \
  http://localhost:4001/bulkTransfers \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
    "bulkTransferId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
    "bulkQuoteId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
    "homeTransactionId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
    "from": {
        "displayName": "Bulk Sender DFSP A",
        "idType": "MSISDN", 
        "idValue": "123456789"
    },
    "individualTransfers": [
        {
            "transferId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
            "to": {
                "idType": "PERSONAL_ID",
                "idValue": "22912345678"
            },
            "amountType": "SEND",
            "currency": "USD",
            "amount": "100.5",
            "transactionType": "TRANSFER",
            "note": "Bulk Payment Item 1: Invoice 456",
            "ilpPacket": "AYIE6QAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggSwZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pTURGTFFrdGFTamxJUkROTk1rUk9WRGRCUzFjME5UVlFNVGNpTENKeGRXOTBaVWxrSWpvaU1ERkxRa3RhU2tGTk1EWXdSemRDVkZjMFZsQTNNa0ZOTUU0aUxDSndZWGxsWlNJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJbEJGVWxOUFRrRk1YMGxFSWl3aWNHRnlkSGxKWkdWdWRHbG1hV1Z5SWpvaU1qSTVNVEl6TkRVMk56Z2lMQ0ptYzNCSlpDSTZJblJsYzNScGJtZDBiMjlzYTJsMFpHWnpjQ0lzSW1WNGRHVnVjMmx2Ymt4cGMzUWlPbnNpWlhoMFpXNXphVzl1SWpwYmV5SnZabVpwWTJsaE16TWlPaTAyTlRJMU9UTTFNUzQ1TmpnM05EWXdNVFFzSW5abGJtbGhiVjgzWlRFaU9tWmhiSE5sTENKbGMzUmlJanBtWVd4elpTd2lURzl5WlcwMk9EVWlPblJ5ZFdVc0ltbHdjM1Z0WHpraU9pMDJORFUwTXprd01pNHlNelk1TVRRME5Dd2laWGhqWDE4aU9uUnlkV1VzSW10bGVTSTZJbVZwZFNJc0luWmhiSFZsSWpvaWNHRnlhV0YwZFhJZ1pXeHBkQ0J2Wm1acFkybGhJbjBzZXlKa2IyeHZjbDlrSWpvdE56VTVOamc1TkRZc0lreHZjbVZ0TnpBaU9uUnlkV1VzSW10bGVTSTZJbk5wZENCaGJHbHhkV0VpTENKMllXeDFaU0k2SWtWNFl5SjlYWDE5TENKd1pYSnpiMjVoYkVsdVptOGlPbnNpWTI5dGNHeGxlRTVoYldVaU9uc2labWx5YzNST1lXMWxJam9pVFdsamFHRmxiQ0lzSW0xcFpHUnNaVTVoYldVaU9pSk9JaXdpYkdGemRFNWhiV1VpT2lKTVpXVWlmU3dpWkdGMFpVOW1RbWx5ZEdnaU9pSXhPVEl5TFRFd0xUQTFJbjE5TENKd1lYbGxjaUk2ZXlKd1lYSjBlVWxrU1c1bWJ5STZleUp3WVhKMGVVbGtWSGx3WlNJNklrMVRTVk5FVGlJc0luQmhjblI1U1dSbGJuUnBabWxsY2lJNklqRXlNelExTmpjNE9TSXNJbVp6Y0Vsa0lqb2lhWFJyTFd4dllXUXRkR1Z6ZEMxa1puTndJbjBzSW01aGJXVWlPaUpLYjJodUlFUnZaU0o5TENKaGJXOTFiblFpT25zaWMybHVkRGM0TVNJNlptRnNjMlVzSW1OMWNuSmxibU41SWpvaVdFOUdJaXdpWVcxdmRXNTBJam9pTVRBd0luMHNJblJ5WVc1ellXTjBhVzl1Vkhsd1pTSTZleUp6WTJWdVlYSnBieUk2SWxSU1FVNVRSa1ZTSWl3aWFXNXBkR2xoZEc5eUlqb2lVRUZaUlZJaUxDSnBibWwwYVdGMGIzSlVlWEJsSWpvaVEwOU9VMVZOUlZJaWZTd2laWGh3YVhKaGRHbHZiaUk2SWpJd01qVXRNVEl0TURWVU1EWTZNRGM2TXpjdU5qY3dXaUo5AA",
            "condition": "6el1iYAyOxEt83DFhnEJQU550fUFfckbuBVS4GChqEc"
        },
        {
            "transferId": "'$(python3 -c "import uuid; print(uuid.uuid4())")'",
            "to": {
                "idType": "MSISDN",
                "idValue": "987654321"
            },
            "amountType": "SEND",
            "currency": "USD",
            "amount": "50",
            "transactionType": "TRANSFER",
            "note": "Bulk Payment Item 2: Salary Advance",
            "ilpPacket": "AYIE6QAAAAAAAABkLGcudGVzdGluZ3Rvb2xraXRkZnNwLnBlcnNvbmFsX2lkLjIyOTEyMzQ1Njc4ggSwZXlKMGNtRnVjMkZqZEdsdmJrbGtJam9pTURGTFFrdGFTamxJUkROTk1rUk9WRGRCUzFjME5UVlFNVGNpTENKeGRXOTBaVWxrSWpvaU1ERkxRa3RhU2tGTk1EWXdSemRDVkZjMFZsQTNNa0ZOTUU0aUxDSndZWGxsWlNJNmV5SndZWEowZVVsa1NXNW1ieUk2ZXlKd1lYSjBlVWxrVkhsd1pTSTZJbEJGVWxOUFRrRk1YMGxFSWl3aWNHRnlkSGxKWkdWdWRHbG1hV1Z5SWpvaU1qSTVNVEl6TkRVMk56Z2lMQ0ptYzNCSlpDSTZJblJsYzNScGJtZDBiMjlzYTJsMFpHWnpjQ0lzSW1WNGRHVnVjMmx2Ymt4cGMzUWlPbnNpWlhoMFpXNXphVzl1SWpwYmV5SnZabVpwWTJsaE16TWlPaTAyTlRJMU9UTTFNUzQ1TmpnM05EWXdNVFFzSW5abGJtbGhiVjgzWlRFaU9tWmhiSE5sTENKbGMzUmlJanBtWVd4elpTd2lURzl5WlcwMk9EVWlPblJ5ZFdVc0ltbHdjM1Z0WHpraU9pMDJORFUwTXprd01pNHlNelk1TVRRME5Dd2laWGhqWDE4aU9uUnlkV1VzSW10bGVTSTZJbVZwZFNJc0luWmhiSFZsSWpvaWNHRnlhV0YwZFhJZ1pXeHBkQ0J2Wm1acFkybGhJbjBzZXlKa2IyeHZjbDlrSWpvdE56VTVOamc1TkRZc0lreHZjbVZ0TnpBaU9uUnlkV1VzSW10bGVTSTZJbk5wZENCaGJHbHhkV0VpTENKMllXeDFaU0k2SWtWNFl5SjlYWDE5TENKd1pYSnpiMjVoYkVsdVptOGlPbnNpWTI5dGNHeGxlRTVoYldVaU9uc2labWx5YzNST1lXMWxJam9pVFdsamFHRmxiQ0lzSW0xcFpHUnNaVTVoYldVaU9pSk9JaXdpYkdGemRFNWhiV1VpT2lKTVpXVWlmU3dpWkdGMFpVOW1RbWx5ZEdnaU9pSXhPVEl5TFRFd0xUQTFJbjE5TENKd1lYbGxjaUk2ZXlKd1lYSjBlVWxrU1c1bWJ5STZleUp3WVhKMGVVbGtWSGx3WlNJNklrMVRTVk5FVGlJc0luQmhjblI1U1dSbGJuUnBabWxsY2lJNklqRXlNelExTmpjNE9TSXNJbVp6Y0Vsa0lqb2lhWFJyTFd4dllXUXRkR1Z6ZEMxa1puTndJbjBzSW01aGJXVWlPaUpLYjJodUlFUnZaU0o5TENKaGJXOTFiblFpT25zaWMybHVkRGM0TVNJNlptRnNjMlVzSW1OMWNuSmxibU41SWpvaVdFOUdJaXdpWVcxdmRXNTBJam9pTVRBd0luMHNJblJ5WVc1ellXTjBhVzl1Vkhsd1pTSTZleUp6WTJWdVlYSnBieUk2SWxSU1FVNVRSa1ZTSWl3aWFXNXBkR2xoZEc5eUlqb2lVRUZaUlZJaUxDSnBibWwwYVdGMGIzSlVlWEJsSWpvaVEwOU9VMVZOUlZJaWZTd2laWGh3YVhKaGRHbHZiaUk2SWpJd01qVXRNVEl0TURWVU1EWTZNRGM2TXpjdU5qY3dXaUo5AA",
            "condition": "6el1iYAyOxEt83DFhnEJQU550fUFfckbuBVS4GChqEc"
        }
    ]
}'











