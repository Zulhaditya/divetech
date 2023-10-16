---
title: Response
tags:
  - express
---

- Pada callback routing ExpressJS, terdapat parameter kedua yaitu response.
- Response merupakan object representasi dari HTTP Response.
- Kita bisa mengubah data HTTP Response melalui object response tersebut.
- https://expressjs.com/en/4x/api.html#res

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.send(`Hello Response`);
});

test("Test Response", async () => {
  const response = await request(app).get("/");

  expect(response.text).toBe("Hello Response");
});
```

**Selanjutnya :** [Response Status](responsestatus.md)
