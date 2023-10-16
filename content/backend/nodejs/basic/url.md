---
title: URL
tags:
  - standard-library
---

- URL adalah standard library yang digunakan untuk bekerja dengan URL
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/url.html

```js
import { URL } from "url";

const test = new URL("https://zulhaditya.com/belajar?kelas=nodejs");

// mengubah url
test.host = "www.zulhaditya.com";
test.searchParams.append("status", "premium");

console.info(test.toString());
console.info(test.href);
console.info(test.protocol);
console.info(test.host);
console.info(test.hostname);
console.info(test.searchParams);
```

**Selanjutnya :** [Util](util.md)
