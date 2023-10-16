---
title: Mock Matchers
tags:
  - jest
---

- Sebelumnya untuk mengecek berapa kali mock function dipanggil, atau apa parameter yang diterima oleh mock function, kita lakukan secara manual dengan mengecek data di mock property.
- Jest sendiri menyediakan fitur matchers untuk mock, dimana kita bisa melakukan matchers dengan lebih mudah dibandingkan secara manual.

```js
import { calculate } from "../src/sum.js";

test("test mock matchers", () => {
  const callback = jest.fn();

  calculate([10, 10, 10], callback);
  calculate([10, 10, 10, 10, 10], callback);

  expect(callback).toHaveBeenCalled();
  expect(callback).toHaveBeenCalledTimes(2);

  expect(callback).toHaveBeenCalledWith(30);
  expect(callback).toHaveBeenCalledWith(50);
});
```

**Selanjutnya :** [Mock Modules](mockmodules.md)