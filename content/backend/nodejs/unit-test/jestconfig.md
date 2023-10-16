---
title: Jest Config
tags:
  - jest
---

- Jest memiliki banyak konfigurasi, namun jika kita tidak ubah konfigurasinya, Jest sudah memiliki default konfigurasi.
- Ada banyak sekali konfigurasi yang terdapat di Jest

# File Konfigurasi Jest

Jest mendukung 2 cara untuk menyimpan data konfigurasi:

1. Menyimpan di file package.json dengan key jest.
2. Menyimpan sebagai file javascript di file jest.config.js/ts/mjs, atau membuatnya secara otomatis dengan perintah:

```bash
jest --init
```

- Jika menggunakan konfigurasi file jest.config.js/ts/mjs, jangan lupa untuk memindahkan konfigurasi jest di package.json

# Pengaturan Konfigurasi

- Konfigurasi di Jest sangat sederhana, cukup gunakan key-value.
- Kita bisa lihat konfigurasi key yang tersedia dan kegunaannya di halaman
- https://jestjs.io/docs/configuration

**Selanjutnya :** [Jest CLI](jestcli.md)