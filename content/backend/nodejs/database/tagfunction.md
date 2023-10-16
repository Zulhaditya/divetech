---
title: Tag Function
tags:
  - database
---

- Tag function sebenarnya jarang digunakan, tapi di Prisma digunakan untuk mempermudah kita mengirim perintah SQL ke database menggunakan Prisma Client.
- Tag function adalah fitur seperti String Template yang bisa dilakukan ketika kita memanggil function.

```js
function tagFunction(array, ...args) {
  console.info(array);
  console.info(args);
}

test("tag function", () => {
  const name = "Nay";
  const lastName = "Wulandari";

  tagFunction`Hello ${name}! ${lastName}, how are you?`;
  tagFunction`Bye ${name}! ${lastName}, see u later`;
});
```

# Tag Function Parameter

- Sederhananya, Tag Function mengubah data string template menjadi parameter yang dipecah dalam dua array.
- Array pertama menjadi data string-nya, dan Array kedua menjadi data parameternya.
- Misalkan untuk data `Hello ${name}!, how are u?`, misalkan $name adalah Nay, akan diubah menjadi:
- Array 1: ["Hello", "!, how are u?"]
- Array 2: ["Nay"]
- Penerapan Tag function bertujuan agar query yang kita buat nanti aman dari serangan SQL Injection, karena Prisma akan melakukan konversi dari variable yang kita kirimkan menggunakan tag function.

```js
test("tag function sql", () => {
  const name = "Nay";
  const age = "22";

  tagFunction`SELECT * FROM users WHERE name = ${name} AND age = ${age}`;
});
```

**Selanjutnya :** [Execute SQL](executesql.md)
