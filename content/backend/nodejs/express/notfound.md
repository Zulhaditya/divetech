---
title: Not Found
tags:
  - express
---

- Saat user melakukan request ke URL yang tidak tersedia, maka secara default ExpressJS akan mengembalikan halaman 404.
- Kadang kita ingin membuat halaman 404 sendiri.
- Pada kasus ini, kita bisa menambahkan middleware di posisi paling akhir.
- Middleware tersebut akan dipanggil jika memang tidak terdapat route yang tersedia untuk route path yang diakses.

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.send(`Hello Response`);
});

app.use((req, res, next) => {
  res.status(404).send(`404 Not Found Oy`);
});

test("Test Response", async () => {
  const response = await request(app).get("/");
  expect(response.text).toBe("Hello Response");
});

test("Test Response Not Found", async () => {
  const response = await request(app).get("/halaman-tidak-ada");
  expect(response.text).toBe("404 Not Found Oy");
});
```
