---
title: Comment
tags:
  - mustache
---

- Kita dapat menambahkan komentar di file Mustache.
- Untuk menambahkan komentar, kita bisa menggunakan {{! isi komentar}}.

```html
<html>
  <body>
    {{! Ini Komentar}}
    <h1>{{title}}</h1>
  </body>
</html>
```

```js
import Mustache from "mustache";
import fs from "fs/promises";

test.only("Comment", async () => {
  const helloTemplate = await fs
    .readFile("./templates/comment.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(helloTemplate, {
    title: "Nay",
  });

  console.info(data);

  expect(data).toContain("Nay");
  expect(data).not.toContain("Ini Komentar");
});
```

**Selanjutnya :** [Partials](partials.md)
