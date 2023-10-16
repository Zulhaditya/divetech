---
title: Route Function
tags:
  - express
---

- Kadang ada kasus ketika kita membuat route path yang sama untuk beberapa tipe HTTP method.
- Pada kasus ini kita bisa memanfaatkan route(path) function sehingga tidak perlu mendeklarasikan nama path sama untuk beberapa route.
- https://expressjs.com/en/4x/api.html#app.route

```js
import express from "express";
import request from "supertest";

const app = express();

app
  .route("/products")
  .get((req, res) => {
    res.send("Get Products");
  })
  .post((req, res) => {
    res.send("Create Products");
  })
  .put((req, res) => {
    res.send("Update Products");
  });

test("Test Route Function", async () => {
  let response = await request(app).get("/products");
  expect(response.text).toBe("Get Products");

  response = await request(app).post("/products");
  expect(response.text).toBe("Create Products");

  response = await request(app).put("/products");
  expect(response.text).toBe("Update Products");
});
```

**Selanjutnya :** [Router](router.md)
