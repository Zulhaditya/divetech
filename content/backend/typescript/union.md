---
title: Union Type
tags:
  - typescript
---

# Union Type

- Seperti yang kita pelajari, JavaScript sebenarnya bisa menyimpan berbagai jenis tipe data di variable yang sama.
- Namun pada TypeScript, hal itu dilarang karena merupakan praktek penulisan kode yang buruk.
- Pada kasus jika kita ingin membuat variable yang bisa berubah bentuk tipe data, kita bisa memberitahunya menggunakan **union type**.
- Secara otomatis, TypeScript membolehkan kita mengubah tipe data, namun sesuai yang sudah ditentukan di union type-nya.

## Kode: Union Type

```js
let sample: number | string | boolean = "Nay";
sample = 100;
sample = true;

console.info(sample);
```

# Menggunakan Union

- Saat menggunakan **Union Type**, kita perlu berhati-hati ketika memanggil method terhadap variable tersebut.
- Hal ini karena tipe datanya bisa berubah, oleh karena itu ada baiknya kita melakukan pengecekan tipe data terlebih dahulu menggunakan **typeof**.

**Selanjutnya** : [Alias](/backend/typescript/alias.md)
