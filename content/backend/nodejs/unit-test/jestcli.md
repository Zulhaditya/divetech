---
title: Jest CLI
tags:
  - jest
---

- Jest memiliki banyak perintah tambahan, tidak hanya mengetikkan perintah jest saja.
- Untuk melihat detail perintah apa saja yang bisa digunakan, gunakan perintah:

```bash
npx jest --help
```

- Menjalankan unit test berdasarkan file atau path tertentu dapat gunakan perintah dibawah ini:

```bash
npx jest --runTestsByPath test/sum.test.js
```

- Menjalankan unit test berdasarkan nama function test dapat gunakan perintah:

```bash
npx jest --testNamePattern "test sum function 1"
```

- Menjalankan unit test berdasarkan file tertentu juga dapat dijalankan dengan perintah ini:

```bash
npx jest test/sum.test.js
```

**Selanjutnya :** [Matchers](matchers.md)