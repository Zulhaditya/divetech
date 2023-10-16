---
title: Module
tags:
  - basic
---

## Definisi Modules

Sekumpulan code yang dapat digunakan kembali dengan antarmuka yang terdefinisi.

## Node Modules

- Fungsionalitas yang simple dan kompleks yang tersimpan di sebuah file Javascript yang dapat kita gunakan kembali pada aplikasi NodeJS.
- Setiap modul memiliki konteks atau keperluan masing-masing, tidak bisa saling tercampur dengan modul lain pada lingkup global.

Terdapat tiga tipe modules di NodeJS yaitu: 1. Core Modules : Modules yang sudah dimiliki NodeJS di librarynya (bawaan). 2. Local Modules : Modules yang kita bikin sendiri. Melakukan exports dan require. 3. Third Party Modules : NPM Modules, modules yang dibuat oleh orang lain.

Fungsi require() adalah mencari modul dengan urutan sebagai berikut: 1. Core Modules 2. File atau direktori ( ./ atau / atau ../ ) 3. Folder 'node_modules'

## Example:

```js
// index.js

// import core modules
const fs = require('fs');

// import local modules
const coba = require('coba');

// import third party modules / npm modules -> folder node_modules
const moment = require('moment');

console.log(
  coba.cetakNama("Zulhaditya");
  coba.PI,
  coba.mahasiswa.cetakMhs(),
  new coba.Orang(),
  coba.PIHelo,
);
```

```js
// coba.js

// function cetak nama
function cetakNama(nama){
	return `Halo, nama saya ${nama}`;
}

// variabel PI
PI = 3.14;

// objek literal mahasiswa
const mahasiswa = {
  nama: 'Inayah Wulandari',
  umur: 22,
  cetakMhs(){
    return `Halo, nama saya ${this.nama}, umur ${this.umur}`;
  }
}

// class
class Orang(){
  constructor(){
    console.log('Objek orang telah dibuat!');
  }
}

// export modules

// cara-1
module.exports.cetakNama = cetakNama;
module.exports.PI = PI;
module.exports.mahasiswa = mahasiswa;
module.exports.Orang = Orang;

// cara-2 -> dijadikan objek
module.exports = {
  cetakNama : cetakNama,
  PI : PI,
  mahasiswa : mahasiswa,
  Orang : Orang,
}

// cara-3 -> objek secara langsung karena penamaan value dan objek sama
module.exports = {cetakNama, PI, mahasiswa, Orang};
```

**Selanjutnya :** [Concurrency](concurrency.md)
