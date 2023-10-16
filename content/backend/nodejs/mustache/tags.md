---
title: Tags
tags:
  - mustache
---

- Mustache menggunakan kurung kurawal dua kali sebagai tags, misalkan {{name}}.
- Tag digunakan untuk mengirim data dari luar template, jika data tidak dikirim, maka akan diganti oleh string kosong.
- Secara default, HTML didalam tags akan di escape, jika kita ingin menampilkan HTML, kita bisa gunakan kurung kurawal tiga kali, contohnya {{{kode}}}.

```js
import Mustache from "mustache";

test("Tags", () => {
  const data = Mustache.render("Hello {{name}}, my hobby is {{{hobby}}}", {
    name: "Nay",
    hobby: "<b>Programming</b>",
  });
  expect(data).toBe("Hello Nay, my hobby is <b>Programming</b>");
});
```

**Selanjutnya :** [Nested Object](nestedobject.md)
