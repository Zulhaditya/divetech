---
title: Exception Matchers
tags:
  - jest
---

- Saat membuat kode program, kita sering membuat exception.
- Dalam unit test pun, kita berharap sebuah exception terjadi.
- Jest memiliki matchers untuk melakukan pengecekan exception.
- Khusus untuk jenis matchers exception, kita perlu menggunakan closure function di value expect() nya, hal ini untuk memastikan exception ditangkap oleh matchers, jika tidak menggunakan closure function, maka exception akan terlanjur terjadi sebelum kita memanggil expect() function.
- Untuk melakukan exceptions matchers, buat terlebih dahulu function yang akan diuji:

```js
export class MyException extends Error {}

export const callMe = (name) => {
  if (name === "zulhaditya") {
    throw new MyException("Ups my exceptions happens");
  } else {
    return "OKE";
  }
};
```

- Lalu buat kode program unit test-nya.

```js
import { MyException, callMe } from "../src/exception.js";

test("exception", () => {
  expect(() => callMe("zulhaditya")).toThrow();
  expect(() => callMe("zulhaditya")).toThrow(MyException);
  expect(() => callMe("zulhaditya")).toThrow("Ups my exceptions happens");
});
```

**Selanjutnya :** [Not Matchers](notmatchers.md)