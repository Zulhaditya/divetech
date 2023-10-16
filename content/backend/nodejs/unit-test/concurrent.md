---
title: Concurrent
tags:
  - jest
---

- Secara default, semua unit test akan dijalankan secara sequential, dan unit test selanjutnya akan dijalankan ketika unit test sebelumnya telah selesai.
- Jest juga mendukung concurrent unit test, dimana kita bisa menandai sebuah unit test agar jalan secara concurrent atau async sehingga tidak perlu ditunggu.
- Saat dibuatnya fitur ini, concurrent masih experimental atau belum stabil.
- https://jestjs.io/docs/api#testconcurrentname-fn-timeout

```js
import { sayHelloAsync } from "../src/async.js";

test.concurrent("concurrent 1", async () => {
  await expect(sayHelloAsync("Zulhaditya")).resolves.toBe("Hello Zulhaditya");
});

test.concurrent("concurrent 2", async () => {
  await expect(sayHelloAsync("Zulhaditya")).resolves.toBe("Hello Zulhaditya");
});

test.concurrent("concurrent 3", async () => {
  await expect(sayHelloAsync("Zulhaditya")).resolves.toBe("Hello Zulhaditya");
});
```

# Membatasi Concurrent

- Kita bisa membatasi berapa banyak concurrent test yang berjalan dengan cara menambahkan konfigurasi jest.
- https://jestjs.io/docs/configuration#maxconcurrency-number

**Selanjutnya :** [Todo Function](todofunction.md)