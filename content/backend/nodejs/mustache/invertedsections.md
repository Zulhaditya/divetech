---
title: Inverted Sections
tags:
  - mustache
---

- Saat menggunakan logika if, kadang kita ingin menambahkan kondisi else.
- Di mustache, kita bisa menggunakan inverted sections, dimana block section akan dieksekusi jika nilai sections adalah null, undefined, false, falsy, atau empty list.
- Untuk menggunakan inverted section, kita bisa gunakan {{^nama}} dan ditutup dengan {{/nama}}.

```html
<html>
  <head>
    <title>Person</title>
  </head>
  <body>
    {{#person}} Hello Person {{name}}! {{/person}} {{^person}} Hello Guest
    {{/person}}
  </body>
</html>
```

```js
import Mustache from "mustache";
import fs from "fs/promises";

test.only("Inverted Sections", async () => {
  const helloTemplate = await fs
    .readFile("./templates/person.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(helloTemplate, {});
  console.info(data);

  expect(data).toContain("Hello Guest");
});
```

**Selanjutnya :** [List](list.md)