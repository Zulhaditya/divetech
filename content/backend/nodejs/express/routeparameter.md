---
title: Route Paramater
tags:
  - express
---

- Saat membuat aplikasi Web API atau RESTful API, kadang kita sering menyimpan parameter dalam URL Path, misalkan /products/{idProduct}, atau /categories/{idCategory}, dan lain-lain.
- ExpressJS mendukung penambahan parameter dalam route path, dengan menggunakan prefix (:)
- Semua data parameter bisa ditambahkan regex jika kita mau, contoh /products/:id(\\d+), artinya kita menambahkan parameter id, dimana id tersebut harus digit.
- Data route parameter secara otomatis bisa kita ambil sebagai attribute di req.params
- https://expressjs.com/en/4x/api.html#req.params

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/products/:id", (req, res) => {
  const idProduct = req.params.id;
  res.send(`Product: ${idProduct}`);
});

app.get("/categories/:id(\\d+)", (req, res) => {
  const idCategory = req.params.id;
  res.send(`Category: ${idCategory}`);
});

app.get("/seller/:idSeller/products/:idProduct", (req, res) => {
  req.params.idSeller;
  req.params.idProduct;
});

test("Test Route Parameter", async () => {
  let response = await request(app).get("/products/inayah");
  expect(response.text).toBe("Product: inayah");

  response = await request(app).get("/products/salah");
  expect(response.text).toBe("Product: salah");

  response = await request(app).get("/categories/123");
  expect(response.text).toBe("Category: 123");

  response = await request(app).get("/categories/salah");
  expect(response.status).toBe(404);
});
```

**Selanjutnya :** [Route Function](routefunction.md)
