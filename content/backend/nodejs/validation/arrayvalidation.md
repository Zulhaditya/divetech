---
title: Array Validation
tags:
  - validation
---

- Selain object, kita juga bisa melakukan validasi di data array.
- Baik itu array dengan isi data sederhana, atau array dengan isi data object.
- https://joi.dev/api/?v=17.9.1#array

# Array of Object

- Untuk melakukan validasi Array of Object, kita bisa kombinasikan schema array dan schema object.

```js
import Joi from "joi";

describe("Joi", () => {
  it("should can validate array", () => {
    const hobbiesSchema = Joi.array()
      .items(Joi.string().required().min(3).max(100))
      .min(1)
      .unique();

    const hobbies = ["Ask", "Reading", "Coding", "Learn"];
    const result = hobbiesSchema.validate(hobbies, {
      abortEarly: false,
    });
    console.info(result);
  });

  it.only("can validate array of object", () => {
    const addressesSchema = Joi.array()
      .min(1)
      .items(
        Joi.object({
          street: Joi.string().required().max(200),
          city: Joi.string().required().max(100),
          country: Joi.string().required().max(100),
          zipCode: Joi.string().required().max(100),
        })
      );
    const address = [
      {
        street: "Jalan belum ada",
      },
    ];
    const result = addressesSchema.validate(address, {
      abortEarly: false,
    });
    console.info(result);
  });
});
```

**Selanjutnya :** [Custom Validation Messages](customvalidationmessages.md)
