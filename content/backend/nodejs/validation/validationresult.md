---
title: Validation Result
tags:
  - validation
---

- Saat kita melakukan validasi menggunakan method validate(), hasil dari method tersebut adalah object yang memiliki attribute value dan error.
- Hasil data akan ada di attribute value, contohnya kita akan melakukan validasi Date, namun inputnya berupa String, maka akan secara otomatis value Date yang akan dikonversi ke result.value
- Namun jika terjadi error, secara otomatis result.error berisi ValidationError.

```js
import Joi from "joi";

describe("Joi", () => {
  it("should can validate date", () => {
    const birthDateSchema = Joi.date().required().max("now").min("1-1-1988");

    const result = birthDateSchema.validate("1-1-1987");
    console.info(result);
    console.info(typeof result.value); // Date
    console.info(typeof result.error); // ValidationError

    const result2 = birthDateSchema.validate("12-19-1990");
    console.info(result2);

    const result3 = birthDateSchema.validate("12-19-2027");
    console.info(result3);
  });
});
```

**Selanjutnya :** [Validation Option](validationoption.md)
