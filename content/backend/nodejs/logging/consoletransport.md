---
title: Console Transport
tags:
  - logging
---

- Saat kita membuat logger, secara default Logger tidak akan menggunakan Transport.
- Transport adalah destinasi atau target yang digunakan untuk mengirim log.
- Ada banyak sekali transport, salah satunya adalah console.
- Console merupakan transport yang digunakan untuk mengirim data log ke console/stdout.

```js
import winston from "winston";

test("create new logger with console transport", () => {
  const logger = winston.createLogger({
    transports: [new winston.transports.Console({})],
  });

  logger.log({
    level: "info",
    message: "Hello Logging",
  });
});
```

**Selanjutnya :** [Logging Level](logginglevel.md)