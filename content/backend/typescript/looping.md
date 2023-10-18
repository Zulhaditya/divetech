---
title: Looping
tags:
  - typescript
---

# For Loop

- Perulangan for di TypeScript sama saja seperti perulangan for di JavaScript.
- TypeScript mendukung semua for loop seperti for loop biasa, for in, dan for of.

```js
const names: string = ["Nay", "Adit", "Hapiz"];

// for i
for (let i = 0; i < names.length; i++) {
  console.info(names[i]);
}

// for of
for (const name of names) {
  console.info(name);
}

// for in
for (const index in names) {
  console.info(names[index]);
}
```

# While / Do While Loop

- TypeScript juga mendukung perulangan while / do while loop sama seperti di JavaScript.

```js
// while loop
let counter = 0;
while (counter < 10) {
  console.info(counter);
  counter++;
}

// do while loop
let counter = 0;
do {
  console.info(counter);
  counter++;
} while (counter < 10);
```

# Break dan Continue

- Sama seperti di JavaScript pada perulangan while dan do while, kita sering menggunakan kata kunci break dan continue.

```js
let counter: number = 0;
do {
  counter++;

  if (counter == 10) {
    break;
  }

  if (counter % 2 == 0) {
    continue;
  }

  console.info(counter);
} while (true);
```

**Selanjutnya** : [Title](/backend/typescript/example.md)
