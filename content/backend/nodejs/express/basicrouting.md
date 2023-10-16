---
title: Basic Routing
tags:
  - express
---

# Routing

- Saat kita membuat web, biasanya kita akan membuat banyak sekali URL Path.
- Routing merupakan teknik yang digunakan untuk meneruskan request dari URL Path ke Callback yang kita tuju.
- Routing di ExpressJS bisa menggunakan object application, dan menggunakan method sesuai dengan nama HTTP methodnya.

```js
import express from "express";

const app = express();

app.get("/", (req, res) => {
  res.send("Hello Zulhaditya!");
});

app.get("/inayah", (req, res) => {
  res.send("Hello Inayah");
});

app.get("/wulan", (req, res) => {
  res.send("Hello Wulandari");
});

app.listen(3000, () => {
  console.log("Service started on port 3000");
});
```

**Selanjutnya :** [Unit Test](unittest.md)
