---
title: DNS
tags:
  - standard-library
---

- DNS merupakan standard library yang digunakan untuk bekerja dengan DNS (Domain Name Server).
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/dns.html

```js
import dns from "dns/promises";

const address = await dns.lookup("www.example.com");

console.info(address.address);
console.info(address.family);
```

**Selanjutnya :** [Events](events.md)