---
title: Concurrency
tags:
  - basic
---

# Sejarah

- Dahulu, komputer hanya menjalankan sebuah program pada satu waktu.
- Karena hanya bisa menjalankan satu program pada satu waktu, hal tersebut sangat tidak efisien dan memakan waktu yang lama karena hanya bisa mengerjakan satu tugas pada satu waktu.
- Semakin berkembangnya teknologi sistem operasi pada komputer memungkinkan program bisa dijalankan secara bersamaan dalam proses yang berbeda-beda, terisolasi, dan saling independen antar program.

# Thread

- Program biasanya dijalankan dalam sebuah proses, dan proses tersebut memiliki resource yang independen dengan proses lain.
- Sekarang, sistem operasi tidak hanya menjalankan multiple proses, namun dalam proses tersebut kita bisa menjalankan banyak pekerjaan sekaligus, atau bisa dibilang proses ringan lebih dikenal sebagai thread.
- Thread membuat proses aplikasi berjalan tidak harus secara sequential, kita bisa membuat proses aplikasi berjalan secara asynchronous atau parallel.

# Concurrency vs Parallel

- Concurrency artinya mengerjakan beberapa pekerjaan satu persatu.
- Parallel artinya mengerjakan beberapa pekerjaan sekaligus pada satu waktu.

## Contoh concurrency dan parallel

- Browser adalah aplikasi yang concurrent dan parallel.
- Browser melakukan proses concurrent ketika membuka web, browser akan melakukan http request, lalu mendownload semua file resource (html, css, js) lalu merender dalam bentuk tampilan website.
- Browser akan melakukan proses parallel, ketika kita membuka beberapa tab web, dan juga sambil download file, dan menonton video dari streaming.

# Synchronous vs Asynchronous

- Synnchronous adalah ketika kode program berjalan secara berurutan atau sequential, dan semua tahapan ditunggu sampai prosesnya selesai baru akan dieksekusi ke tahapan selanjutnya.
- Asynchronous adalah ketika kode program berjalan kita tidak perlu menunggu eksekusi kode tersebut selesai, kita bisa melanjutkan ke tahapan kode program selanjutnya.

**Selanjutnya :** [Threadpool Web Model](threadpool.md)
