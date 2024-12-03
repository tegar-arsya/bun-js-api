To install dependencies:
```sh
bun install
```

To run:
```sh
bun run dev
```

open http://localhost:3000


-- Active: 1727230758167@@127.0.0.1@3306@api-bun
# RESFUL API BUN JS DAN HONO


# Instalasi :
- install bun di web resminya
## buat project, misal dengan bun hono dengan cara :
- bun create hono (nama project)
- lalu pilih bun dan bun 
## jika ingin menambahkan zod maka install package dengan cara :
- bun add zod

## jika ingin menambahkan prisma di project bisa dengan cara :
- bun add -d prisma
- bun add @prisma/client

## jika ingin menambahkan logger atau logging bisa menggunakan winston :
- bun add winston


## instalasi prisma ke dalam project :
- bunx prisma init --database-provider mysql
- (karena default menggunakan postgre maka disini saya menggunakan mysql)


## untuk migrasi ke database :
- bunx prisma migrate dev

## DATA USER

 1. username
 3. password
 4. Token (optional)
 
 > Anda bisa berexplor data user yang akan di masukkan, saya menambahkan role tetapi ini nantinya masuk pada model, secara alurnya role memiliki.
 > 
 ## USER API
 
 ## Register User
    Enpoint: POST /api/users
    
Request Body:
```json
{
  "username" : "tegar",
  "password" : "tegar123",
  "name" : "Tegar Arsyadani"
}
```

Response Body (Sukses):
```json
{
    "data" : {
    "username" : "tegar",
    "name" : "Tegar Arsyadani"
    }
}
```

Response Body (Failed) :

```json
{
  "errors" : "Username must not blank, ..."
}
```

 ## Login User
    Endpoint : POST /api/users/login

 Request Body : 

```json
{
  "username" : "tegar",
  "password" : "tegar123"
}
```  

Response Body (Success) :

```json
{
  "data" : {
    "username" : "tegar",
    "name" : "Tegar Arsyadani",
    "token" : "token"
  }
}
```
 ## Update User

    Endpoint : PATCH /api/users/current

Request Header :
- Authorization : token

Request Body :

```json
{
  "name" : "Kalo mau update nama",
  "password" : "kalo mau update password"
}
```

Response Body (Success) :

```json
{
  "data" : {
    "username" : "tegar",
    "name" : "Tegar Arsyadani"
  }
}
```
 ## Get User
    Endpoint : GET /api/users/current

Request Header :
- Authorization : token

Response Body (Success) :

```json
{
  "data" : {
    "username" : "tegar",
    "name" : "Tegar Arsyadani"
  }
}
```

 ## Logout User
    Endpoint : DELETE /api/users/current

Request Header :
- Authorization : token

Response Body (Success) :

```json
{
  "data" : true
}
```





## Kontak Data

 1. firstName
 2. lastName
 3. Email
 4. Phone
 
 ## Kontak API
 
 ## Create kontak
 Endpoint : POST /api/contacts

Request Header :
- Authorization : token

Request Body :

```json
{
  "first_name" : "Nama Depan",
  "last_name" : "Nama Belakang",
  "email" : "tg@gmail.com",
  "phone" : "08999999999"
}
```

Response Body

```json
{
  "data": {
    "id": 1,
    "first_name": "Nama Depan",
    "last_name": "Nama Belakang",
    "email": "tg@gmail.com",
    "phone": "08999999999"
  }
}
```
 ## Update Kontak

 Endpoint : PUT /api/contacts/{idContact}

Request Header :
- Authorization : token

Request Body :

```json
{
    "first_name": "Nama Depan",
    "last_name": "Nama Belakang",
    "email": "eko@gmail.com",
    "phone": "08999999999"
  }
```

Response Body

```json
{
  "data": {
    "id": 1,
    "first_name": "Nama Depan",
    "last_name": "Nama Belakang",
    "email": "eko@gmail.com",
    "phone": "08999999999"
  }
}
```

 ## Get Kontak

 Endpoint : GET /api/contacts/{idContact}

Request Header :
- Authorization : token

Response Body

```json
{
  "data": {
    "id": 1,
    "first_name": "Nama Depan",
    "last_name": "Nama Belakang",
    "email": "eko@gmail.com",
    "phone": "08999999999"
  }
}
```
 ## Search Kontak

 Endpoint : GET /api/contacts

Request Header :
- Authorization : token

Query Parameter :
- name : string, search ke first_name atau last_name
- email : string, search ke email
- phone : string, search ke phone
- page : number, default 1
- size : number, default 10

Response Body

```json
{
  "data" : [
    {
      "id": 1,
      "first_name": "Nama Depan",
      "last_name": "Nama Belakang",
      "email": "eko@gmail.com",
      "phone": "08999999999"
    },
    {
      "id": 2,
      "first_name": "Nama Depan",
      "last_name": "Nama Belakang",
      "email": "eko@gmail.com",
      "phone": "08999999999"
    }
  ],
  "paging" : {
    "current_page" : 1,
    "total_page" : 10,
    "size" : 10
  }
}
```
 ## Remove
 
 Endpoint : DELETE /api/contacts/{idContact}

Request Header :
- Authorization : token

Response Body

```json
{
  "data" : true
}
```
 ## Data Alamat Kontak
 
 1. Jalan
 2. Kota
 3. Provinsi
 4. Negara
 5. Kode Pos

 ## Alamat API
 ## Create Alamat

 Endpoint : POST /api/contacts/{idContact}/addresses

Request Header :
- Authorization : token

Request Body :

```json
{
  "jalan" : "jalan",
  "kota" : "kota",
  "provinsi" : "provinsi",
  "negara" : "negara",
  "kode_post" : "234234"
}
```

Response Body :

```json
{
  "data" : {
    "id" : 1,
    "jalan" : "jalan",
    "kota" : "kota",
    "provinsi" : "provinsi",
    "negara" : "negara",
    "kode_post" : "234234"
  }
}
```


 ## Update Alamat

 Endpoint : PUT /api/contacts/{idContact}/addresses/{idAddress}

Request Header :
- Authorization : token

Request Body :

```json
{
  "jalan" : "jalan",
  "kota" : "kota",
  "provinsi" : "provinsi",
  "negara" : "negara",
  "kode_post" : "234234"
}
```

Response Body :

```json
{
  "data" : {
    "id" : 1,
    "jalan" : "jalan",
    "kota" : "kota",
    "provinsi" : "provinsi",
    "negara" : "negara",
    "kode_post" : "234234"
}
```
 ## Get Alamat

 Endpoint : GET /api/contacts/{idContact}/addresses/{idAddress}

Request Header :
- Authorization : token

Response Body :

```json
{
  "data" : {
    "id" : 1,
    "jalan" : "jalan",
    "kota" : "kota",
    "provinsi" : "provinsi",
    "negara" : "negara",
    "kode_post" : "234234"
  }
}
```

 ## Daftar Alamat
 Endpoint : GET /api/contacts/{idContact}/addresses

Request Header :
- Authorization : token

Response Body :

```json
{
  "data": [
    {
      "id": 1,
      "jalan" : "jalan",
      "kota" : "kota",
      "provinsi" : "provinsi",
      "negara" : "negara",
      "kode_post" : "234234"
    },
    {
      "id": 2,
      "jalan" : "jalan",
      "kota" : "kota",
      "provinsi" : "provinsi",
      "negara" : "negara",
      "kode_post" : "234234"
    }
  ]
}
```
 ## Remove Alamat 

 Endpoint : DELETE /api/contacts/{idContact}/addresses/{idAddress}

Request Header :
- Authorization : token

Response Body :

```json
{
  "data": true
}
```