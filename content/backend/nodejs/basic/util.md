---
title: Util
tags:
  - standard-library
---

- Util adalah standard library yang berisikan utility-utility yang bisa kita gunakan untuk mempermudah pembuatan kode program Node.js
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/util.html

```js
import util from "util";

const firstName = "zulhaditya";
const lastName = "hapiz";

console.info(`Hello ${firstName} ${lastName}`);
// format string
console.info(util.format("Hello %s", firstName, lastName));

const person = {
  firstName: "inayah",
  lastName: "wulandari",
};

console.info(`Person : ${JSON.stringify(person)}`);
// format json
console.info(util.format("Person : %j", person));
```

**Selanjutnya :** [Zlib](zlib.md)
