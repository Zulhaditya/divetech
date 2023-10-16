---
title: Mock Partial Modules
tags:
  - jest
---

- Saat kita melakukan mock modules, maka secara default seluruh modules tersebut akan di mock oleh Jest.
- Kadang, kita tidak ingin melakukan mock semua dibagian modules, mungkin hanya beberapa bagian saja.
- Jest juga memiliki fitur yang bisa digunakan untuk menggantikan module aslinya menggunakan jest.requireActual(module)
- https://jestjs.io/docs/jest-object#jestrequireactualmodulename

```js
import { getAllProducts, getProductById } from "../src/database";
import { ProductService } from "../src/product-service";

jest.mock("../src/database", () => {
  const originalModule = jest.requireActual("../src/database");

  return {
    __esModule: true,
    ...originalModule,
    getAllProducts: jest.fn(),
  };
});

test.failing("mock modules getProductById", () => {
  ProductService.findById(1);
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

**Selanjutnya :** [Mock Class](mockclass.md)