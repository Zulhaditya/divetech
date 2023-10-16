---
title: Custom Validation
tags:
  - validation
---

- Saat kita membutuhkan validasi yang tidak disediakan di Joi, kita juga bisa membuat custom validation di Joi.
- Terdapat method custom() di semua schema yang bisa kita gunakan untuk menambah validasi baru.
- https://joi.dev/api/?v=17.9.1#anycustommethod-description

```js
import Joi from "joi";

describe("Joi", () => {
  it("should can create custom validation", () => {
    const registerSchema = Joi.object({
      username: Joi.string().required().min(3).max(100).email(),
      password: Joi.string()
        .required()
        .min(6)
        .max(100)
        .custom((value, helpers) => {
          if (value.startsWith("nay")) {
            return helpers.error("password.wrong");
          }
          return value;
        })
        .messages({
          "password.wrong": 'password cannot start with "nay"',
        }),
      confirmPassword: Joi.string().required().min(6).max(100),
    })
      .custom((value, helpers) => {
        if (value.password !== value.confirmPassword) {
          return helpers.error("register.password.different");
        }
        return value;
      })
      .messages({
        "register.password.different":
          "password and confirmPassword is different",
      });

    const request = {
      username: "nay@gmail.com",
      password: "yan12345",
      confirmPassword: "salah12345",
    };

    const result = registerSchema.validate(request, {
      abortEarly: false,
    });

    console.info(result);
  });
});
```
