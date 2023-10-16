---
title: Script
tags:
  - npm
---

- NPM memiliki fitur script, dimana kita bisa menyediakan perintah script yang nanti bisa digunakan untuk menjalankan perintah lainnya.
- Penggunaan script ini biasanya digunakan untuk mempermudah ketika kita menjalankan perintah yang panjang.
- Untuk menambahkan script, kita bisa tambahkan scriptnya di file package.json

# Menjalankan Script

Untuk menjalankan script kita bisa gunakan perintah:

```bash
npm run-script namascript

# atau
npm run namascript
```

# Special Script

- Script di package.json terdapat beberapa yang spesial atau khusus.
- Script tersebut tidak perlu dijalankan menggunakan npm run-script namascript, tapi bisa langsung dijalankan menggunakan perintah npm namascript.
- Contoh: **start, stop, test, restart, uninstall, version,** dan lain-lain.
- Selain itu, terdapat script special untuk script diatas, kita bisa gunakan prefix pre sebagai script yang akan dijalankan sebelumnya, dan prefix post sebagai script yang dijalankan setelahnya.
- Misalnya ketika kita gunakan perintah npm start, maka akan menjalankan perintah script prestart, start, dan poststart.

**Selanjutnya :** [Export Module](exportmodule.md)