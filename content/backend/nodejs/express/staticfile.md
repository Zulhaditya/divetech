---
title: Static File
tags:
  - express
---

- Saat membuat web, kadang kita ingin menampilkan static file seperti html, css, javascript, gambar, atau file lainnya.
- Jika kita ingin membuat route untuk setiap file, maka akan sangat menyulitkan.
- Untungnya, terdapat Middleware yang bisa digunakan untuk menyediakan static file.
- Middleware ini secara otomatis akan mencari file, jika file ada, maka akan dikembalikan file tersebut, jika tidak ada maka akan dilanjutkan ke middleware atau route selanjutnya.
- Kita bisa menggunakan Middleware express.static()
- https://expressjs.com/en/4x/api.html#express.static

# Prefix Path

- Kadang kita ingin memberi prefix path pada static file, misalkan /static/filenya
- Pada kasus itu kita bisa tambahkan route pada middlewarenya, contoh:
- app.use("static", express.static(...))

```js
import express from "express";
import request from "supertest";

const app = express();

// app.use(express.static(__dirname + "/static"));
app.use("/static", express.static(__dirname + "/static"));

app.get("/", (req, res) => {
  res.send(`Hello Response`);
});

app.get("/contoh.txt", (req, res) => {
  res.send(`Hello Response`);
});

test("Test Static File", async () => {
  const response = await request(app).get("/");
  expect(response.text).toBe("Hello Response");
});

test("Test Static file /static/contoh.txt", async () => {
  const response = await request(app).get("/static/contoh.txt");
  expect(response.text).toContain("This is sample text");
});
```

**Selanjutnya :** [Template Engine](templateengine.md)
