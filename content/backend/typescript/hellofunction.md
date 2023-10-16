---
title: Hello Function
tags:
  - typescript
---

Sebelum mempelajari TypeScript lebih lanjut, kita akan coba buat **hello function** menggunakan TypeScript.

- Buatlah sebuah folder **src** dan isi dengan file **say-hello.ts**, ini adalah kodenya:

```js
export function sayHello(name: String): String {
  return `Hello ${name}`;
}
```

- Buat file unit test menggunakan TypeScript, nama filenya **say-hello.test.ts**. Letakkan di folder **tests**. Ini adalah kodenya:

```js
import { sayHello } from "../src/say-hello";

describe("sayHello", function (): void {
  it("should return hello world", function (): void {
    expect(sayHello("world")).toBe("Hello world");
  });
});
```

- Untuk mengetahui apakah kode kita sudah benar dan unit test berhasil, gunakan perintah:

```bash
npm test

# atau
npx jest
```

**Selanjutnya** : [Compile](/backend/typescript/compile.md)
