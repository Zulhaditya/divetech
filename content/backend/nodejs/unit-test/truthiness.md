---
title: Truthiness
tags:
  - jest
---

- Dalam unit test, kita ingin membedakan antara nilai undefined, null, dan false.
- Kita juga ingin melakukan ekspetasi nilai tersebut.

```js
test("truthiness", () => {
  let value = null;

  expect(value).toBeNull();
  expect(value).toBeDefined();
  expect(value).toBeFalsy();

  value = undefined;

  expect(value).toBeUndefined();
  expect(value).toBeFalsy();
  value = "Aditya";

  expect(value).toBeTruthy();
  expect(value).toBe("Aditya");
});
```

**Selanjutnya :** [Numbers Matchers](numbersmatcher.md)