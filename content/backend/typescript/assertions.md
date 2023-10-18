---
title: Assertions
tags:
  - typescript
---

# Type Assertions

- Kadang, kita sering berada di situasi dimana kita mengetahui tipe data yang digunakan, namun TypeScript tidak tahu tipe data tersebut.
- Biasanya pada kasus ini kita menggunakan kode dari JavaScript sehingga membuat return valuenya berupa tipe data any.
- Kita bisa melakukan konversi ke tipe data yang kita mau menggunakan kata kunci as.
- Ini disebut dengan type assertions.

## Kode: Type Assertions

```js
const person: any = {
  name: "Nay",
  age: 23
}

const person2: Person = person as Person
console.info(person2)
```

**Selanjutnya** : [Function](/backend/typescript/function.md)
