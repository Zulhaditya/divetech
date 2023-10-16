---
title: Threadpool
tags:
  - standard-library
---

# Threadpool

- Threadpool digunakan untuk memanajemen thread.
- Threadpool merupakan tempat dimana kita menyimpan thread, ketika kita butuh sebuah thread kita dapat mengambil dari threadpool, kita bisa kembalikan threadnya ke threadpool jika tidak digunakan lagi.
- Dengan threadpool, kita bisa memanfaatkan thread yang sama berkali-kali, tanpa harus membuat thread baru secara terus menerus.

# Threadpool Queue

- Jika semua thread penuh, kita tidak bisa lagi meminta thread ke threadpool. Kita harus menunggu sampai ada thread yang tidak sibuk.
- Dimana kita harus menunggu sampai ada thread yang bisa digunakan?
- Biasanya threadpool memiliki tempat untuk menyimpan tugas yang belum dikerjakan oleh thread di tempat bernama queue (antrian).
- Ketika kita mengirim perintah ke threadpool, perintah tersebut akan dikirim ke queue, lalu perintah tersebut akan dieksekusi satu persatu oleh thread yang tersedia di threadpool.

# Threadpool Web Model

- Dahulu, pembuatan web application sangat populer menggunakan threadpool model.
- Setiap request yang masuk ke web server akan diproses oleh satu buah thread.
- Dengan demikian ketika banyak request yang masuk, semua bisa diproses secara parallel karena akan ditangani oleh thread masing-masing.
- Namun, threadpool model ini memiliki kekurangan, ketika thread sedang sibuk semua, secara otomatis request selanjutnya harus menunggu sampai ada thread yang selesai melakukan tugas sebelumnya.
- Contoh web server yang menggunakan threadpool model, seperti Apache HTTPD, Apache Tomcat, dan lain-lain.

**Selanjutnya :** [Blocking dan Non-blocking](blocking.md)
