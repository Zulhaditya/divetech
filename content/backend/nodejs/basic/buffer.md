---
title: Buffer
tags:
  - standard-library
---

- Buffer merupakan object yang berisikan urutan byte dengan panjang tetap.
- Buffer merupakan turunan dari tipe data Uint8Array.
- Buffer juga digunakan untuk menyimpan data.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/buffer.html

```js
const buffer = Buffer.from("Zulhaditya Hapiz");
console.info(buffer);
console.info(buffer.toString());

buffer.reverse();
console.info(buffer.toString());
```

# Buffer Encoding

- Buffer juga bisa digunakan untuk melakukan encoding dari satu encoding ke encoding yang lainnya.
- Ada banyak encoding yang didukung oleh buffer, misalnya utf8, ascii, hex, base64, base64url dan lain-lain.

```js
const buffer = Buffer.from("Zulhaditya Hapiz", "utf-8");

console.info(buffer.toString());
console.info(buffer.toString("hex"));
console.info(buffer.toString("base64"));

const bufferBase64 = Buffer.from("WnVsaGFkaXR5YSBIYXBpeg==", "base64");

console.info(bufferBase64.toString("utf-8"));
```

**Selanjutnya :** [Stream](stream.md)
