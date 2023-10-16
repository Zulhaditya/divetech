---
title: Signed Cookie
tags:
  - express
---

- Salah satu kelemahan ketika menyimpan data di Cookie adalah, Cookie bisa dimodifikasi oleh Client, misalkan kita modifikasi Cookie di browser kita.
- Salah satu cara untuk menjaga agar Cookie tidak dimodifikasi adalah dengan menambahkan signature pada cookie kita.
- Setiap nilai Cookie memiliki signature, dimana ketika Cookie diubah, otomatis Signature tidak akan sama lagi, dan secara otomatis value cookie tidak dianggap valid lagi.
- Fitur ini tersedia di cookie parser dengan nama signed cookie.
- Kita wajib menyebutkan Cookie mana yang ingin di signed, ketika kita membuat Cookie di response.
- Selain itu kita perlu memasukkan Secret Key untuk digunakan ketika proses pembuatan signature, pastikan secret-nya aman dan tidak mudah untuk ditebak.

# Membaca Signed Cookie

- Jika kita membuat Cookie sebagai Signed Cookie, maka untuk membacanya, jangan menggunakan req.cookies, melainkan harus menggunakan req.signedCookies
- https://expressjs.com/en/4x/api.html#req.signedCookies

```js
import cookieParser from "cookie-parser";
import express from "express";
import request from "supertest";

const app = express();
app.use(cookieParser("CONTOHRAHASIA"));
app.use(express.json());

app.get("/", (req, res) => {
  const name = req.signedCookies["Login"];
  res.send(`Hello ${name}`);
});

app.post("/login", (req, res) => {
  const name = req.body.name;
  res.cookie("Login", name, { path: "/", signed: true });
  res.send(`Hello ${name}`);
});

test("Test Cookie Read", async () => {
  const response = await request(app)
    .get("/")
    .set(
      "Cookie",
      "Login=s%3AInayah.Z1xfjjjEAO7wa7ugjo6Jlq7QbdUJYXHTDA4rC9fHMfQ; Path=/"
    );

  expect(response.text).toBe("Hello Inayah");
});

test("Test Cookie Write", async () => {
  const response = await request(app).post("/login").send({ name: "Inayah" });
  console.info(response.get("Set-Cookie").toString());

  expect(response.get("Set-Cookie").toString()).toContain("Inayah");
  expect(response.text).toBe("Hello Inayah");
});
```

**Selanjutnya :** [Response Body Lainnya](responselainnya.md)