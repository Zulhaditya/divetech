---
title: Format
tags:
  - logging
---

- Format adalah object yang digunakan untuk melakukan formatting data log sebelum dikirim ke Transport.
- Saat kita membuat logger, logger akan menggunakan JSON format, artinya data akan dikirim dalam bentuk JSON.
- Winston juga menyediakan banyak format selain JSON.

```js
import winston from "winston";

test("create new logger with console transport", () => {
  const logger = winston.createLogger({
    level: "info",
    // format: winston.format.json(),
    format: winston.format.logstash(),
    transports: [new winston.transports.Console({})],
  });

  logger.info("Hello Format");
});
```

# Membuat Format Sendiri

- Winston juga menyediakan format printf, yang bisa digunakan untuk membuat format sendiri.

```js
import winston from "winston";

test("logging with printf format", () => {
  const logger = winston.createLogger({
    level: "info",
    format: winston.format.printf((log) => {
      return `${new Date()} | ${log.level.toUpperCase()}: ${log.message}`;
    }),
    transports: [new winston.transports.Console({})],
  });

  logger.info("Hello Format");
  logger.warn("Hello Warn");
});
```

**Selanjutnya :** [Combine Format](combineformat.md)
