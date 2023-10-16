---
title: Export Module
tags:
  - npm
---

# Main

- Attribute main adalah entry point yang akan di-load ketika kita menjalankan project Node.js / Package.
- Ketika membuat aplikasi, mungkin tidak akan terlalu berguna, tapi pada kasus ketika kita membuat library yang akan digunakan di banyak project, attribute ini akan terlihat kegunaannya.
- Terdapat attribute export untuk menggantikan penggunaan main sebagai konfigurasi untuk mengekspos file Javascript.
- Kita dapat membuat fitur alias ketika mengekspos file js, sehingga tidak perlu menggunakan nama file js yang asli.

# Menggunakan Module

- Untuk menggunakan module yang sudah di export, kita cukup gunakan import dari nama module yang dieksport tersebut, namun ganti tanda .(titik) dengan nama package yang ada di package.json
- Contoh:
  "." menjadi "belajar-nodejs-npm"
  "./write" menjadi "belajar-nodejs-npm/write"

**Selanjutnya :** [Dependency Management](dependency.md)
