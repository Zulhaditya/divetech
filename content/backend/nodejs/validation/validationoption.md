---
title: Validation Option
tags:
  - validation
---

- Saat kita menggunakan validasi menggunakan validate() method, sebenarnya terdapat opsi tambahan yang bisa kita kirim untuk mengatur cara melakukan validasi.
- https://joi.dev/api/?v=17.9.1#anyvalidatevalue-options

```js
import Joi from "joi";

describe("Joi", () => {
  it("should return validation error", async () => {
    const usernameSchema = Joi.string().min(5).email().required();

    const result = usernameSchema.validate("ups@gmail.com", {
      abortEarly: false,
    });
    console.info(result);

    if (result.error) {
      result.error.details.forEach((detail) => {
        console.info(`${detail.path} = ${detail.message}`);
      });
    }
  });
});
```

**Selanjutnya :** [Object Validation](objectvalidation.md)
