---
title: Custom Validation Messages
tags:
  - validation
---

- Saat menggunakan validation Joi, terdapat fitur default error messages yang direpresentasikan menggunakan message key.
- https://joi.dev/api/?v=17.9.1#list-of-errors
- Jika kita mau, kita bisa mengubah value dari message key, ketika membuat schema, sehingga secara otomatis.
- Untuk mengubah message nya, kita bisa menggunakan method messages() pada schema.
- https://joi.dev/api/?v=17.9.1#anymessagesmessages

```js
import Joi from "joi";

describe("Joi", () => {
  it("should can use custom messages", () => {
    const schema = Joi.string().min(3).max(10).required().messages({
      "string.min": "{{#label}} panjang harus minimal {{#limit}} karakter",
      "string.max": "{{#label}} panjang harus maximal {{#limit}} karakter",
    });

    const request = "aaa";
    const result = schema.validate(request);
    console.info(result);
  });

  it.only("should can use custom messages in object validation", () => {
    const schema = Joi.object({
      username: Joi.string().required().email().messages({
        "any.required": "{{#label}} harus diisi",
        "string.email": "{{#label}} harus valid email",
      }),
      password: Joi.string().required().min(6).max(10).messages({
        "any.required": "{{#label}} harus diisi",
        "string.min": "{{#label}} harus lebih dari {{#limit}} karakter",
        "string.max": "{{#label}} harus kurang dari {{#limit}} karakter",
      }),
    });

    const request = {
      username: "nay@gmail.com",
      password: "123456",
    };

    const result = schema.validate(request, {
      abortEarly: false,
    });
    console.info(result);
  });
});
```

**Selanjutnya :** [Custom Validation Messages](customvalidation.md)
