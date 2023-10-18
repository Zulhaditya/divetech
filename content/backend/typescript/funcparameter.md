---
title: Function as Parameter
tags:
  - typescript
---

# Function sebagai Parameter

- Sama seperti di JavaScript, TypeScript juga bisa menggunakan function sebagai parameter.
- Hal ini sering dilakukan, biasanya ketika memanggil function yang membutuhkan callback function lainnya.
- Pada TypeScript, paramater yang berupa function, perlu kita beri tau bahwa parameter tersebut adalah function.
- Kita bisa gunakan Function Interface, atau bisa langsung sebutkan pada parameternya, jumlah parameter dan return value function yang dibutuhkan.

## Kode: Function sebagai Parameter

```js
function sayHello(name: string, filter: (name: string) => string): string {
  return `Hello ${filter(name)}`;
}

function toUpper(name: string): string {
  return name.toUpperCase();
}

expect(sayHello("Nay", toUpper)).toBe("Hello NAY");

// anonymous function
expect(
  sayHello("Aditya", function (name: string): string {
    return name.toUpperCase();
  })
).toBe("Hello ADITYA");

// arrow function
expect(sayHello("Hapiz", (name: string): string => name.toUpperCase())).toBe(
  "Hello HAPIZ"
);
```

**Selanjutnya** : [If Statement](/backend/typescript/if.md)
