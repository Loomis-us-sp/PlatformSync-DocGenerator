# Transactions

## Request for Transactions

The Pull API for requesting transactions has not yet been defined.

## Response for Transactions

```json
{
    "Total": 5434,
    "Page": 0,
    "PageSize": 1000,
    "Transactions": [
        {
            "SerialNumber": "UT01234",
            "RetrievedOn": "2018-05-01T13:24:00.000000",
            "TransactionDateTime": "2018-05-01T13:20:00.000000",
            "UserName": "ROSE",
            "TransactionType": "CashTransaction",
            "Amount": 240,
            "Denominations": [
                {
                    "UnitValue": 20,
                    "Count": 8,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 5,
                    "Count": 12,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 1,
                    "Count": 20,
                    "Currency": "USD"
                }
            ],
            "Register": "Register 1",
            "ChangePurchaseNumber": "ASD1234",
            "DepositReferenceNumber": "JGH2345",
        }
    ]
}
```

**Response Properties**

Property Name | More Information
------------- | ----------------
Total | Total number of transactions included in this (and possibly subsequent) page(s)
Page | The current page (zero-based index)
PageSize | The number of transaction included in this page (for the Push API, corresponds to the `MaxBatchSize` definition)
Transactions | Transaction Object list

**Transaction Object**

Property Name | More Information
------------- | ----------------
SerialNumber | Serial number of the safe that the transaction occured on
RetrievedOn | Datetime of when the transaction was retrieved from the safe (In CST/CDT)
TransactionDateTime | Datetime of when the transaction occured on the safe (In local time)
UserName | Logged in user that performed the transaction
TransactionType | Type of transaction performed.  Will be one of `TransactionType`'s outlined below.
Amount | Total cash value of the transaction
Denominations | If the transaction was a validated drop, it will contain a list of bills.  For more information, see "Denomination Object" table below.
Register | Which register, if any, that was used for the transaction
ChangePurchaseNumber | Change purchase number, if any, that was used for the transaction
DepositReferenceNumber | Deposit Reference Number, if any, that was used for the transaction

**Transaction Types**

- Validated Drop = 1
- Manual Drop = 2
- Change Purchase = 3
- End of Day = 4
- End of Shift = 5
- Servicing = 6

**Denomination Object**

Property Name | More Information
------------- | ----------------
UnitValue | Value of each bill
Count | Number of bills
Currency | Currency of the bill
