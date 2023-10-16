---
title: Matchers
tags:
  - jest
---

- Saat kita membuat unit test, kita memiliki ekspetasi hasil akhir.
- Contoh, pada kode sum() sebelumnya, ketika kita memanggil function sum() dengan parameter 1 dan 2, ekspetasi kita adalah hasil return dari function sum() tersebut adalah 3.
- Di Jest, hal ini dinamakan Matchers.
- https://jestjs.io/docs/using-matchers

# Expect Function

- Matchers di Jest direpresentasikan dalam sebuah function bernama expect(value).
- Function expect() mengembalikan object Matchers, yang digunakan untuk testing value yang kita expect().
- Ada banyak sekali function untuk melakukan test di matchers, kita bisa baca detailnya di halaman dokumentasi API untuk function expect().
- https://jestjs.io/docs/expect

**Selanjutnya :** [Equal Matchers](equalmatchers.md)