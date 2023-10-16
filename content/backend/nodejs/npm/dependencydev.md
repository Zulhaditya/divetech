---
title: Dependency Development
tags:
  - npm
---

- Di package.json, terdapat dua jenis dependency, production dan development.
- Dependency management yang sebelumnya dibahas adalah production dependency, yaitu dependency yang dibutuhkan ketika aplikasi sedang berjalan.
- Sedangkan development dependency, adalah dependency yang dibutuhkan khusus ketika proses development, contoh misalkan dependency unit testing, digunakan ketika pada tahap development saja, tetapi tidak kita butuhkan ketika aplikasi berjalan.

# Menambah Development Dependency

- Untuk menambahkan development dependency, kita bisa tambahkan di bagian devDependencies pada package.json
- Atau gunakan perintah:

```bash
npm install namapackage --save-dev
```

- Untuk download dependency, sama seperti download production dependency, bisa gunakan perintah

```bash
npm install
```

# Install Dependency tanpa Development

- Secara default, saat menggunakan perintah npm install, semua dependency akan di install, termasuk development.
- Ada baiknya jika kita menjalankan aplikasi di production, kita tidak perlu menginstall development dependency, caranya bisa gunakan perintah:

```bash
npm install --production
```

**Selanjutnya :** [Package](package.md)