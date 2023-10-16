---
title: Mock Function
tags:
  - jest
---

- Jest bisa digunakan untuk membuat mock function.
- Kita bisa membuat tiruan dari sebuah function.
- Salah satu fitur mock function adalah kita dapat melihat detail dari parameter yang digunakan untuk memanggil mock function tersebut.
- Untuk membuat mock function kita bisa menggunakan jest.fn()
- https://jestjs.io/docs/mock-function-api#jestfnimplementation

```js
export const calculate = (numbers, callback) => {
  let total = 0;
  for (let number of numbers) {
    total += number;
  }
  callback(total);
};
```

```js
import { calculate } from "../src/sum.js";

test("test calculate", () => {
  const callback = jest.fn();

  calculate([10, 10, 10], callback);
  calculate([10, 10, 10, 10, 10], callback);
});
```

# Mock Property

- Saat menggunakan Mock, kita ingin melihat parameter apa yang digunakan untuk memanggil Mock.
- Atau return value apa yang dikembalikan oleh Mock Function.
- Kita bisa menggunakan property Mock dari Mock Function untuk melihatnya.
- https://jestjs.io/docs/mock-function-api#mockfnmockcalls
- https://jestjs.io/docs/mock-function-api#mockfnmockresults

```js
import { calculate } from "../src/sum.js";

test("test calculate", () => {
  const callback = jest.fn();

  calculate([10, 10, 10], callback);
  calculate([10, 10, 10, 10, 10], callback);

  expect(callback.mock.calls.length).toBe(2);

  console.info(callback.mock.calls);

  expect(callback.mock.calls[0][0]).toBe(30);
  expect(callback.mock.calls[1][0]).toBe(50);
});
```

# Mock Return Value

- Kadang ada kasus dimana kita ingin membuat mock function dengan return value yang sudah ditentukan.
- Namun jika pada kasus sederhana tanpa logic, kita bisa membuat return value dengan mudah pada mock function.
- Kita bisa memanfaatkan function mockReturnValue(returnValue) atau mockReturnValueOnce(returnValue).
- https://jestjs.io/docs/mock-function-api#mockreturnvaluevalue
- https://jestjs.io/docs/mock-function-api#mockfnmockreturnvalueoncevalue

```js
test("test mock return value", () => {
  const callback = jest.fn();

  callback.mockReturnValueOnce(40);
  callback.mockReturnValueOnce(80);

  expect(calculateAndReturn([10, 10, 10], callback)).toBe(40);
  expect(calculateAndReturn([10, 10, 10], callback)).toBe(80);

  expect(callback.mock.results[0].value).toBe(40);
  expect(callback.mock.results[1].value).toBe(80);
});
```

# Mock Implementation

- Mock Implementation digunakan untuk implementasi logic dari sebuah mock function dan dapat mengubah return value dari mock function secara dinamis.
- Kita bisa menggunakan mockImplementation() atau mockImplementationOnce()
- https://jestjs.io/docs/mock-function-api#mockfnmockimplementationfn
- https://jestjs.io/docs/mock-function-api#mockfnmockimplementationoncefn

```js
test("test mock implementation", () => {
  const callback = jest.fn();

  callback.mockImplementation((total) => {
    return total * 2;
  });

  expect(calculateAndReturn([10, 10, 10], callback)).toBe(60);
  expect(calculateAndReturn([10, 10, 10, 10, 10], callback)).toBe(100);

  expect(callback.mock.results[0].value).toBe(60);
  expect(callback.mock.results[1].value).toBe(100);
});
```

**Selanjutnya :** [Mock Matchers](mockmatchers.md)