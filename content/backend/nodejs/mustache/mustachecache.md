---
title: Mustache Cache
tags:
  - mustache
---

- Saat kita menggunakan function render(), data template akan di cache oleh MustacheJS, hal ini agar ketika kita melakukan render dengan template yang sama, proses render akan menjadi lebih cepat.
- Biasanya, proses render di awal akan sedikit lebih lama, dikarenakan butuh melakukan proses kompilasi template terlebih dahulu.
- Jika kita ingin mempercepat, di awal aplikasi berjalan, kita bisa lakukan kompilasi semua template terlebih dahulu, dengan cara menggunakan function parse(template).

```js
import Mustache from "mustache";

test("Menggunakan Mustache Cache", () => {
  Mustache.parse("Hello {{name}}");

  const data = Mustache.render("Hello {{name}}", { name: "Nay" });
  expect(data).toBe("Hello Nay");
});
```

**Selanjutnya :** [Tags](tags.md)