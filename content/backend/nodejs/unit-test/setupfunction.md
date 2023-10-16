---
title: Setup Function
tags:
  - jest
---

- Saat membuat unit test, kita membuat kode yang perlu dibuat sebelum unit test berjalan.
- Kita juga bisa membuat kode yang diperlukan setelah unit test berjalan.
- Jest memiliki fitur untuk menangani kasus seperti ini.

```js
import { sum } from "../src/sum.js";

beforeAll(() => {
  console.info("Before All");
});

afterAll(() => {
  console.info("After All");
});

beforeEach(() => {
  console.info("Before Each");
});

afterEach(() => {
  console.info("After Each");
});

test("first test", () => {
  expect(sum(10, 10)).toBe(20);
  console.info("First Test");
});

test("second test", () => {
  expect(sum(10, 10)).toBe(20);
  console.info("Second Test");
});
```

# One-Time Setup Function

- Namun terkadang kita ingin membuat kode yang hanya dieksekusi sekali saja dalam sebuah file unit test.
- Sekali sebelum semua unit test.
- Dan sekali setelah semua unit test.
- Jest juga menyediakan fitur tersebut.

**Selanjutnya :** [Scoping](scoping.md)