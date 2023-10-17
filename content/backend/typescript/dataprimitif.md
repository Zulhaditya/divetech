---
title: Tipe Data Primitif
tags:
  - typescript
---

# Tipe Data Primitif

Tipe data primitif di TypeScript sama seperti JavaScript, yang membedakannya adalah kita harus mendeklarasikan tipe data yang digunakan. Saat kita sudah menentukan satu tipe data maka kita tidak bisa ubah menjadi tipe data yang lainnya.

# Deklarasi Variable

- Karena TypeScript adalah **Strongly Type Language**, oleh karena itu saat kita membuat variable, kita harus menentukan tipe data yang digunakan.
- Jika sudah menentukan tipe datanya, kita tidak boleh mengubah variable tersebut menjadi tipe data yang berbeda.
- TypeScript bisa secara otomatis menentukan tipe data yang digunakan, namun kita dapat menentukan secara eksplisit menggunakan:

```js
const namaVariable: tipedata = value;
```

# Kode: Tipe Data Primitif

```js
const name: string = "Zulhaditya";
const balance: number = 700000;
const isVip: boolean = true;

console.info(name);
console.info(balance);
console.info(isVip);
```

**Selanjutnya** : [Babel TypeScript](/backend/typescript/babelts.md)
