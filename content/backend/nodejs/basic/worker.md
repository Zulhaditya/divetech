---
title: Worker
tags:
  - standard-library
---

- Worker thread adalah standard library yang digunakan untuk mengaktifkan thread ketika mengeksekusi Javascript secara paralel.
- Worker thread sangat cocok ketika kita membuat kode program yang butuh jalan secara paralel, dan biasanya ketika kode program kita membutuhkan proses yang CPU intensive, seperti enkripsi dan kompresi.
- Cara kerja worker thread mirip dengan web worker di Javscript web API.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/worker_threads.html

# Worker Main

```js
import { threadId, Worker } from "worker_threads";

const worker1 = new Worker("./worker.mjs");
const worker2 = new Worker("./worker.mjs");

worker1.addListener("message", (message) => {
  console.info(`Thread-${threadId} menerima data dari worker 1 : ${message}`);
});

worker2.addListener("message", (message) => {
  console.info(`Thread-${threadId} menerima data dari worker 2 : ${message}`);
});

worker1.postMessage(10);
worker2.postMessage(10);
```

# Worker

```js
import { threadId, parentPort } from "worker_threads";

parentPort.addListener("message", (message) => {
  for (let i = 0; i < message; i++) {
    console.info(`Thread-${threadId} mengirimkan pesan ${i}`);
    parentPort.postMessage(i);
  }
  
  parentPort.close();
});
```

**Selanjutnya :** [HTTP Client](httpclient.md)