---
title: OS
tags:
  - standard-library
---

- OS merupakan standard library yang bisa digunakan untuk mendapatkan informasi tentang sistem operasi yang digunakan.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/os.html

```js
import os from "os";

// menampilkan platform os
console.info(os.platform());

// menampilkan arsitektur 64/32bit
console.info(os.arch());

// menampilkan total cpu
console.table(os.cpus());

// menampilkan waktu aktif sistem dalam hitungan detik
console.info(os.uptime());

// menampilkan total memori sistem dalam byte
console.info(os.totalmem());

// menampilkan jumlah free memory dalam byte
console.info(os.freemem());

// menampilkan network interfaces
console.table(os.networkInterfaces());
```

**Selanjutnya :** [Path](path.md)
