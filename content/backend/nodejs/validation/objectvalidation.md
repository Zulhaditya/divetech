---
title: Object Validation
tags:
  - validation
---

- Saat kita membuat aplikasi, kita sering sekali membuat Javascript Object.
- Untungnya Joi, juga bisa digunakan untuk melakukan validasi JS Object, sehingga mempermudah kita untuk melakukan validasi sekaligus ke semua field di JS Object.
- https://joi.dev/api/?v=17.9.1#object

# Nested Object

- Joi juga bisa digunakan untuk memvalidasi nested object.
- Saat kita ingin memvalidasi nested object, kita harus tentukan object schema-nya juga.

```js
import Joi from "joi";

describe("Joi", () => {
  it("should can validate object", () => {
    const loginSchema = Joi.object({
      username: Joi.string().required().min(3).max(100).email(),
      password: Joi.string().required().min(6).max(100),
    });

    const request = {
      username: "nay@gmail.com",
      password: "rahasia",
    };

    const result = loginSchema.validate(request, {
      abortEarly: false,
    });

    console.info(result);
  });

  it("should can validate nested object", () => {
    const createSchema = Joi.object({
      id: Joi.string().required().max(100),
      name: Joi.string().required().max(100),
      address: Joi.object({
        street: Joi.string().required().max(200),
        city: Joi.string().required().max(100),
        country: Joi.string().required().max(100),
        zipCode: Joi.string().required().max(100),
      }).required(),
    });

    const request = {
      address: {},
    };

    const result = createSchema.validate(request, {
      abortEarly: false,
    });

    console.info(result);

    if (result.error) {
      result.error.details.forEach((value) => {
        console.info(`${value.path} : ${value.message}`);
      });
    }
  });
});
```

**Selanjutnya :** [Array Validation](arrayvalidation.md)
