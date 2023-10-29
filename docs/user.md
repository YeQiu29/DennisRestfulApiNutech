# User API Spec

## Register User

Endpoint : POST /api/users

Request Body :

```json
{
  "email": "user@nutech-integrasi.com",
  "first_name": "User",
  "last_name": "Nutech",
  "password": "abcdef1234"
}
```

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Registrasi berhasil silahkan login",
  "data": null
}
```

Response Body (Failed, 102) :

```json
{
  "status": 102,
  "message": "Paramter email tidak sesuai format",
  "data": null
}
```

## Login User

Endpoint : POST /api/auth/login

Request Body :

```json
{
  "email": "user@nutech-integrasi.com",
  "password": "abcdef1234"
}
```

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Login Sukses",
  "data" : {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjoiNTRVdXRjYTdCS0ZPX0ZUZGZ1bXlJem9zSTRKa1VxUGZVZ0ROSTUwelRTQlo2aHoyY0hKZ1VMb1loM09HUUd0ekQxV3dTX194aHBNZTE2SGFscVRzcEhjS21UclJ3S2FYYmZob3AzdzFFUHJ2NFdBQmk1c0RpdV9DSnZTSWt2MDFTbEU0QU5pbVB0bUx5azZoUzlOalVQNEZaVVpfRVBtcEk4Y3pNc3ZWa2JFPSIsImlhdCI6MTYyNjkyODk3MSwiZXhwIjoyNTU2MTE4Nzk4fQ.9C9NvhZYKivhGWnrjo4Wr1Rv-wur1wCm0jqfK9XDD8U"
  }
}
```

Response Body (Failed, 102) :

```json
{
  "status": 102,
  "message": "Paramter email tidak sesuai format",
  "data": null
}
```

Unauthorized (Failed, 103)
```json
{
  "status": 103,
  "message": "Username atau password salah",
  "data": null
}

```

## Profile

Endpoint : GET /api/users/current

Request Header :

- X-API-TOKEN : Token (Mandatory) 

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Sukses",
  "data": {
    "email": "user@nutech-integrasi.com",
    "first_name": "User",
    "last_name": "Nutech",
    "profile_image": "https://yoururlapi.com/profile.jpeg"
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

## Profile Update

Endpoint : PATCH /api/users/current

Request Header :

- X-API-TOKEN : Token (Mandatory)

Request Body : 

```json
{
  "first_name": "User Edited",
  "last_name": "Nutech Edited"
}
```

Response Body (Success) :

```json
{
  "status": 0,
  "message": "Update Pofile berhasil",
  "data": {
    "email": "user@nutech-integrasi.com",
    "first_name": "User Edited",
    "last_name": "Nutech Edited",
    "profile_image": "https://yoururlapi.com/profile.jpeg"
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

## Logout User

Endpoint : DELETE /api/auth/logout

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "data" : "OK"
}
```
