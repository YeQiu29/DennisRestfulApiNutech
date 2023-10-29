# Module Transcation

## Create Balance

Endpoint : GET /api/contacts

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Get Balance Berhasil",
  "data": {
    "balance": 1000000
  }
}
```

Response Body (Failed, 108) :

```json
{
  "status": 108,
  "message": "Token tidak tidak valid atau kadaluwarsa",
  "data": null
}
```

## Top Up

Endpoint : POST /api/contacts/{idContact}

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "top_up_amount": 1000000
}
```

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Top Up Balance berhasil",
  "data": {
    "balance": 2000000
  }
}
```

Response Body (Failed, 102) :

```json
{
  "status": 102,
  "message": "Paramter amount hanya boleh angka dan tidak boleh lebih kecil dari 0",
  "data": null
}
```

Unauthorized (Failed, 108) :
```json
{
  "status": 108,
  "message": "Token tidak tidak valid atau kadaluwarsa",
  "data": null
}
```

## Transaction

Endpoint : POST /api/contacts/{idContact}

Request Header :

- X-API-TOKEN : Token (Mandatory)

Request Body :

```json
{
  "service_code": "PULSA"
}
```

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Transaksi berhasil",
  "data": {
    "invoice_number": "INV17082023-001",
    "service_code": "PLN_PRABAYAR",
    "service_name": "PLN Prabayar",
    "transaction_type": "PAYMENT",
    "total_amount": 10000,
    "created_on": "2023-08-17T10:10:10.000Z"
  }
}
```

Response Body (Failed, 102) :

```json
{
  "status": 102,
  "message": "Service ataus Layanan tidak ditemukan",
  "data": null
}
```

Unauthorized (Failed, 108) :
```json
{
  "status": 108,
  "message": "Token tidak tidak valid atau kadaluwarsa",
  "data": null
}
```

## Transaction History

Endpoint : GET /api/contacts/history

Query Param :

- offset : Integer, contact first name or last name, using like query, optional
- limit : Integer, contact phone, using like query, optional
- page : Integer, start from 0, default 0
- size : Integer, default 10

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Get History Berhasil",
  "data": {
    "offset": 0,
    "limit": 3,
    "records": [
      {
        "invoice_number": "INV17082023-001",
        "transaction_type": "TOPUP",
        "description": "Top Up balance",
        "total_amount": 100000,
        "created_on": "2023-08-17T10:10:10.000Z"
      },
      {
        "invoice_number": "INV17082023-002",
        "transaction_type": "PAYMENT",
        "description": "PLN Pascabayar",
        "total_amount": 10000,
        "created_on": "2023-08-17T11:10:10.000Z"
      },
      {
        "invoice_number": "INV17082023-003",
        "transaction_type": "PAYMENT",
        "description": "Pulsa Indosat",
        "total_amount": 40000,
        "created_on": "2023-08-17T12:10:10.000Z"
      }
    ]
  }
}
```

Response Body (Failed, 108) :

```json
{
  "status": 108,
  "message": "Token tidak tidak valid atau kadaluwarsa",
  "data": null
}
```