---
title: Function Parameter
tags:
  - typescript
---

# Function Parameter

- Sama seperti di JavaScript, function di TypeScript bisa memiliki banyak parameter, rest parameter (variable argument) sampai default value.
- Fitur yang berbeda dengan JavaScript adalah di TypeScript setiap parameter wajib diisi, kecuali kita tentukan sebagai optional menggunakan ? (tanda tanya).

## Kode: Default Value

```js
function sayHello(name: string = "Guest"): string {
  return `Hello ${name}`;
}

expect(sayHello("Nay")).toBe("Hello Nay");
expect(sayHello()).toBe("Hello Guest");
```

## Kode: Rest Parameter

```js
function sum(...values: number[]): number {
      let total = 0
      for (const value of values) {
        total += value
      }
      return total
    }

    expect(sum(1, 2, 3, 4, 5)).toBe(15
```

## Kode: Optional Parameter

```js
function sayHello(firstName: string, lastName?: string): string {
  if (lastName) {
    return `Hello ${firstName} ${lastName}`;
  } else {
    return `Hello ${firstName}`;
  }
}

expect(sayHello("Nay")).toBe("Hello Nay");
expect(sayHello("Aditya", "Hapiz")).toBe("Hello Aditya Hapiz");
```

**Selanjutnya** : [Overloading](/backend/typescript/overloading.md)
