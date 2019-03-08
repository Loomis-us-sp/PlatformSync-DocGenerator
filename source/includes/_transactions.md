# Transactions

## Payload

```json
{
    "Metadata": {
        "MessageId": "2d603c44-c52c-4c30-9ea3-17d580e1d149"
    },
    "Transactions": [
        {
            "PickupGroupId": 232,
            "SerialNumber": "UT82233",
            "RetrievedOn": "2018-05-11T17:29:32.4668424-05:00",
            "TransactionDateTime": "2018-05-10T17:39:57.5717919",
            "UserName": "1UAUOVPITN4",
            "TransactionType": "ValidatedCashIn",
            "Amount": 2203.0,
            "Denominations": [
                {
                    "UnitValue": 1.0,
                    "Count": 20,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 2.0,
                    "Count": 4,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 5.0,
                    "Count": 19,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 10.0,
                    "Count": 7,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 20.0,
                    "Count": 23,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 50.0,
                    "Count": 9,
                    "Currency": "USD"
                },
                {
                    "UnitValue": 100.0,
                    "Count": 11,
                    "Currency": "USD"
                }
            ],
            "Register": "REGISTER_3",
            "ChangePurchaseNumber": "5009188254",
            "DepositReferenceNumber": "021105"
        }
    ]
}
```

**Transaction Object Properties**

Property Name | More Information
------------- | ----------------
PickupGroupId | Groups transactions to a servicing
SerialNumber | Serial number of the safe that the transaction occured on
RetrievedOn | Datetime of when the transaction was retrieved from the safe (Includes GMT Offset)
TransactionDateTime | Datetime of when the transaction occured on the safe (In local time; will not include GMT offset)
UserName | Logged in user that performed the transaction
TransactionType | Type of transaction performed.  Will be one of `TransactionType`'s outlined below.
Amount | Total cash value of the transaction (if applicable).
Denominations | If the transaction was a validated drop or dispense, it will contain a list of bills or coin by denomination.  For more information, see "Denomination Object" table below (if applicable).
Register | Which register, if any, that was used for the transaction (if properly configured on the safe).
ChangePurchaseNumber | Change purchase number, if any, that was used for the transaction (if properly configured on the safe).
DepositReferenceNumber | Deposit Reference Number, if any, that was used for the transaction (if properly configured on the safe).

**Transaction Types**

- CashIn
- Servicing
- ChangeRequest
- ManualCashTransaction
- CoinDispenseBuyChange
- NoteDispenseBuyChange
- CoinDispense
- NoteDispense
- TubeRemoved
- TubeLoaded
- EndOfDay
- Placeholder
- TubeDumped

**Denomination Object**

Property Name | More Information
------------- | ----------------
UnitValue | Value of each bill or coin
Count | Number of bills or coin
Currency | Currency of the bill or coin
