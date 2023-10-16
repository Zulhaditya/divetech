---
title: Numbers Matcher
tags:
  - jest
---

- Jest juga memiliki matchers yang digunakan untuk value berupa number.
- Ketika value bernilai number, kita bisa menggunakan toBe() dan toEqual(), untuk memastikan bahwa number bernilai sama dengan expected.

```js
test("numbers", () => {
  const value = 2 + 2;

  expect(value).toBeGreaterThan(3);
  expect(value).toBeGreaterThanOrEqual(4);
  expect(value).toBeLessThan(5);
  expect(value).toBeLessThanOrEqual(4);
  expect(value).toBe(4);
});
```

**Selanjutnya :** [String Matchers](stringmatchers.md)