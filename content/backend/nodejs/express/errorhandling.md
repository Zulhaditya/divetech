---
title: Error Handling
tags:
  - express
---

# Jika terjadi error

- Apa yang terjadi jika ada error di aplikasi kita? secara otomatis error tersebut akan ditangkap oleh ExpressJS.
- Lalu detail error-nya akan ditampilkan di response secara otomatis.
- Ada kasus ketika kita ingin mengubah cara menampilkan error, atau bahkan kita memang berharap terjadi error, misalkan validation error.
- Pada kasus seperti ini, ExpressJS memiliki fitur Error-Handling Middleware, dimana kita bisa membuat Middleware dan akan dieksekusi ketika terjadi error.
- Berbeda dengan Middleware biasanya, pada Error-Handling Middleware, diperlukan empat parameter, dimana diawali dengan parameter error-nya.

```js
import express from "express";
import request from "supertest";

const app = express();

const errorMiddleware = (err, req, res, next) => {
  res.status(500).send(`Terjadi Error: ${err.message}`);
};

app.get("/", (req, res) => {
  throw new Error("Ups");
});

app.use(errorMiddleware);

test("Test Response", async () => {
  const response = await request(app).get("/");
  expect(response.status).toBe(500);
  expect(response.text).toBe("Terjadi Error: Ups");
});
```

**Selanjutnya :** [Static File](staticfile.md)