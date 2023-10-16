---
title: Route Path
tags:
  - express
---

- Sebelumnya kita telah belajar melakukan routing dengan HTTP method sesuai dengan yang kita mau.
- Sekarang kita akan bahas lebih detail tentang Route Path-nya.
- Sebelumnya, route path yang digunakan tidak dinamis. ExpressJS mendukung route path yang dinamis dengan cara menggunakan route path string patterns atau regex.

# Path to Regex

- ExpressJS menggunakan library Path to Regex untuk melakukan routing berupa regex.
- Kita bisa lihat detail cara melakukan regex pada halaman dokumentasi library.
- https://www.npmjs.com/package/path-to-regexp
- Untuk melakukan pengetesan kita bisa menggunakan website
- https://forbeslindesay.github.io/express-route-tester

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/products/*.json", (req, res) => {
  res.send(req.originalUrl);
});

app.get("/categories/*(\\d+).json", (req, res) => {
  res.send(req.originalUrl);
});

test("Test Route Path", async () => {
  let response = await request(app).get("/products/inayah.json");
  expect(response.text).toBe("/products/inayah.json");

  response = await request(app).get("/products/salah.json");
  expect(response.text).toBe("/products/salah.json");

  response = await request(app).get("/categories/123.json");
  expect(response.text).toBe("/categories/123.json");

  response = await request(app).get("/categories/salah.json");
  expect(response.status).toBe(404);
});
```

**Selanjutnya :** [Route Parameter](routeparameter.md)
