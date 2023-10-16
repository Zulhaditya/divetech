---
title: String Matchers
tags:
  - jest
---

- Jest juga memiliki matchers function yang digunakan untuk value string.
- Jika ingin memastikan sebuah string sama, kita bisa gunakan toBe() atau toEqual().
- Function .toMatch(regex) digunakan untuk memastikan value sesuai dengan regex.

```js
test("strings", () => {
  const name = "Muhammad Zulhaditya Hapiz";

  expect(name).toBe("Muhammad Zulhaditya Hapiz");
  expect(name).toEqual("Muhammad Zulhaditya Hapiz");
  expect(name).toMatch(/ditya/);
});
```

**Selanjutnya :** [Array Matchers](arraymatchers.md)