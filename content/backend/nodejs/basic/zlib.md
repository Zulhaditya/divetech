---
title: Zlib
tags:
  - standard-library
---

- Zlib adalah standard library yang digunakan untuk melakukan kompresi menggunakan Gzip.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/zlib.html

# Compress File

```js
import fs from "fs";
import zlib from "zlib";

const source = fs.readFileSync("zlib-compress.mjs");
const result = zlib.gzipSync(source);

fs.writeFileSync("zlib-compress.txt", result);
```

# Decompress File

```js
import fs from "fs";
import zlib from "zlib";

const source = fs.readFileSync("zlib-compress.txt");
console.info(source.toString());

const result = zlib.unzipSync(source);
console.info(result.toString());
```

**Selanjutnya :** [Console](console.md)
