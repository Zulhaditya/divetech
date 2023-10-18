---
title: Indexable Interface
tags:
  - typescript
---

# Indexable Interface

- Interface juga bisa digunakan untuk membuat tipe data dengan jenis yang memiki index, seperti array atau object.

## Kode: Array

```js
interface StringArray {
  [index: number]: string;
}

const names: StringArray = ["Zulhaditya", "Hapiz"];
console.info(names[0]);
console.info(names[1]);
```

## Kode: Object

```js
interface StringDictionary {
  [key: string]: string;
}

const dictionary: StringDictionary = {
  name: "Zulhaditya",
  address: "Kepulauan Riau",
};

console.info(dictionary["name"]);
console.info(dictionary["address"]);
```

**Selanjutnya** : [Extending](/backend/typescript/extending.md)
