---
title: Response Lainnya
tags:
  - express
---

- Sebelumnya kita sudah mencoba beberapa jenis Response Body di ExpressJS.
- Kita bisa menggunakan res.send(data) untuk mengirim response berupa text misalnya, atau menggunakan res.json(object) untuk mengirim data dalam bentuk JSON.
- Sebenarnya masih banyak jenis Response Body lainnya yang didukung oleh ExpressJS.

```txt
contoh.txt

This is sample text
```

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.sendFile(__dirname + "/contoh.txt");
});

test("Test Response Send File", async () => {
  const response = await request(app).get("/");
  expect(response.text).toContain("This is sample text");
});
```

**Selanjutnya :** [Error Handling](errorhandling.md)
