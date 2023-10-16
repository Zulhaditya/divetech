---
title: Path
tags:
  - standard-library
---

- Path merupakan standard library yang digunakan untuk bekerja dengan lokasi file dan directory / folder.
- Resources: https://nodejs.org/dist/latest-v16.x/docs/api/path.html

```js
import path from "path";

const file = "/Users/zulhaditya/file.txt";

// mendapatkan directory file
console.info(path.dirname(file));

// mendapatkan nama file
console.info(path.basename(file));

// mendapatkan ekstension file
console.info(path.extname(file));
```

**Selanjutnya :** [File System](fs.md)
