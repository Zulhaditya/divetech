---
title: Stream
tags:
  - standard-library
---

- Stream adalah standard library yang digunakan untuk kontrak aliran data di Node.js
- Ada banya sekali stream object di Node.js
- Stream bisa jadi object yang bisa dibaca, atau bisa ditulis, dan stream adalah turunan dari EventEmitter.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/stream.html

```js
import fs from "fs";

const writer = fs.createWriteStream("target.log");
writer.write("Inayah ");
writer.write("Fitri ");
writer.write("Wulandari");
writer.end();

const reader = fs.createReadStream("target.log");

reader.addListener("data", (data) => {
  console.info(data.toString());
});
```

**Selanjutnya :** [Timer](timer.md)
