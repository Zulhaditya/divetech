---
title: Rotate File
tags:
  - logging
---

- Secara default, winston transport file hanya akan menyimpan semua log didalam satu file.
- Hal ini akan sangat berbahaya ketika aplikasi berjalan dalam jangka waktu yang lama, sehingga menyebabkan ukuran file akan semakin besar.

# Daily Rotate File

- Winston sendiri membuat package terpisah untuk membantu menyelesaikan permasalahan ini, yaitu Daily Rotate File.
- https://www.npmjs.com/package/winston-daily-rotate-file
- Package ini digunakan untuk membuat rotasi file transport secara otomatis sesuai dengan aturan yang bisa kita tentukan sendiri, dan bisa secara otomatis menghapus file lama ketika sudah tidak diperlukan lagi.

```js
import winston from "winston";
import DailyRotateFile from "winston-daily-rotate-file";

test("logging with dailty rotate file", () => {
  const logger = winston.createLogger({
    level: "info",
    transports: [
      new winston.transports.Console({}),
      new DailyRotateFile({
        filename: "app-%DATE%.log",
        zippedArchive: true,
        maxSize: "1mb",
        maxFiles: "14d",
      }),
    ],
  });

  for (let i = 0; i < 100000; i++) {
    logger.info(`Hello World ${i}`);
  }
});
```

**Selanjutnya :** [Create Transport](createtransport.md)
