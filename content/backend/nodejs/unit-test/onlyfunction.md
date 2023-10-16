---
title: Only Function
tags:
  - jest
---

- Ketika kita ingin melakukan proses debugging di unit test pada sebuah file yang unit test-nya banyak, kadang kita ingin fokus ke unit test tertentu.
- Jika ingin menggunakan skip unit test yang lain, maka akan sulit jika terlalu banyak.
- Kita bisa menggunakan only function, untuk memaksa dalam file tersebut, hanya unti test yang ditandai dengan only yang akan dieksekusi.
- https://jestjs.io/docs/api#testonlyname-fn-timeout

```js
test("test 1", () => console.info("test 1"));
test("test 2", () => console.info("test 2"));
test.only("test 3", () => console.info("test 3"));
test("test 4", () => console.info("test 4"));
test("test 5", () => console.info("test 5"));
```

**Selanjutnya :** [Duplicate Unit Test](duplicate.md)
