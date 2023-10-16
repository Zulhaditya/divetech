---
title: Debugger
tags:
  - standard-library
---

- Node.js memiliki fitur debugger, dimana kita bisa mengikuti tahapan eksekusi program di Node.js
- Hal ini sangat cocok ketika kita melakukan proses debugging, mencari sebab masalah yang terjadi di aplikasi kita.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/debugger.html

# Breakpoint

- Dalam debugging, terdapat istilah breakpoint, yaitu lokasi dimana kita ingin menghentikan sementara eksekusi kode program.
- Biasanya ini dilakukan untuk mengawasi data-data di sekitar lokasi berhentinya.
- Untuk menambahkan breakpoint, kita bisa menggunakan kata kunci: debugger.

# Menjalankan Mode Debug

- Jika kita menjalankan file Javscript hanya dengan menggunakan perintah node namafile.js, maka secara default tidak akan berjalan dalam mode debug.
- Agar jalan dalam mode debug, kita harus menambahkan perintah inspect: node inspect namafile.js

# Perintah Debugger

Saat masuk ke mode debug, ada beberapa perintah yang bisa digunakan dalam melakukan debugging.

- cont, c: Continue execution
- next, n: Step next
- step, s: Step in
- out, o: Step out
- pause : Pause running code

```js
function sayHello(name) {
  debugger;
  return `Halo, ${name}`;
}

const name = "Zulhaditya";
console.info(sayHello(name));
```

**Selanjutnya :** [DNS](dns.md)
