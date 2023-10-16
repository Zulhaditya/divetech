---
title: Request Param
tags:
  - express
---

- Request juga bisa digunakan untuk mengambil data query parameter.
- Secara otomatis, semua query parameter akan disimpan dalam bentuk object di req.query
- https://expressjs.com/en/4x/api.html#req.query

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.send(`Hello ${req.query.firstName} ${req.query.lastName}`);
});

test("Test Query Parameter", async () => {
  const response = await request(app)
    .get("/")
    .query({ firstName: "Zulhaditya", lastName: "Hapiz" });
  expect(response.text).toBe("Hello Zulhaditya Hapiz");
});
```

**Selanjutnya :** [Request Header](requestheader.md)
