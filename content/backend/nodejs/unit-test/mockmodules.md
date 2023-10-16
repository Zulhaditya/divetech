---
title: Mock Modules
tags:
  - jest
---

- Saat membuat aplikasi, sudah pasti kita sering menggunakan JS Module, baik itu yang kita buat sendiri atau JS Module opensource.
- Jest juga bisa digunakan untuk melakukan mock terhadap modules.

# Melakukan Mock Modules

- Kita bisa gunakan function jest.mock(module)
- Secara otomatis ketika kita import dari module tersebut, maka jest akan melakukan mock.
- https://jestjs.io/docs/jest-object#jestmockmodulename-factory-options
- Jika tidak ingin melakukan mock lagi, kita bisa gunakan jest.unmock()
- https://jestjs.io/docs/jest-object#jestunmockmodulename

```js
import { getAllProducts, getProductById } from "../src/database";
import { ProductService } from "../src/product-service";

jest.mock("../src/database");

test("mock modules getProductById", () => {
  getProductById.mockImplementation((id) => {
    return {
      id: id,
      name: "Product Mock",
    };
  });
  const product = ProductService.findById(1);

  expect(product).toEqual({
    id: 1,
    name: "Product Mock",
  });
});

test("mock modules getAllProducts", () => {
  const products = [
    {
      id: 1,
      name: "Product Mock",
    },
    {
      id: 2,
      name: "Product Mock",
    },
  ];
  getAllProducts.mockImplementation(() => {
    return products;
  });

  expect(ProductService.findAll()).toEqual(products);
});
```

**Selanjutnya :** [Mock Partial Modules](mockpartialmodules.md)