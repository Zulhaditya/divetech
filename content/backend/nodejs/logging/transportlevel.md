---
title: Transport Level
tags:
  - logging
---

- Beberapa transport memiliki pengaturan level sendiri.
- Saat sebuah transport memiliki pengaturan level, secara otomatis transport hanya akan menerima log dengan level tersebut atau yang lebih tinggi.
- Hal ini sangat cocok digunakan untuk memisahkan beberapa level log di transport yang berbeda.

```js
import winston from "winston";

test("create new logger with console and file transport", () => {
  const logger = winston.createLogger({
    level: "info",
    transports: [
      new winston.transports.Console({}),
      new winston.transports.File({
        filename: "application.log",
      }),
      new winston.transports.File({
        level: "error",
        filename: "application-error.log",
      }),
    ],
  });

  logger.info("Hello World!");
  logger.info("Hello World!");
  logger.info("Hello World!");
  logger.error("Hello Error");
  logger.error("Hello Error");
  logger.error("Hello Error");
});
```

**Selanjutnya :** [Rotate File](rotatefile.md)