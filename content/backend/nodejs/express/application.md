---
title: Application
tags:
  - express
---

- Saat kita membuat web menggunakan ExpressJS, kita akan membuat object application.
- Application adalah object utama dalam library ExpressJS.
- https://expressjs.com/en/4x/api.html#app

# Menjalankan Application

- Application secara default tidak berjalan, jika kita ingin menjalankan Application-nya, kita perlu menggunakan method listen(port).
- Dimana port adalah nomor port yang ingin kita gunakan untuk menjalankan web-nya.
- Pastikan port yang kita pilih tidak bentrok dengan aplikasi lain.
- https://expressjs.com/en/4x/api.html#app.listen

```js
import express from "express";

const app = express();

app.listen(3000, () => {
  console.log("Service started on port 3000");
});
```

**Selanjutnya :** [Basic Routing](basicrouting.md)