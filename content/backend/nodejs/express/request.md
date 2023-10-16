---
title: Request
tags:
  - express
---

- Saat kita membuat callback di router, parameter pertama adalah object request, yang secara otomatis diisi oleh ExpressJS.
- Object request akan berisikan informasi tentang HTTP Request yang masuk ke callback tersebut.
- Ada banyak sekali informasi HTTP Request yang bisa kita ambil dari object request, seperti Query Param, Header, Body, dan lain-lain.
- https://expressjs.com/en/4x/api.html#req

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.send(`Hello ${req.query.name}`);
});

test("Test Query Parameter", async () => {
  const response = await request(app).get("/").query({ name: "World" });
  expect(response.text).toBe("Hello World");
});
```

**Selanjutnya :** [Request URL](requesturl.md)
