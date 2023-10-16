---
title: Middleware
tags:
  - express
---

- Middleware adalah function yang bisa digunakan untuk mengakses request object, response object dan next function dalam alur hidup aplikasi ExpressJS.
- Jika middleware memanggil next function, artinya function middleware selanjutnya atau router akan dieksekusi.

# Fungsi Middleware

Ada banyak sekali kegunaan dari middleware seperti:

- Eksekusi kode sebelum router di eksekusi.
- Mengubah request atau response object sebelum router di eksekusi.
- Mengakhiri response tanpa harus mengeksekusi router.
- Dan lain-lain.

# Spesifikasi Middleware

- Untuk membuat middleware, kita cukup membuat function dengan 3 parameter, request, response, dan next.
- request adalah request object.
- response adalah response object.
- next adalah next function, bisa middleware selanjutnya atau router.

# Manipulasi Request

- Karena request itu adalah Javascript Object.
- Kita bisa memanipulasi request object di middleware.
- Misal untuk mengubah attribute atau menambahkan attribute baru, agar bisa digunakan di middleware selanjutnya, atau di router.

```js
import express from "express";
import request from "supertest";

// middleware untuk logger
const logger = (req, res, next) => {
  console.info(`Receive request: ${req.method} ${req.originalUrl}`);
  next();
};

// middleware untuk menambahkan header baru
const addPoweredHeader = (req, res, next) => {
  res.set("X-Powered-By", "Ackxle");
  next();
};

// middleware untuk melakukan validasi
const apiKeyMiddleware = (req, res, next) => {
  if (req.query.apiKey) {
    next();
  } else {
    res.status(401).end();
  }
};

// middleware untuk menambahkan attribute di request
const requestTimeMiddleware = (req, res, next) => {
  req.requestTime = Date.now();
  next();
};

const app = express();
app.use(logger);
app.use(apiKeyMiddleware);
app.use(addPoweredHeader);
app.use(requestTimeMiddleware);

app.get("/", (req, res) => {
  res.send(`Hello Response`);
});

app.get("/inayah", (req, res) => {
  res.send(`Hello Inayah`);
});

app.get("/time", (req, res) => {
  res.send(`Hello, Today is ${req.requestTime}`);
});

test("Test Response Middleware", async () => {
  const response = await request(app).get("/").query({ apiKey: "123" });
  expect(response.get("X-Powered-By")).toBe("Ackxle");
  expect(response.text).toBe("Hello Response");
});

test("Test Response Middleware 2", async () => {
  const response = await request(app).get("/inayah").query({ apiKey: "123" });
  expect(response.get("X-Powered-By")).toBe("Ackxle");
  expect(response.text).toBe("Hello Inayah");
});

test("Test Response Middleware Unauthorized", async () => {
  const response = await request(app).get("/inayah");
  expect(response.status).toBe(401);
});

test("Test Response Middleware Time", async () => {
  const response = await request(app).get("/time").query({ apiKey: "123" });
  expect(response.get("X-Powered-By")).toBe("Ackxle");
  expect(response.text).toContain("Hello, Today is");
});
```

**Selanjutnya :** [Route Path](routepath.md)