---
title: Router
tags:
  - express
---

- Saat membuat aplikasi ExpressJS, secara default sudah terdapat object Router-nya.
- Namun, kita bisa membuat object router sendiri jika kita mau, hal ini sangat cocok jika ingin melakukan grouping Router, lalu misalkan kita bisa menambahkan Router tersebut ke Application seperti Middleware.
- Ini sangat cocok ketika kita ingin membuat fitur modular yang bisa mengaktifkan atau menonaktifkan router secara dinamis.
- Dengan object router, kita bisa memiliki Middleware dan Routing secara independen.
- https://expressjs.com/en/4x/api.html#express.router
- https://expressjs.com/en/4x/api.html#router

```js
import express from "express";
import request from "supertest";

const app = express();

const router = express.Router();

router.use((req, res, next) => {
  console.info(`Receive request : ${req.originalUrl}`);
  next();
});

router.get("/feature/a", (req, res) => {
  res.send("feature a");
});

test("Test Router Disabled", async () => {
  const response = await request(app).get("/feature/a");
  expect(response.status).toBe(404);
});

test("Test Router Enabled", async () => {
  app.use(router);

  const response = await request(app).get("/feature/a");
  expect(response.text).toBe("feature a");
});
```

**Selanjutnya :** [Type of Middleware](typemiddleware.md)