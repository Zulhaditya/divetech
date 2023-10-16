---
title: Database First Migration
tags:
  - database
---

- Database-first Migration adalah kebalikan dari Model-first Migration.
- Ini biasanya dilakukan ketika database nya sudah ada, dan kita ingin menggunakan Prisma untuk mengelola database nya.
- Untuk membuat model dari schema database yang sudah ada, kita bisa gunakan perintah:

```bash
npx prisma db pull
```

- Selanjutnya, kita bisa review perubahan di Schema-nya, dan ubah jika dibutuhkan.

# Example

- Kita akan hapus semua isi model di Prisma Schema.
- Lalu kita akan lakukan perintah untuk pull schema db.

**Selanjutnya :** [Prisma Studio](prismastudio.md)
