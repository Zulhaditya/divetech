---
title: Partials
tags:
  - mustache
---

- Saat kita membuat halaman web menggunakan Mustache, kita ingin membagi template menjadi beberapa bagian.
- Misalkan ada bagian header, content, dan footer.
- Untungnya, Mustache mendukung hal tersebut.
- Kita bisa menggunakan perintah {{ > namaPartial}}.
- Pada function render, terdapat parameter ketiga yang berisikan object partials yang bisa kita gunakan untuk menambahkan data template lainnya.

```html
<!-- header.mustache -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <title>{{title}}</title>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body></body>
</html>
```

```html
<!-- content.mustache -->

{{> header}}
<h1>{{title}}</h1>
<p>{{content}}</p>
{{ > footer}}
```

```html
<!-- footer.mustache -->

<p>Muhammad Zulhaditya Hapiz</p>
</body>
</html>
```

```js
import Mustache from "mustache";
import fs from "fs/promises";

test.only("Partials", async () => {
  const contentTemplate = await fs
    .readFile("./templates/content.mustache")
    .then((data) => data.toString());

  const headerTemplate = await fs
    .readFile("./templates/header.mustache")
    .then((data) => data.toString());

  const footerTemplate = await fs
    .readFile("./templates/footer.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(
    contentTemplate,
    {
      title: "Nay",
      content: "Belajar Mustache JS",
    },
    {
      header: headerTemplate,
      footer: footerTemplate,
    }
  );

  console.info(data);

  expect(data).toContain("Nay");
  expect(data).toContain("Belajar Mustache JS");
});
```
