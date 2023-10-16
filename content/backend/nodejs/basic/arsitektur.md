---
title: Arsitektur
tags:
  - basic
---

- NodeJS merupakan **runtime environment** untuk mengeksekusi kode Javascript
- Javascript itu awalnya hanya bisa diakses menggunakan **browser**
- Setiap browser memiliki Javscript engine masing-masing seperti Chrome dengan V8 dan Firefox dengan SpiderMonkey
- NodeJS dibuat menggunakan V8 Engine dari Chrome karena perilaku sesuai dengan apa yang diharapkan dan juga paling cepat

# Cara kerja

```js
// contoh synchronous
const getData = (id) => {
  const nama = id === 1 ? "Zulhaditya" : "Hapiz";
  return { id, nama };
};

const data = (id) => {
  console.log(halo);
};

const getUserSatu = getData(1);
console.log(getUserSatu);

const getUserDua = getData(2);
console.log(getUserDua);

const nama = "Hello";
console.log(nama);
```

```js
// contoh asynchronous
const getName = (id, cb) => {
  const time = id === 1 ? 3000 : 2000;
  setTimeout(() => {
    const name = id === 1 ? "Zulhaditya" : "Inayah";
    cb({ id, name });
  }, time);
};

const anggotaSatu = getName(1, (hasil) => {
  console.log(hasil);
});

const anggotaDua = getName(2, (hasil) => {
  console.log(hasil);
});
```

# Web Application

- Web application adalah aplikasi yang berjalan di sisi server dan ditampilkan di browser client.
- Saat membuat web application, biasanya akan dibagi menjadi 3 bagian yaitu Client, Server, dan Database.

# Alur Web Application

- Client -> Server -> Database

## Client

- Client merupakan user interface atau bagian frontend dari web application.
- Client digunakan untuk berinteraksi dengan server, baik itu mengirim data atau menerima data.
- Frontend biasanya dibuat menggunakan HTML, CSS, dan Javascript.

## Server

- Server bertanggung jawab untuk menerima request dari client, mengerjakan request yang dikirimkan dan membalas request berupa response ke client.
- Server bertugas sebagai backend untuk web app, dimana semua logic aplikasi akan dilakukan di server.
- Biasanya server dibuat menggunakan PHP, Python, Java, .NET dan banyak bahasa pemrograman lainnya.
- Dengan adanya Node.js, sekarang kita bisa membuat server menggunakan Javascript.

## Database

- Database adalah tempat untuk menyimpan data web application.
- Data disimpan dan diambil oleh server.
- Client tidak bisa langsung mengambil atau menyimpan data ke database secara langsung, oleh karena itu dibutuhkan penengah yakni server untuk mengelola aktivitas tersebut.
- Database biasanya menggunakan aplikasi sistem basis data seperti MySQL, PostgreSQL, MongoDB, dan lain-lain.

# Event-Loop

- Event-Loop merupakan single thread proses yang digunakan untuk mengeksekusi kode non-blocking.
- Karena Event-Loop hanya menggunakan single thread, maka kita harus berhati-hati ketika membuat blocking code, karena bisa memperlambat proses eksekusi kode.
- Event-Loop sendiri bertugas untuk menerima dan mengirim eksekusi kode ke C++ Threadpool, oleh karena itu selalu usahakan menggunakan kode non-blocking agar proses blocking-nya dikerjakan di C++ Threadpool.
- Event-Loop akan menerima response dari C++ Threadpool yang dikirim via callback dan dilakukan secara otomatis oleh Node.js.

# C++ Threadpool

- Node.js menggunakan C++ Threadpool untuk workernya, yaitu threadpool untuk melakukan pekerjaan.
- Libuv adalah library yang digunakan di Node.js, dimana secara default libuv menggunakan 4 thread didalam threadpool-nya, hal ini menjadikan kita bisa melakukan 4 pekerjaan blocking sekaligus dalam satu waktu.
- Jika terlalu banyak pekerjaan blocking, kita bisa mengubah jumlah thread di libuv dengan pengaturan environment variable UV_THREADPOOL_SIZE.

**Selanjutnya :** [Node REPL](repl.md)
