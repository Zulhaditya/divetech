---
title: Todo Function
tags:
  - jest
---

- Gunakan Todo Function ketika kita berencana membuat unit test yang belum dilakukan.
- Todo Function akan ditampilkan sebagai summary ketika kita menjalankan unit test, untuk mengingatkan kita.
- https://jestjs.io/docs/api#testtodoname

```js
import { sumAll } from "../src/sum.js";

test.todo("Create test for sumAll() with big numbers");
test.todo("Create test for sumAll() with negative numbers");
```

**Selanjutnya :** [Failing Function](failingfunction.md)