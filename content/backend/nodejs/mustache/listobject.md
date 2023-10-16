---
title: List Object
tags:
  - mustache
---

- Kadang, kita memiliki data kumpulan object didalam list atau array.
- Kita dapat mengakses data object tersebut menggunakan sections, caranya mirip dengan menggunakan sections object.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Students</title>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body>
    <h1>Students</h1>

    <table>
      {{#students}}
      <tr>
        <td>{{name}}</td>
        <td>{{value}}</td>
      </tr>
      {{/students}}
    </table>
  </body>
</html>
```

```js
import Mustache from "mustache";
import fs from "fs/promises";

test.only("Object List", async () => {
  const helloTemplate = await fs
    .readFile("./templates/students.mustache")
    .then((data) => data.toString());

  const data = Mustache.render(helloTemplate, {
    students: [
      { name: "Nay", value: 90 },
      { name: "Hapiz", value: 100 },
    ],
  });

  console.info(data);

  expect(data).toContain("Nay");
  expect(data).toContain("90");
});
```

**Selanjutnya :** [Functions](functions.md)