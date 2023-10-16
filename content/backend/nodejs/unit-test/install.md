---
title: Install
tags:
  - jest
---

- Jest digunakan untuk membuat unit test saja, sehingga kita tidak perlu menambahkan dependency production.
- Kita cukup tambahkan sebagai development dependency.
- Kita bisa tambahkan di package.json atau bisa gunakan perintah:

```bash
npm install jest --save-dev
```

- https:///www.npmjs.com/package/jest

# Menjalankan Unit Test

- Untuk menjalankan unit test menggunakan jest, kita bisa jalankan file jest yang ada di node_modules/.bin/jest
- Tapi bisa dipermudah menggunakan script di package, dengan mengetikkan kode programnya saja di bagian script test.

# NPX

- Menjalankan perintah jest lumayan ribet karena kita harus menjalankan melalui folder node_modules/.bin/
- Untungnya, di Node.js terdapat program NPX (Node Package Runner).
- NPX ini digunakan untuk menjalankan perintah yang bisa secara otomatis mendeteksi file yang terdapat di node_modules/.bin/
- Jadi untuk menjalankan jest, kita bisa menggunakan perintah:

```bash
npx jest
```

**Selanjutnya :** [Create Unit Test](create.md)
