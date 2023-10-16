---
title: Combine Format
tags:
  - logging
---

- Winston memiliki fitur bernama Combine Format, dimana kita bisa melakukan kombinasi beberapa format sekaligus.
- Ini cocok untuk menambahkan informasi tambahan ke log data, misal data timestamp, data jarak waktu antar log, dan lain-lain.
- Kita bisa menggunakan Combine Format di Winston untuk menggabungkan beberapa format.

```js
import winston from "winston";

test("logging with combine format", () => {
  const logger = winston.createLogger({
    level: "info",
    format: winston.format.combine(
      winston.format.timestamp(),
      winston.format.ms(),
      winston.format.json()
    ),
    transports: [new winston.transports.Console({})],
  });

  logger.info("Hello Format");
  logger.warn("Hello Warn");
  logger.error("Hello Error");
});
```

**Selanjutnya :** [File Transport](filetransport.md)
