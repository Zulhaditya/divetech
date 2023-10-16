---
title: Global Async
tags:
  - basic
---

- Saat kita belajar Javascript, untuk menggunakan Async Await, biasanya kita perlu membuat function yang kita tandai sebagai Async.
- Saat menggunakan module, secara default, global code adalah Async, oleh karena itu kita bisa menggunakan Async Await.
- Kecuali jika kita membuat function, maka function tersebut harus kita tandai sebagai Async jika ingin menggunakan Async Await.

```js
// async.mjs
function samplePromise() {
  return Promise.resolve("Zulhaditya");
}

const name = await samplePromise();
console.info(name);
```

**Selanjutnya :** [Standard Library](standardlib.md)