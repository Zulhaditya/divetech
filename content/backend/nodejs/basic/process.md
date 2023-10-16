---
title: Process
tags:
  - standard-library
---

- Process merupakan standard library yang digunakan untuk mendapatkan informasi proses Node.js yang sedang berjalan.
- Process juga merupakan instance dari EventEmitter, sehingga kita bisa menambahkan listener kedalam process.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/process.html

```js
import process from "process";

process.addListener("exit", (exitCode) => {
  console.info(`Node.js exit with code ${exitCode}`);
});

console.info(process.version);
console.table(process.argv);
console.table(process.report);
console.table(process.env);
process.exit(1);
```

**Selanjutnya :** [Readline](readline.md)
