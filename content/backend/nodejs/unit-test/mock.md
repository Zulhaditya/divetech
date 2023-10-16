---
title: Mock
tags:
  - jest
---

- Saat membuat unit test, kadang kita terkendala di bagian kode yang sulit di test.
- Misalkan terdapat kode yang melakukan interaksi dengan sistem lain, misalnya database, message broker, third party web service, dan lain-lain.
- Jika kita melakukan unit test dengan berinteraksi secara langsung, maka akan sulit untuk konsisten. Misalkan unit test pertama sukses, ketika dijalankan lagi, ternyata gagal karena data sudah terinput ke dalam sistem ataupun database.
- Pada kasus ini, kita harus melakukan Mocking.

# Mock

- Dalam pemrograman, Mock Object adalah object tiruan yang kita buat dan memiliki tingkah laku menyerupai dengan object yang aslinya.
- Salah satu fitur Mock Object adalah kita bisa memberitahu tingkah laku dari object tersebut sesuai dengan yang kita inginkan.
- Mock Object ini sangat cocok digunakan ketika kita melakukan unit test yang berhubungan dengan sistem lain, sehingga kita tidak perlu berinteraksi dengan sistem lain tersebut.

## Jenis Mock

- Mock Function, yang bisa kita gunakan untuk membuat tiruan dari sebuah function.
- Mock Class, yang bisa kita gunakan untuk membuat tiruan dari object class.
- Mock Modules, yang digunakan untuk membuat tiruan modules.

**Selanjutnya :** [Mock Function](mockfunction.md)