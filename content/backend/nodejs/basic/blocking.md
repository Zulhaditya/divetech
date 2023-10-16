---
title: Blocking dan Non-blocking
tags:
  - basic
---

# Blocking / Synchronous

- Saat kita membuat kode program, secara default kode program akan berjalan secara blocking atau synchronous.
- Artinya, kita harus menunggu sebuah kode selesai sebelum kode selanjutnya dieksekusi.
- Contoh, ketika kita membuat kode program untuk membaca file, jika kode kita blocking, maka kita harus menunggu program selesai membaca file, baru kita bisa melanjutkan kode program selanjutnya.

# Non Blocking / Asynchronous

- Non blocking berbeda dengan blocking, kode program non blocking akan dieksekusi tanpa harus menunggu kode program tersebut selesai.
- Non blocking akan dijalankan secara asynchronous.
- Ketika memanggil kode non blocking, biasanya kita perlu mengirimkan callback untuk dipanggil oleh kode non blocking tersebut ketika kodenya sudah selesai.
- Contoh kode non blocking adalah Javascript async, AJAX, Fetch API, dan lain-lain.
- Node.js mendukung semua fitur kode non-blocking.

**Selanjutnya :** [Global Async](globalasync.md)