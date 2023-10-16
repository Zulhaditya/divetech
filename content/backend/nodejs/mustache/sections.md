---
title: Sections
tags:
  - mustache
---

- Mustache adalah template engine yang tidak memiliki logic yang kompleks.
- Ada kasus jika kita ingin menambahkan logic, misalkan if else.
- Di mustache, hal ini bisa kita ganti menjadi sections.
- Sections di mustache menggunakan {{#nama}}, dan ditutup dengan {{/nama}}
- Dimana blok didalam sections tidak akan ditampilkan jika variabel di sections tidak ada, atau ada tapi dengan nilai null, undefined, false, 0, NaN, empty string atau empty array.

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

**Selanjutnya :** [Section Data](sectiondata.md)