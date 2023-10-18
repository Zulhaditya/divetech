---
title: Function
tags:
  - typescript
---

# Function

- Sama seperti di JavaScript, TypeScript juga mendukung pembuatan function.
- Cara pembuatan function di TypeScript sama dengan di JavaScript.
- Salah satu yang membedakannya adalah, pada parameter kita perlu menentukan tipe data, dan pada function kita juga perlu menentukan tipe data return value-nya.
- Pada kasus function tersebut tidak mengembalikan value, kita bisa menggunakan tipe data void, atau tidak perlu menyebutkan sama sekali di JavaScript.

## Kode: Say Hello Function

```js
// function dengan return value string
function sayHello(name: string): string {
  return `Hello ${name}`;
}

expect(sayHello("Nay")).toBe("Hello Nay");

// function tanpa return
function printHello(name: string): void {
  console.info(`Hello ${name}`);
}

printHello("Aditya");
```

**Selanjutnya** : [Function Parameter](/backend/typescript/parameter.md)
