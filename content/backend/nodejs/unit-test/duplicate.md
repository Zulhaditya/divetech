---
title: Duplicate
tags:
  - jest
---

- Salah satu kesalahan yang biasa dilakukan adalah membuat unit test yang duplicate.
- Biasanya akan melakukan duplicate unit test, hanya karena data yang di test-nya saja yang berbeda.

```js
import { sumAll } from "../src/sum.js";

const table = [
  [[10, 10, 10], 30],
  [[10, 10, 10, 10, 10], 50],
  [[10, 10, 10, 10, 10, 10, 10], 70],
  [[20, 30, 30, 20], 100],
];

test.each(table)("test sumAll(%s) should result %i", (numbers, expected) => {
  expect(sumAll(numbers)).toBe(expected);
});
```

# Object Sebagai Data

- Saat menggunakan array, jika terlalu banyak parameternya, maka akan membingungkan.
- Each function juga bisa menggunakan data Object, namun kita perlu melakukan destructuring.

```js
const data = [
  {
    numbers: [],
    expected: 0,
  },
  {
    numbers: [10, 10],
    expected: 20,
  },
  {
    numbers: [10, 20, 20],
    expected: 50,
  },
];

test.only.each(data)(
  "test sumAll(%s) should result %i",
  ({ numbers, expected }) => {
    expect(sumAll(numbers)).toBe(expected);
  }
);
```

**Selanjutnya :** [Concurrent Test](concurrent.md)