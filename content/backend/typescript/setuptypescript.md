---
title: Setup TypeScript
tags:
  - typescript
---

# 1. Install TypeScript

Install library TypeScript pada development karena TypeScript hanya digunakan pada tahap development saja, tidak untuk produksi karena saat dicompile akan menghasilkan kode JavaScript. Lakukan perintah ini untuk instalasi TypeScript:

```bash
npm install --save-dev typescript
```

# 2. Setup TypeScript

Lakukan instalasi library TypeScript Compiler dengan perintah:

```bash
npx tsc --init
```

Lalu, semua konfigurasi akan dibuat didalam file **tsconfig.json**. Selanjutnya, ubah "module" dari "commonjs" menjadi "ES6".

# 3. Setup Jest untuk TypeScript

Kunjungi https://jestjs.io/docs/getting-started#using-typescript untuk informasi selanjutnya, ikuti saja dokumentasi yang diberikan pada website **Jest** tersebut. Setelah selesai mengikuti instruksi yang diberikan maka project TypeScript kita sudah bisa digunakan, Yeaay!

# 4. Testing

Kita bisa melakukan testing apakah **Jest** sudah bisa digunakan pada project kita, yaitu dengan membuat sebuah folder **tests** dan didalamnya buat file **hello.test.ts**, Lalu isi dengan kode berikut:

```js
describe("Hello", function () {
  it("should say hello world", function () {
    const name = "Hello World";
    expect(name).toBe("Hello World");
  });
});
```

Selanjutnya, buka terminal dan jalankan perintah:

```bash
npx jest
```

**Selanjutnya** : [Hello Function](/backend/typescript/hellofunction.md)
