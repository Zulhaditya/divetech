---
title: Undefined/Null
tags:
  - typescript
---

# Null dan Undefined

- Saat kita menggunakan ? pada variable atau parameter, secara otomatis kita bisa mengirim data undefined.
- Tapi terkadang, ada kasus ketika kita ingin mengirim data null, pada kasus ini kita menggunakan tipe data null.

## Kode: Undefined

```js
function sayHello(name?: string) {
  if (name) {
    console.log(`Hello ${name}`);
  } else {
    console.info("Hello");
  }
}

sayHello("Nay");
const name: string | undefined = undefined;
sayHello(name);
```

## Kode: Null

```js
function sayHello(name?: string | null) {
  if (name) {
    console.log(`Hello ${name}`);
  } else {
    console.info("Hello");
  }
}

sayHello("Nay");
const name: string | undefined = undefined;
sayHello(null);
```

**Selanjutnya** : [Interface](/backend/typescript/interface.md)
