---
title: Equal Matchers
tags:
  - jest
---

- Salah satu Matchers yang biasa digunakan ketika membuat unit test adalah equals matchers.
- Digunakan untuk memastikan bahwa data sesuai atau sama dengan ekspetasi kita.

```js
test("test toBe", () => {
  const name = "Inayah";

  const hello = `Hello ${name}`;
  expect(hello).toBe("Hello Inayah");
});

test("test toEqual", () => {
  let person = { id: "Zulhaditya" };

  Object.assign(person, { name: "Hapiz" });
  expect(person).toEqual({ id: "Zulhaditya", name: "Hapiz" });
});
```

**Selanjutnya :** [Truthiness Matchers](truthiness.md)