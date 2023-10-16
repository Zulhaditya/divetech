---
title: Create Transport
tags:
  - logging
---

- Kadang pada kasus tertentu, mungkin kita ingin membuat Transport sendiri, misalkan ketika ada log error, kita ingin mengirim data log tersebut ke database, atau ke chat atau ke email, dsb.
- Jika tidak ada transport yang tersedia secara default oleh Winston, kita bisa mencari transport yang opensource di komunitas, atau bisa saja membuat transport sendiri secara manual jika kita mau.
- Untuk membuat transport, kita cukup membuat class turunan dari package winston-transport.

# Transport Lainnya

- Winston juga menyediakan Transport lain, misalkan:
  - Redis Transport: https://github.com/winstonjs/winston-redis
  - Syslog Transport: https://github.com/winstonjs/winston-syslog
  - CouchDB Transport: https://github.com/winstonjs/winston-couchdb
  - Loggy Transport: https://github.com/winstonjs/winston-loggly
- Atau Transport yang disediakan di komunitas:
  - Slack Transport: https://github.com/TheAppleFreak/winston-slack-webhook-transport
  - Telegram Transport: https://github.com/ivanmarban/winston-telegram

**Selanjutnya :** [Exceptions](exceptions.md)
