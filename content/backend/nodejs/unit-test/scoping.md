---
title: Scoping
tags:
  - jest
---

- Saat kita menggunakan setup function, secara default akan dieksekusi pada setiap test() function yang terdapat di file unit test.
- Jest mempunyai fitur scoping atau grouping, dimana kita bisa membuat group unit test menggunakan function describe().
- Setup function yang dibuat di dalam describe() hanya digunakan untuk unit test didalam describe() tersebut.
- Namun setup function diluar describe() secara otomatis juga digunakan dalam describe().

**Selanjutnya :** [Code Coverage](codecoverage.md)