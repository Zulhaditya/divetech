---
title: User API Spec
tags:
  - api
---
# Register User API

## Endpoint : POST /api/users

## Request Body :

```json
{
  "username": "nay",
  "password": "rahasia",
  "name": "Inayah Wulandari"
}
```

## Response Body Success :

```json
{
  "data": {
    "username": "nay",
    "name": "Inayah Wulandari"
  }
}
```

## Response Body Error :

```json
{
  "errors": "Username already registered"
}
```

# Login User API

## Endpoint : POST /api/users/login

## Request Body :

```json
{
  "username": "nay",
  "password": "rahasia"
}
```

## Response Body Success :

```json
{
  "data": {
    "token": "unique-token"
  }
}
```

## Response Body Error :

```json
{
  "errors": "Username or Password wrong"
}
```

# Update User API

## Endpoint : PATCH /api/users/current

## Headers :

- Authorization : token

## Request Body :

```json
{
  "name": "Inayah Wulandari Lagi", // optional
  "password": "new password" // optional
}
```

## Response Body Success :

```json
{
  "data": {
    "username": "nay",
    "name": "Inayah Wulandari Lagi"
  }
}
```

## Response Body Error :

```json
{
  "errors": "Name length max 100"
}
```

# Get User API

## Endpoint : GET /api/users/current

## Headers :

- Authorization : token

## Response Body Success :

```json
{
  "data": {
    "username": "nay",
    "name": "Inayah Wulandari"
  }
}
```

## Response Body Error :

```json
{
  "errors": "Unauthorized"
}
```

# Logout User API

## Endpoint : DELETE /api/users/logout

## Headers :

- Authorization : token

## Response Body Success :

```json
{
  "data": "OK"
}
```

## Response Body Error :

```json
{
  "errors": "Unauthorized"
}
```

**Selanjutnya :** [Contact API Spec](contactapispec.md)