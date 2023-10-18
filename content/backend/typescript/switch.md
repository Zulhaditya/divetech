---
title: Switch Statement
tags:
  - typescript
---

# Switch Statement

- Switch statement di TypeScript juga sama seperti di JavaScript.

## Kode: Switch Statement

```js
function sayHello(name: string): string {
  switch (name) {
    case "Nay":
      return "Hi Nay";
    case "Adit":
      return "Hi Adit";
    default:
      return "Hello";
  }
}

console.info(sayHello("Nay"));
console.info(sayHello("Adit"));
console.info(sayHello("Hapiz"));
```

**Selanjutnya** : [Looping](/backend/typescript/looping.md)
