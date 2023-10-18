---
title: Intersection
tags:
  - typescript
---

# Intersection Types

- Intersection merupakan cara membuat tipe data baru dengan cara menggabungkan dua tipe data lainnya.
- Hal ini sangat cocok ketika kita tidak bisa melakukan extends pada interface.
- Kita bisa membuat type dengan menggunakan kata kunci &/dan.

## Kode: Intersection Types

```js
export interface HasName {
  name: string;
}

export interface HasId {
  id: string;
}

export type Domain = HasId & HasName;
```

**Selanjutnya** : [Assertions](/backend/typescript/assertions.md)
