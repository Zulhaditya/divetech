---
title: Rejections
tags:
  - logging
---

- Selain kasus Exception yang tidak ter-handle, kadang sering ada kasus di Node.js kita lupa untuk menghandle Promise Rejection.
- Winston memiliki fitur yang bisa digunakan untuk menangkap semua promise yang reject secara otomatis.
- Jadi kita bisa melihat detail Error Rejection tersebut.
- Sama seperti Exceptions, kita bisa atur ini di Logger atau di Transport.

```js
import winston from "winston";

async function callAsync() {
  return Promise.reject("Ups");
}

const logger = winston.createLogger({
  level: "info",
  transports: [
    new winston.transports.Console({}),
    new winston.transports.File({
      handleExceptions: true,
      handleRejections: true,
      filename: "exception.log",
    }),
  ],
});

callAsync();
```
