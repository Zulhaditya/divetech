---
title: Logging Level
tags:
  - logging
---

- Dalam logging, terdapat istilah Level, Level biasanya digunakan sebagai informasi seberapa penting log tersebut.
- Level dimulai dari paling rendah ke paling tinggi, semakin tinggi Level-nya, semakin penting informasi log tersebut.
- Untuk menambahkan level ketika melakukan log, kita bisa ubah attribute level menjadi level yang kita inginkan.

# Winston Level

- error
- warn
- info
- http
- verbose
- debug
- silly

```js
import winston from "winston";

test("create logger with logging level", () => {
  const logger = winston.createLogger({
    transports: [new winston.transports.Console({})],
  });

  logger.log({
    level: "error",
    message: "Hello Error",
  });

  logger.log({
    level: "warn",
    message: "Hello Warn",
  });

  logger.log({
    level: "info",
    message: "Hello Info",
  });

  logger.log({
    level: "http",
    message: "Hello http",
  });

  logger.log({
    level: "verbose",
    message: "Hello Verbose",
  });

  logger.log({
    level: "debug",
    message: "Hello Debug",
  });

  logger.log({
    level: "silly",
    message: "Hello Silly",
  });
});
```

## Kenapa beberapa level tidak muncul?

- Secara default, saat membuat logger, logger hanya menampilkan log dengan level info atau level diatasnya.
- Jika kita ingin mengubah log level mana yang ingin kita tampilkan, kita perlu mengubah konfigurasi level ketika membuat logger, dengan menggunakan level minimal yang ingin kita tampilkan.
- Kirimkan parameter level untuk menampilkan level logging tertentu.

```js
import winston from "winston";

test("create logger with logging level", () => {
  const logger = winston.createLogger({
    level: "debug",
    transports: [new winston.transports.Console({})],
  });

  logger.log({
    level: "error",
    message: "Hello Error",
  });

  logger.log({
    level: "warn",
    message: "Hello Warn",
  });

  logger.log({
    level: "info",
    message: "Hello Info",
  });

  logger.log({
    level: "http",
    message: "Hello http",
  });

  logger.log({
    level: "verbose",
    message: "Hello Verbose",
  });

  logger.log({
    level: "debug",
    message: "Hello Debug",
  });

  logger.log({
    level: "silly",
    message: "Hello Silly",
  });
});
```

# Shortcut Function

- Logger juga memiliki function shortcut yang bisa digunakan untuk melakukan logging, sehingga kita tidak perlu menggunakan function log dan object dengan attribute level lagi.
- Kita bisa menggunakan function dengan nama sesuai dengan levelnya, misal logger.info(message), logger.warn(messsage) dan lain-lain.

```js
test("logging with shortcut function", () => {
  const logger = winston.createLogger({
    level: "debug",
    transports: [new winston.transports.Console({})],
  });

  logger.error("Hello Error");

  logger.warn("Hello Warn");

  logger.info("Hello Info");

  logger.http("Hello HTTP");

  logger.verbose("Hello Verbose");

  logger.debug("Hello Debug");

  logger.silly("Hello Silly");
});
```

**Selanjutnya :** [Format](format.md)