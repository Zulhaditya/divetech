---
title: Array
tags:
  - typescript
---

# Tipe Data Array

- Tipe data array di TypeScript juga sama seperti JavaScript, cara pembuatannya dan penggunaannya.
- Di TypeScript, tipe data array bisa menggunakan tanda:

```js
tipeData[] atau Array<TipeData>

// contoh:
describe('Array', function() {
  it('should same with javascript', function() {

    const names: string[] = ["Zulhaditya", "Hapiz", "Inayah", "Wulandari"]
    const values: number[] = [1, 2, 3]

    console.info(names)
    console.info(values)
  })
})
```

# Read Only Array

Di TypeScript, kita bisa membuat array dengan tipe **readonly** (tidak bisa diubah lagi) menggunakan tipe data:

```js
ReadonlyArray<TipeData>

// contoh:
const hobbies: ReadonlyArray<string> = ["Membaca", "Menulis"]
console.info(hobbies)
```

# Tuple

- Tuple adalah tipe data array, yang panjang array dan juga tipe data di tiap index sudah ditentukan.
- Pada kasus tuple bersifat **readonly**, kita bisa menambahkan kata kunci **readonly** juga.

```js
const person: readonly [string, string, number] = ["Nay", "Aditya", 10]

console.info(person[0])
console.info(person[1])
console.info(person[2])
```

**Selanjutnya** : [Any](/backend/typescript/any.md)
