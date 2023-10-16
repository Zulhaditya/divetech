---
title: Template Engine
tags:
  - express
---

- Saat membuat web menggunakan ExpressJS, jika kita membuat string HTML lalu kita kirim menggunakan response, hal tersebut akan sangat menyulitkan.
- Kita bisa mempermudah hal tersebut dengan menerapkan Template Engine.
- Template Engine adalah library yang digunakan untuk membuat template yang fungsinya untuk mempermudah kita ketika ingin menampilkan data di template-nya.
- Biasanya template tersebut dalam bentuk HTML, dan datanya dapat diubah sesuai dengan data yang kita ingin tampilkan di HTML tersebut.

# Template Engine Library

- ExpressJS tidak menyediakan template engine, oleh karena itu kita dapat menggunakan library lain seperti:
- Mustache: https://github.com/janl/mustache.js/
- Pug: https://github.com/pugjs/pug
- EJS: https://github.com/mde/ejs
- Marko: https://github.com/marko-js/marko
- Dan lain-lain.

## Mustache Express

- Kita akan menggunakan Mustache sebagai template engine.
- Hal ini dikarenakan Mustache merupakan template engine yang sangat mudah untuk digunakan.
- Kita tidak akan menginstall Mustache secara manual, kita akan menggunakan bantuan library Mustache Express.
- https://www.npmjs.com/package/mustache-express

### Contoh:

Buat terlebih dahulu file template-nya di folder /views/index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>{{title}}</title>
    <meta charset="UTF-8" />
  </head>
  <body>
    <p>{{say}}</p>
  </body>
</html>
```

Selanjutnya buat file template.test.js

```js
import express from "express";
import request from "supertest";
import mustacheExpress from "mustache-express";

const app = express();

app.set("views", __dirname + "/views");
app.set("view engine", "html");
app.engine("html", mustacheExpress());

app.get("/", (req, res) => {
  res.render("index", {
    title: "Hello World",
    say: "This is a test",
  });
});

test("Test Response", async () => {
  const response = await request(app).get("/");
  console.info(response.text);
  expect(response.text).toContain("Hello World");
  expect(response.text).toContain("This is a test");
});
```

**Selanjutnya :** [File Upload](fileupload.md)
