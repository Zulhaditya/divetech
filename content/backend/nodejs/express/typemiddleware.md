---
title: Type Middleware
tags:
  - express
---

Di ExpressJS, terdapat beberapa jenis middleware yaitu:

- Application-level middleware
- Router-level middleware
- Error-handling middleware
- Built-in middleware
- Third-party middleware

# Application-Level Middleware

- Middleware ini digunakan di object application, sebelumnya kita sudah menggunakan Application-Level middleware, dengan cara menggunakan function app.use(middleware).
- Saat kita menggunakan Application-Level Middleware, maka secara otomatis MIddleware tersebut akan dipanggil di semua route.
- Jika kita ingin menggunakan Middleware hanya untuk route path tertentu, kita bisa tambahkan route pattern ketika ingin menggunakan app.use(), misalkan app.use("/products\*", middleware).
- https://expressjs.com/en/4x/api.html#app.use

# Router-Level Middleware

- Yaitu middleware yang ditambahkan pada object router yang kita buat menggunakan express.router().
- Middleware ini secara otomatis akan dipanggil ketika request masuk ke router ini.
- Sama seperti Application-Level Middleware, jika kita ingin middleware dipanggil pada route path tertentu, kita juga bisa menambahkan route pattern ketika menggunakan middleware menggunakan router.use(path, middleware).
- https://expressjs.com/en/4x/api.html#router.use

# Error-Handling Middleware

- Yaitu middleware yang dipanggil ketika terjadi error di aplikasi kita (throw Error).
- Cara penggunaannya mirip dengan Application-Level Middleware, yang membedakan adalah function callback-nya memilki empat parameter, yaitu error, request, response dan next.
- Object error akan secara otomatis terisi oleh data Error yang terjadi di aplikasi kita.
- Middleware ini sangat cocok, ketika kita ingin menampilkan tampilan yang berbeda ketika terjadi error di aplikasi kita.

# Built-in Middleware

- ExpressJS menggunakan middleware untuk melakukan pemrosesan request dan response, termasuk Built-in Middleware, yaitu middleware yang sudah terdapat secara otomatis di ExpressJS.
- express.json(), yaitu middleware yang melakukan parsing request body menjadi Javascript object.
- express.text(), yaitu middleware yang melakukan parsing request body menjadi string.
- express.raw(), yaitu middleware yang digunakan untuk parsing request body menjadi buffer.
- express.urlencoded(), yaitu middleware yang digunakan untuk parsing request body form menjadi object.
- express.static(), yaitu middleware yang digunakan untuk melayani file static.

# Third-party Middleware

- Yaitu middleware buatan orang lain yang kita gunakan.
- Untuk menggunakannya, kita perlu menambahkan dependency middlewarenya terlebih dahulu.

**Selanjutnya :** [Request Body](requestbody.md)
