---
title: Mustache File
tags:
  - mustache
---

- MustacheJS sebenarnya tidak memiliki kemampuan untuk membaca template dari file, jadi kita perlu membaca template file dari file secara manual.
- Biasanya Mustache menggunakan nama file dengan extension .mustache

```js
import Mustache from "mustache";
import fs from "fs/promises";

test("Mustache File", async () => {
  const helloTemplate = await fs
    .readFile("./templates/hello.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(helloTemplate, {
    title: "Inayah Cantik",
  });

  console.info(data);

  expect(data).toContain("Inayah Cantik");
});
```

**Selanjutnya :** [Sections](sections.md)
