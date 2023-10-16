---
title: Intro Babel
tags:
  - jest
---

# Kekurangan Jest

- Jest belum support javascript modules dan masih menggunakan cara lama yaitu menggunakan commonjs dengan memanfaatkan function require().
- Untungnya, ada library Babel yang bisa digunakan untuk membantu pembuatan unit test menggunakan jest dengan menerapkan javascript modules.

# Jest Code Transformation

- Jest mendukung code transformation, yaitu fitur pengubahan kode program sebelum dijalankan oleh Jest.
- Fitur ini dimanfaatkan untuk melakukan kompilasi ke kode javascript yang bisa dimengerti oleh Jest, dengan memanfaatkan library Babel.
- https://jestjs.io/docs/code-transformation

# Babel

- Babel adalah javascript compiler, yang digunakan untuk melakukan kompilasi kode javascript ke kode javascript yang beda versinya, biasanya untuk konversi ke versi lama agar kompatibel dengan browser versi lama.
- Dengan Babel, kita bisa membuat kode program javascript terbaru seperti modules dapat di compile menjadi kode javascript lama sehingga kompatibel ketika dijalankan oleh teknologi lama yang belum mendukung fitur javascript terbaru.
- https://babeljs.io

## Integrasi Babel dan Jest

- Jest terintegrasi baik dengan babel, sehingga kita bisa secara otomatis melakukan kompilasi kode javascript unit test dengan babel, dan menjalankan kode javascript dengan versi yang kompatibel dengan jest.
- https://babeljs.io/setup
- Install babel-jest dengan perintah dibawah ini:

```bash
npm install --save-dev babel-jest
```

- Selanjutnya ubah package.json seperti ini:

```json
{
  "scripts": {
    "test": "jest"
  },
  "jest": {
    "transform": {
      "^.+\\.[t|j]sx?$": "babel-jest"
    }
  }
}
```

- Langkah selanjutnya adalah membuat file babel.config.json untuk konfigurasi babel.

```json
{
  "presets": ["@babel/preset-env"]
}
```

- Langkah terakhir adalah instalasi library preset-env.

```bash
npm install @babel/preset-env --save-dev
```

- Jalankan lagi unit test-nya.

```bash
npx jest
```

- Unit test telah berhasil menjalankan pengujian, ditunjukkan pada gambar dibawah ini:

**Selanjutnya :** [Jest Config](jestconfig.md)