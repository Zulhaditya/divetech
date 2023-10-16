---
title: Section Data
tags:
  - mustache
---

- Saat menggunakan sections, kita juga bisa mengakses data yang terdapat di sections secara otomatis, tanpa harus menyebutkan sections-nya lagi.
- Misalkan pada kasus sebelumnya, kita bisa mengakses {{name}} tanpa harus menyebutkan {{person.name}}.

```js
import Mustache from "mustache";
import fs from "fs/promises";

test("Sections Data", async () => {
  const helloTemplate = await fs
    .readFile("./templates/person.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(helloTemplate, {
    person: {
      name: "Nay",
    },
  });

  console.info(data);

  expect(data).toContain("Hello Person Nay!");
});
```

**Selanjutnya :** [Inverted Sections](invertedsections.md)
