---
title: Request URL
tags:
  - express
---

- Untuk mendapatkan URL saat ini, kita bisa menggunakan object request untuk mendapatkan informasinya.
- req.originalUrl, untuk mendapatkan url secara full beserta query param-nya.
- req.path, untuk mendapatkan path url tanpa query param.
- req.hostname, untuk mendapatkan nama host atau domain dari web kita.
- req.protocol, untuk mendapatkan protocol dari url web.
- req.secure, untuk mengecek apakah url web nya https atau bukan.
- req.subdomains, untuk mendapatkan array subdomain dari url web kita.

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/hello/world", (req, res) => {
  res.json({s
    path: req.path,
    originalUrl: req.originalUrl,
    hostname: req.hostname,
    protocol: req.protocol,
    secure: req.secure,
  });
});

test("Test Request URL", async () => {
  const response = await request(app)
    .get("/hello/world")
    .query({ name: "Zulhaditya" });

  expect(response.body).toEqual({
    path: "/hello/world",
    originalUrl: "/hello/world?name=Zulhaditya",
    hostname: "127.0.0.1",
    protocol: "http",
    secure: false,
  });
});
```

**Selanjutnya :** [Request Query Param](requestparam.md)
