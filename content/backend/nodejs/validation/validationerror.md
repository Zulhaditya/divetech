---
title: Validation Error
tags:
  - validation
---

- Jika terjadi error karena data tidak valid, maka hasil result.error akan berisi ValidationError.
- https://joi.dev/api/?v=17.9.1#validationerror

```js
import Joi from "joi";

describe("Joi", () => {
  it("should return validation error", async () => {
    const usernameSchema = Joi.string().min(5).email().required();

    const result = usernameSchema.validate("ups");
    console.info(result);

    if (result.error) {
      result.error.details.forEach((detail) => {
        console.info(`${detail.path} = ${detail.message}`);
      });
    }
  });
});
```
