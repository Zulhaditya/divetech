---
title: Response Body
tags:
  - express
---

- Untuk mengubah Response Body, kita bisa menggunakan method res.send(body)
- Dimana parameter body bisa kita kirim dalam bentuk buffer atau string, baik itu text, html, json, dan lain-lain.
- https://expressjs.com/en/4x/api.html#res.send

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.set("Content-Type", "text/html");
  res.send(`<html><body>Hello World</body></html>`);
});

test("Test Response", async () => {
  const response = await request(app).get("/");

  expect(response.get("Content-Type")).toContain("text/html");
  expect(response.text).toBe(`<html><body>Hello World</body></html>`);
});
```

**Selanjutnya :** [Redirect](redirect.md)