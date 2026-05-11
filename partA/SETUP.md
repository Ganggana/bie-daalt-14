# Part A — Setup

## Сонгосон API
**JSONPlaceholder** — https://jsonplaceholder.typicode.com

## Brief
JSONPlaceholder нь fake REST API бөгөөд API testing, prototype, Postman/Newman дадлагад тохиромжтой. Энэ лабораторид posts resource дээр GET, GET by ID, POST, PUT/PATCH, DELETE болон negative/error case request-үүдийг шалгана.

## Base URL
```text
{{baseUrl}}
```

Development environment-д:
```text
https://jsonplaceholder.typicode.com
```

## Auth
Auth шаардлагагүй. Authorization header/token ашиглахгүй.

## Эхний амжилттай request
```http
GET {{baseUrl}}/posts/1
```

Expected status:
```text
200 OK
```

## Notes
- Бүх request URL-д `{{baseUrl}}` variable ашигласан.
- Token/secret байхгүй тул repository-д sensitive мэдээлэл commit хийгдээгүй.
