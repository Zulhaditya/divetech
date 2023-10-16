---
title: Create
tags:
  - jest
---

- Jest sudah menyediakan function yang diregistrasikan secara global bernama test(), function tersebut digunakan untuk membuat unit test.
- test() memiliki parameter nama unit test dan juga function yang berisi kode unit test-nya.

# Langkah untuk membuat unit test

1. Buat terlebih dahulu function yang ingin dilakukan testing.

```js
// src/sum.js
export const sum = (first, second) => {
  return first + second;
};
```

2. Setelah membuat function atau method yang ingin diuji, buat file unit test-nya.

```js
import { sum } from "../src/sum.js";

test("test sum function", () => {
  const result = sum(1, 2);
  expect(result).toBe(3);
});
```

3. Untuk melakukan unit test jalankan perintah:

```bash
npx jest
```

4. Setelah menjalankan perintah diatas, akan terdapat error seperti dibawah ini yang disebabkan saat ini Jest belum support untuk javascript module.

**Selanjutnya :** [Intro Babel](introbabel.md)
