---
title: List
tags:
  - mustache
---

- Saat membuat template, kita juga ingin menampilkan data yang bentuknya adalah list atau array.
- Mustache juga bisa menggunakan sections untuk menampilkan itu.
- Untuk menampilkan tiap data, kita bisa gunakan titik didalam sectionnya, misal {{.}}
- Sama seperti sections, jika data list tidak ada, maka tidak akan menampilkan apapun.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hobbies</title>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body>
    <h1>Hobbies</h1>

    <ul>
      {{#hobbies}}
      <li>{{.}}</li>
      {{/hobbies}}
    </ul>
  </body>
</html>
```

```js
import Mustache from "mustache";
import fs from "fs/promises";

test.only("List", async () => {
  const helloTemplate = await fs
    .readFile("./templates/hobbies.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(helloTemplate, {
    hobbies: ["Coding", "Gaming", "Ngopi"],
  });

  console.info(data);

  expect(data).toContain("Coding");
  expect(data).toContain("Gaming");
  expect(data).toContain("Ngopi");
});
```

**Selanjutnya :** [List Object](listobject.md)