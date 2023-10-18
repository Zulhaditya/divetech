---
title: Interface
tags:
  - typescript
---

# Interface

- Interface adalah cara lain untuk melakukan deklarasi data selain menggunakan type.
- Interface bisa dikembangkan dengan mudah dibandingkan type.
- Oleh karena itu, kebanyakan tipe data yang kompleks, kebanyakan programmer typescript akan menggunakan interface dibandingkan menggunakan type.

## Kode: Interface

```js
export interface Seller {
  id: number;
  name: string;
  address?: string;
}
```

# Readonly Properties

- Properties dapat kita jadikan readonly, yang artinya tidak bisa diubah lagi.
- Kita bisa mengubah kata kunci readonly pada attribute tersebut.

## Kode: Readonly Properties

```js
export interface Seller {
  id: number;
  name: string;
  address?: string;
  readonly nib: string;
  readonly npwp: string;
}
```

**Selanjutnya** : [Function Interface](/backend/typescript/funcinterface.md)
