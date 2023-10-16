---
title: Array Matchers
tags:
  - jest
---

- Jest memiliki function yang digunakan untuk mengecek data didalam sebuah array.
- Jika ingin memastikan bahwa array memiliki value yang sama, kita bisa menggunakan toEqual().

```js
test("array simple", () => {
  const names = ["Inayah", "Fitri", "Wulandari"];
  expect(names).toEqual(["Inayah", "Fitri", "Wulandari"]);
  expect(names).toContain("Wulandari");
});

test("array object", () => {
  const persons = [
    {
      name: "Zulhaditya",
    },
    {
      name: "Hapiz",
    },
  ];
  expect(persons).toContainEqual({
    name: "Zulhaditya",
  });
});
```

**Selanjutnya :** [Exceptions Matchers](exceptionmatchers.md)