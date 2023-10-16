---
title: Request Header
tags:
  - express
---

- Object request juga bisa digunakan untuk mendapatkan http header dari request.
- Kita bisa menggunakan method req.get(name) atau req.header(name) untuk mendapatkan header berdasarkan name, khusus untuk HTTP header, name nya adalah case insensitive.
- https://expressjs.com/en/4x/api.html#req.get

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  const type = req.get("accept");
  res.send(`Hello ${type}`);
});

test("Test Query Parameter", async () => {
  const response = await request(app).get("/").set("Accept", "text/plain");
  expect(response.text).toBe("Hello text/plain");
});
```

**Selanjutnya :** [Response](response.md)