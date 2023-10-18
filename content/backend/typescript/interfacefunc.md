---
title: Interface Function
tags:
  - typescript
---

# Function di Interface

- Implementasi dari interface di JavaScript sebenarnya adalah sebuah object.
- Pada JavaScript, kita bisa menambahkan function sebagai attribute di object.
- Kita juga bisa melakukan hal ini di interface.

## Kode: Interface Person

```js
interface Person {
  name: string
  sayHello(name: string): string
}
```

**Selanjutnya** : [Intersection](/backend/typescript/intersection.md)
