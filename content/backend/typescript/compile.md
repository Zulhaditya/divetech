---
title: Compile
tags:
  - typescript
---

# TypeScript Compile

- Kode TypeScript tidak bisa langsung dijalankan, kita harus melakukan kompilasi terlebih dahulu menjadi kode JavaScript.
- Kita bisa gunakan perintah:

```bash
npx tsc
```

- Secara default, semua file hasil kompilasi akan disimpan di lokasi yang sama dengan file TypeScript.
- Kita bisa memisahkan hasil kompilasi ke sebuah folder **dist** (distribution).
- Untuk mengubah lokasi file hasil kompilasi, kita perlu mengubah settingnya di **tsconfig.json**.
- Pada **tsconfig.json**, cari "outdir" dan ubah valuenya sesuai dengan folder yang diinginkan:

```json
{
  "outDir": "dist/"
}
```

# Include dan Exclude

- Secara default, semua file **.ts** akan dikompilasi oleh TypeScript, terkadang kita tidak membutuhkan hal tersebut.
- Misalnya, kita hanya ingin melakukan kompilasi untuk kode program, dan tidak butuh kompilasi untuk kode unit test.
- Kita bisa menambahkan include dan exclude pada **tsconfig.json**.
- Berikut adalah contoh kode include dan exclude:

```json
{
  "include": ["src/**/*", "tests/**/*"],
  "exclude": ["src/**/*.test.ts", "tests/**/*.test.ts"]
}
```

- Untuk kebutuhan belajar ubah file **tsconfig.json** menjadi seperti ini:

```json
{
  "include": ["src/**/*", "tests/**/*"]
}
```

**Selanjutnya** : [Tipe Data Primitif](/backend/typescript/dataprimitif.md)
