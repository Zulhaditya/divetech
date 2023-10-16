---
title: Unit Test
tags:
  - express
---

# Bagaimana melakukan unit test di ExpressJS?

- Salah satu yang sulit ketika membuat aplikasi web yang harus berjalan yaitu melakukan automation test.
- Jika melakukan manual test, terlihat mudah tinggal kita buka di web browser.
- Namun dalam pekerjaan sehari-hari, lambat laun, hal ini akan menyulitkan kita ketika harus melakukan manual test jika terdapat perubahan di aplikasi kita.
- Oleh karena itu sangat direkomendasikan menggunakan unit test, walaupun aplikasinya dalam bentuk web.

## Supertest

- Supertest adalah salah satu library yang bisa digunakan untuk membantu dalam pengetesan web ExpressJS.
- Dengan supertest, kita bisa lebih mudah untuk membuat unit test-nya, dibanding melakukan secara manual.
- https://www.npmjs.com/package/supertest

```js
import express from "express";
import request from "supertest";

const app = express();

app.get("/", (req, res) => {
  res.send("Hello Zulhaditya!");
});

test("Test ExpressJS", async () => {
  const response = await request(app).get("/");
  expect(response.text).toBe("Hello Zulhaditya!");
});
```

**Selanjutnya :** [Request](request.md)
