---
title: Package
tags:
  - npm
---

# Create Package

- Kita akan coba membuat library lalu di upload ke https://npmjs.com

```js
export const sayHello = (name) => {
  return `Halo, ${name}`;
};

export const sum = (numbers) => {
  let total = 0;

  for (const number of numbers) {
    total += number;
  }

  return total;
};
```

# Publish Package

## Login ke Web NPM

- Setelah membuat library/package, selanjutnya kita perlu login terlebih dahulu ke Website NPM menggunakan perintah NPM.
- Kita bisa gunakan perintah

```bash
npm adduser
```

- Setelah melakukan login, maka untuk mengupload library kita, gunakan perintah:

```bash
npm publish
```

# Install Package

- Setelah library yang kita buat telah di publish ke npm, selanjutnya kita bisa install package tersebut di project yang kita inginkan.
- Caranya sama seperti menginstall dependency yang lain.

# Upgrade Package

- Untuk melakukan upgrade package yang sudah kita buat sebelumnya, caranya sangat mudah, cukup melakukan update version di package.json
- Lakukan upgrade package dengan mengikuti aturan semantic version.

## Aturan Semantic Version

- Jika melakukan bugfix, tidak ada code break, upgrade versi PATCH.
- Jika menambah fitur, tidak ada code break, upgrade versi MINOR.
- Jika mengubah fitur, dan melakukan code break, upgrade versi MAJOR.
- Setelah melakukan perubahan package, dan yakin dengan perubahannya, kita bisa melakukan publish package lagi.
- Gunakan perintah:

```bash
npm publish
```

# Update Dependency

- Untuk melakukan update dependency, kita harus mengubah versi dari dependency.
- Jika sudah menggunakan version ~ atau ^ , maka bisa secara otomatis melakukan update dengan menggunakan perintah:

```bash
npm update namapackage
```

- Atau jika ingin update semua dependency, gunakan perintah:

```bash
npm update
```

**Selanjutnya :** [Ignore File](ignorefile.md)