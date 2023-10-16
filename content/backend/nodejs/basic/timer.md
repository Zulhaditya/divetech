---
title: Timer
tags:
  - standard-library
---

- Timer merupakan standard library yang digunakan untuk melakukan scheduling.
- Function timer terdapat di globals, sehingga kita bisa menggunakannya tanpa melakukan import, namun semua function timer menggunakan callback.
- Jika ingin menggunakan timer versi promise, kita bisa mengimport dari module timers/promise
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/timers.html

# Timer versi callback

```js
setInterval(() => {
  console.info(`Start time at ${new Date()}`);
}, 1000);
```

# Timer versi promise

```js
import timers from "timers/promises";

const name = await timers.setTimeout(5000, "Zulhaditya");
console.info(new Date());
console.info(name);

for await (const startTime of timers.setInterval(1000, "ignored")) {
  console.info(`Start time at ${new Date()}`);
}
```

**Selanjutnya :** [Net](net.md)
