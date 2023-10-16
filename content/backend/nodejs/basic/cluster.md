---
title: Cluster
tags:
  - standard-library
---

- Node.js berjalan secara single thread, kecuali jika kita membuat manual threadnya menggunakan worker thread, tapi tetap dalam satu process.
- Node.js memiliki standard library Cluster yang digunakan untuk menjalankan beberapa process Node.js secara bersamaan.
- Ini sangat cocok digunakan ketika menggunakan CPU yang multicore, sehingga semua core bisa kita utilisasi dengan baik, misalkan kita menjalankan process Node.js sejumlah CPU core.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/cluster.html

# Cluster Primary dan Worker

- Didalam Cluster, terdapat 2 jenis aplikasi, Primary dan Worker.
- Primary biasanya digunakan sebagai koordinator atau manajer untuk para Worker.
- Sedangkan Worker sendiri adalah aplikasi yang menjalankan tugasnya.
