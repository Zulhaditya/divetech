---
title: Redirect
tags:
  - express
---

- Untuk melakukan redirect dari sebuah web ke halaman lain, kita hanya cukup menggunakan HTTP Header Location.
- Di ExpressJS, kita bisa melakukan manual dengan menggunakan HTTP Header Location, atau bisa menggunakan method res.redirect(to)
- https://expressjs.com/en/4x/api.html#res.redirect

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.redirect("/to-next-page");
});

test("Test Response Redirect", async () => {
  const response = await request(app).get("/");
  expect(response.status).toBe(302);
  expect(response.get("location")).toBe("/to-next-page");
});
```

**Selanjutnya :** [Middleware](middleware.md)