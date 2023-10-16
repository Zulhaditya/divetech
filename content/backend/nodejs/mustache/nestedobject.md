---
title: Nested Object
tags:
  - mustache
---

- Mustache tags juga bisa digunakan untuk data nested, bahkan array.
- Untuk mengaksesnya, dalam tags kita bisa gunakan titik, misalkan {{person.name}}

```js
import Mustache from "mustache";

test("Menggunakan Nested Object", () => {
  const data = Mustache.render("Hello {{person.name}}", {
    person: {
      name: "Nay",
    },
  });
  expect(data).toBe("Hello Nay");
});
```

**Selanjutnya :** [Mustache File](mustachefile.md)