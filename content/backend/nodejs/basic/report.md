---
title: Report
tags:
  - standard-library
---

- Report merupakan standard library yang digunakan untuk membuat laporan secara otomatis dalam file ketika sesuatu terjadi pada aplikasi Node.js kita.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/report.html

```js
import process from "process";

process.report.reportOnFatalError = true;
process.report.reportOnSignal = true;
process.report.reportOnUncaughtException = true;
process.report.filename = "report.json";

function sampleError() {
  throw new Error("Ups!");
}

sampleError();
```

**Selanjutnya :** [Buffer](buffer.md)