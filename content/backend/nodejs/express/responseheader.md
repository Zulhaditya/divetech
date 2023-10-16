---
title: Response Header
tags:
  - express
---

- Kita juga bisa mengubah HTTP Response header dengan menggunakan method res.set(name, value) atau res.header(name, value).
- Atau jika ingin langsung beberapa name, kita bisa masukkan dalam bentuk object ke dalam parameter name-nya.
- https://expressjs.com/en/4x/api.html#res.set

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.set({
    "X-Powered-By": "Ackxle",
    "X-Author": "Zulhaditya",
  });
  res.send(`Hello Response`);
});

test("Test Response Header", async () => {
  const response = await request(app).get("/");

  expect(response.text).toBe("Hello Response");
  expect(response.get("X-Powered-By")).toBe("Ackxle");
  expect(response.get("X-Author")).toBe("Zulhaditya");
});
```

**Selanjutnya :** [Response Body](responsebody.md)
