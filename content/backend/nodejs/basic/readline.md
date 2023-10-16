---
title: Readline
tags:
  - standard-library
---

- Readline merupakan standard library yang digunakan untuk membaca input.
- Readline hanya mendukung versi callback di versi Node.js LTS 16.
- Di Node.js 17 sudah mendukung promise sehingga lebih mudah digunakan, namun itupun masih di tahap experimental.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/readline.html

```js
import readline from "readline";
import process from "process";

const input = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

input.question("Siapa nama anda? ", (name) => {
  console.info(`Halo ${name}`);
  input.close();
});
```

**Selanjutnya :** [Report](report.md)