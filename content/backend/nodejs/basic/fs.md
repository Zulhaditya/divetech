---
title: File System
tags:
  - standard-library
---

- File System merupakan standard library yang digunakan untuk memanipulasi file.
- Dalam File System, terdapat 3 jenis library.
  1.  Library yang bersifat blocking atau synchronous
  2.  Library yang bersifat non-blocking atau asynchronous menggunakan callback
  3.  Library yang bersifat non-blocking atau asynchronous menggunakan promise
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/fs.html

```js
import fs from "fs/promises";

// membaca file
const buffer = await fs.readFile("file-system.mjs");
console.info(buffer.toString());

// membuat dan menulis file
fs.writeFile("temp.txt", "Halo NodeJS");
```

**Selanjutnya :** [Debuggger](debugger.md)
