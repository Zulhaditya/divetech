---
title: Use Mustache
tags:
  - mustache
---

- Sebelum mempelajari tentang Mustache Template Engine, kita harus mempelajari terlebih dahulu cara penggunaan MustacheJS.
- Untuk menggunakan MustacheJS, terdapat fitur bernama render(template, data) di package mustache, yang digunakan untuk merender template dan data.

```js
import Mustache from "mustache";

test("Menggunakan Mustache", () => {
  const data = Mustache.render("Hello {{name}}", { name: "Nay" });
  // Hello Nay
});
```

**Selanjutnya :** [Mustache Cache](mustachecache.md)
