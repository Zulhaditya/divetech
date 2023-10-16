---
title: Exceptions
tags:
  - logging
---

- Saat membuat program Node.js, kadang kita lupa menangkap exception.
- Hal ini berbahaya karena nanti kita tidak bisa melakukan debug exception dengan baik, sehingga kita tidak bisa investigasi selanjutnya.

# Handle Exception

- Winston memiliki fitur secara otomatis yang bisa digunakan untuk menangkap Exeception yang belum terhandle.
- Kita bisa melakukan pengaturan ini di Logger, yang secara otomatis exception akan dikirim ke semua transport.
- Atau kita bisa melakukan pengaturan ini di transport.

```js
import winston from "winston";

const logger = winston.createLogger({
  level: "info",
  transports: [
    new winston.transports.Console({}),
    new winston.transports.File({
      handleExceptions: true,
      filename: "exception.log",
    }),
  ],
});

hello();
```

**Selanjutnya :** [Rejections](rejections.md)
