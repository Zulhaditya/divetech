---
title: Dependency
tags:
  - npm
---

- Salah satu fitur yang sangat berguna di NPM adalah dependency management.
- Saat membuat aplikasi kita akan membutuhkan dependency ke library atau package pihak lain, misalkan package open source, atau package yang kita buat sendiri.
- NPM mendukung dependency management, sehingga kita tidak perlu download package secara manual, termasuk melakukan update secara manual ketika ada update terbaru.

# npmjs.com

- Secara default, NPM akan download dependency dari website:
- https://www.npmjs.com/
- Kita bisa mendownload package atau membuat open source package.
- Untuk menginstall dependency, kita bisa gunakan perintah:

```bash
npm install namadependency@version
```

- Atau bisa langsung tulis di dependency pada package.json

# Download Dependency

- Untuk download dependency, kita bisa gunakan perintah: npm install
- Secara otomatis NPM akan download package yang ada di dependency kedalam folder node_modules.
- Selain itu, NPM akan membuat file package-lock.json yang berisikan informasi versi package yang di download, ini untuk mempermudah ketika kita melakukan download ulang library di komputer lain.

**Selanjutnya :** [Dependency Version](dependencyversion.md)