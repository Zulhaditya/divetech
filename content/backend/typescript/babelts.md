---
title: Babel TypeScript
tags:
  - typescript
---

# Babel TypeScript

- Untuk menjalankan unit test, kita menggunakan **Jest** dan **Babel**.
- Banyak programmer yang mengeluh karena ketika proses development, TypeScript harus dicompile terlebih dahulu.
- Oleh karena itu, **@babel/typescript** melakukan cara kompilasi dengan cara menghapus seluruh kode TypeScript dan menjadikan kode JavaScript.
- Error pada TypeScript yang harusnya terjadi di unit test kadang tidak terjadi karena kode TypeScript dihapus oleh **Babel**.
- Kita harus memastikan melakukan pengecekan menggunakan perintah:

```bash
npx tsc
```

- Untuk memastikan kode TypeScript tidak bermasalah.

# TypeScript Compiler

Untuk menjalankan TypeScript Compiler secara terus menerus, kita bisa meggunakan perintah:

```bash
npx tsc --watch
```

**Selanjutnya** : [Array](/backend/typescript/array.md)
