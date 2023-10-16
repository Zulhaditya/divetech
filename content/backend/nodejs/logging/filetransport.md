---
title: File Transport
tags:
  - logging
---

- Sebelumnya, kita hanya menggunakan Console Transport, selain Console Transport, Winston memiliki file transport.
- Digunakan untuk menyimpan data log ke sebuah file.
- Kita bisa menambahkan langsung beberapa transport kedalam satu logger object.

```js
import winston from "winston";

test("create new logger with file transport", () => {
  const logger = winston.createLogger({
    transports: [
      new winston.transports.Console({}),
      new winston.transports.File({
        filename: "application.log",
      }),
    ],
  });

  logger.info("Hello World!");
  logger.info("Hello World!");
  logger.info("Hello World!");
});
```

**Selanjutnya :** [Transport Level](transportlevel.md)