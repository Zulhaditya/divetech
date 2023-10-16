---
title: Test Async
tags:
  - jest
---

- Saat membuat kode program Javascript, penggunaan kode asynchronous pasti sering kita gunakan, baik menggunakan promise atau async await.
- Jest terintegrasi dengan baik jika kita ingin melakukan pengetesan terhadap kode async.
- Namun saat kita melakukan pengetesan kode async, sebelum melanjutkan ke unit test selanjutnya.
- Caranya sangat mudah, kita bisa gunakan async code di closure function jest.

```js
export const sayHelloAsync = (name) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (name) {
        resolve(`Hello ${name}`);
      } else {
        reject("Name is empty");
      }
    }, 1000);
  });
};
```

```js
import { sayHelloAsync } from ".../src/async.js";

test("test async function", async () => {
  const result = await sayHelloAsync("Zulhaditya");
  expect(result).toBe("Hello Zulhaditya");
});

export const sayHelloAsync = (name) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (name) {
        resolve(`Hello ${name}`);
      } else {
        reject("Name is empty");
      }
    }, 1000);
  });
};
```

# Regenerator Runtime Error

- Secara default babel tidak memiliki fitur untuk kompilasi runtime ketika menemukan fitur regenerator atau async function.
- Kita bisa menambahkan plugin untuk transform dan regenerator dengan menambahkan dependency.

```bash
npm install @babel/plugin-transform-runtime --save-dev
```

- Selanjutnya tambahkan di babel.config.json

```json
{
  "presets": ["@babel/preset-env"],
  "plugins": [
    [
      "@babel/plugin-transform-runtime",
      {
        "regenerator": true
      }
    ]
  ]
}
```

# Async Matchers

- Sebelunya kita menggunakan async await untuk melakukan matchers, sebenarnya Jest juga memiliki fitur matchers terhadap data async atau promise.
- Hal ini mempermudah kita ketika ingin melakukan matchers, sehingga tidak perlu melakukan await pada async function-nya.
- Semua async matchers mengembalikan promise.

**Selanjutnya :** [Setup Function](setupfunction.md)