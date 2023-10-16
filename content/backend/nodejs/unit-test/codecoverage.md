---
title: Code Coverage
tags:
  - jest
---

- Saat membuat unit test, kita ingin tahu apakah semua kode kita sudah tercakupi dengan semua skenario unit test kita atau belum.
- Jest memiliki fitur bernama Code Coverage, dengan ini kita bisa melihat kode mana yang sudah tercakupi dengan unit test, dan mana yang belum.
- Praktek ini adalah best practice dengan menentukan jumlah presentase kode yang harus tercukupi oleh unit test, misalnya 80%.

# Menggunakan Fitur Code Coverage

- Secara default, Jest tidak menggunakan fitur Code Coverage, jika kita ingin menggunakan Code Coverage, kita perlu mengubah konfigurasi Jest.
- Caranya kita tambahkan atribut collectAverage dengan nilai true di package.json
- https://jestjs.io/docs/configuration#collectcoverage-boolean

# Folder Coverage

- Jest Code Coverage secara otomatis membuat folder coverage di project kita.
- Jangan lupa untuk meng-ignore folder tersebut agar tidak ter-commit ke project kita.
- Folder coverage tersebut berisi laporan Code Coverage berupa file html yang bisa kita lihat dengan mudah.

# Coverage Threshold

- Jest memiliki fitur untuk menentukan Coverage Threshold dengan presentase, dimana jika Threshold-nya dibawah presentase yang sudah ditentukan, secara otomatis maka unit test akan gagal.
- Kita bisa tambahkan konfigurasi coverageThreshold.
- https://jestjs.io/docs/configuration#coveragethreshold-object

# Collect Coverage

- Kadang saat project kita sudah besar, kita ingin menentukan bagian kode mana yang ingin digunakan untuk menghitung code coverage nya.
- Kita bisa menggunakan atribute collectCoverageFrom
- https://jestjs.io/docs/configuration#collectcoveragefrom-array

**Selanjutnya :** [It Function](itfunction.md)
