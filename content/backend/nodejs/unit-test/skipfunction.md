---
title: Skip Function
tags:
  - jest
---

- Saat membuat unit test, kita mendapatkan masalah di salah satu unit test, kita ingin meng-ignore unit test tersebut terlebih dahulu.
- Kita tidak perlu menambahkan komentar pada unit test tersebut.
- Kita bisa menggunakan skip function, yang secara otomatis akan menjadikan unit test tersebut ter-ignore dan tidak akan dieksekusi.
- https://jestjs.io/docs/api#testskipname-fn

```js
test("test 1", () => console.info("test 1"));
test("test 2", () => console.info("test 2"));
test.skip("test 3", () => console.info("test 3"));
test("test 4", () => console.info("test 4"));
test("test 5", () => console.info("test 5"));
```

**Selanjutnya :** [Only Function](onlyfunction.md)
