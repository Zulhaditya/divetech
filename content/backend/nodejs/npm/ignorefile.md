---
title: Ignore File
tags:
  - npm
---

- Saat kita publish package ke web NPM, secara default, semua file yang terdapat di project akan di publish ke web NPM.
- Ketika ingin meng-ignore beberapa file agar tidak ikut terpublish ke web NPM, kita dapat membuat file .npmignore
- Format penulisan .npmignore sama dengan format penulisan .gitignore

# Git Ignore

- NPM secara default akan membaca file .npmignore untuk melakukan ignore file.
- Namun, jika file .npmignore tidak ada, maka NPM akan mencoba baca file .gitignore
- Oleh karena itu, jika sudah memiliki .gitignore, kita bisa saja tidak perlu membuat .npmignore lagi, kecuali jika ingin melakukan ignore file yang berbeda.
