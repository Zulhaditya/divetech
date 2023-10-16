---
title: Validation
tags:
  - validation
---

- Joi mendukung validasi untuk banyak tipe data Javascript, seperti String, Number, Boolean, dan lain-lain.
- Untuk menggunakan Joi, kita cukup import Joi dari package Joi.
- Selanjutnya, kita bisa menggunakan method-method sesuai dengan tipe datanya.

# Schema

- Hal pertama yang dilakukan untuk melakukan validasi adalah membuat Schema.
- Schema adalah aturan-aturan yang sudah kita tentukan.
- Setelah membuat schema, baru selanjutnya kita bisa melakukan validasi data menggunakan schema tersebut.

# Validasi Tipe Data

- String: https://joi.dev/api/?v=17.9.1#string
- Number: https://joi.dev/api/?v=17.9.1#number
- Boolean: https://joi.dev/api/?v=17.9.1#boolean

```js
import Joi from "joi";

describe("Joi", () => {
  it("should can create schema", () => {
    const schema = Joi.string().min(3).max(100).required();
    const result = schema.validate("nay");
    if (result.error) {
      console.info(result.error);
    }
  });

  it.only("should can validate basic data type", () => {
    const usernameSchema = Joi.string().email().required();
    const isAdminSchema = Joi.boolean().required();
    const priceSchema = Joi.number().required().min(1000).max(1000000);

    const resultUsername = usernameSchema.validate("nay@gmail.com");
    console.info(resultUsername);

    const resultIsAdmin = isAdminSchema.validate("false");
    console.info(resultIsAdmin);

    const resultPrice = priceSchema.validate("100000");
    console.info(resultPrice);
  });
});
```

**Selanjutnya :** [Date Validation](datevalidation.md)
