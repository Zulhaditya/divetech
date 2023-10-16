---
title: Cookie
tags:
  - express
---

- Dalam HTTP, salah satu fitur yang biasa digunakan untuk pertukaran data dari server dan client adalah Cookie.
- Banyak yang menggunakan Cookie sebagai session misalnya.
- Sayangnya, secara default, ExpressJS tidak mendukung Cookie, kita bisa menggunakan Third-party Middleware untuk mendukung Cookie ini.

# Cookie Parser

- Cookie Parser adalah salah satu Third-party middleware yang digunakan untuk mendukung fitur Cookie, dimana dengan Cookie Parser, kita secara otomatis menyimpan data Cookie, atau mengambil data Cookie.
- https://npmjs.com/package/cookie-parser

## Menulis Cookie

- Untuk menulis Cookie, kita bisa tambahkan di response, dengan method res.cookie(key, value, setting).
- https://expressjs.com/en/4x/api.html#res.cookie
- Untuk menghapus cookie bisa gunakan res.clearCookie(key, setting)
- https://expressjs.com/en/4x/api.html#res.clearCookie

```js
import cookieParser from "cookie-parser";
import express from "express";
import request from "supertest";

const app = express();
app.use(cookieParser());
app.use(express.json());

app.get("/", (req, res) => {
  const name = req.cookies["name"];
  res.send(`Hello ${name}`);
});

app.post("/login", (req, res) => {
  const name = req.body.name;
  res.cookie("Login", name, { path: "/" });
  res.send(`Hello ${name}`);
});

test("Test Cookie Read", async () => {
  const response = await request(app)
    .get("/")
    .set("Cookie", "name=Inayah;author=Wulandari");

  expect(response.text).toBe("Hello Inayah");
});

test("Test Cookie Write", async () => {
  const response = await request(app).post("/login").send({ name: "Inayah" });

  expect(response.get("Set-Cookie").toString()).toBe("Login=Inayah; Path=/");
  expect(response.text).toBe("Hello Inayah");
});
```

**Selanjutnya :** [Signed Cookie](signedcookie.md)
