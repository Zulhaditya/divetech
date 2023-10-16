---
title: Failing Function
tags:
  - jest
---

- Dalam membuat unit test, jangan hanya membuat skenario sukses.
- Kadang kita juga perlu membuat skenario gagal, atau ekspektasi gagal, contoh misalkan ketika mengirim data tidak valid, maka kita berharap kalau kodenya terjadi error.
- Pada kasus ini, Jest menyediakan fitur Failing Function.
- https://jestjs.io/docs/api#testfailingname-fn-timeout

```js
import { sayHello } from "../src/sayHello.js";

test("sayHello success", () => {
  expect(sayHello("Zulhaditya")).toBe("Hello, Zulhaditya");
});

test.failing("sayHello error", () => {
  expect(sayHello(null));
});

test("sayHello error matchers", () => {
  expect(() => sayHello(null)).toThrow();
});
```

**Selanjutnya :** [Mock](mock.md)
