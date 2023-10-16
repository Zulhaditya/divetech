---
title: Functions
tags:
  - mustache
---

- Dalam tags, selain data, kita juga bisa mengakses function.
- Caranya cukup mudah, kita hanya perlu membuat function yang mengembalikan function dengan parameter text, dan render.
- Parameter render adalah function Mustache untuk melakukan render, dan sebelum dikembalikan, kita bisa memanipulasi hasilnya.
- Untuk menggunakan function, caranya sama dengan menggunakan sections, cukup gunakan {{#function}} dan ditutup dengan {{/function}}.

```js
import Mustache from "mustache";
import fs from "fs/promises";

test.only("Functions", async () => {
  const parameter = {
    name: "Nay",
    upper: () => {
      return (text, render) => {
        return render(text).toUpperCase();
      };
    },
  };

  const data = Mustache.render("Hello {{#upper}}{{name}}{{/upper}}", parameter);
  console.info(data);
  expect(data).toBe("Hello NAY");
});
```

**Selanjutnya :** [Comment](/backend/nodejs/mustache/comment.md)
