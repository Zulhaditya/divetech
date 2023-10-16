---
title: Comment
tags:
  - go
---

# Comment pada Go

- Komentar adalah text yang akan diabaikan saat dieksekusi
- Komentar dapat digunakan untuk menjelaskan kode dan membuatnya lebih mudah dibaca
- Komentar juga dapat digunakan untuk mencegah eksekusi kode saat menguji kode alternatif
- Go mendukung komentar satu baris atau banyak baris

# Single-line Comments

- Komentar satu baris menggunakan simbol //
- Setiap text yang berada di baris yang diawali simbol tersebut tidak akan dieksekusi

## Contoh:

```go
// Ini adalah single-comment
package main
import ("fmt")

func main() {
  // Ini adalah single-comment
  fmt.Println("Hello World!")
}
```

# Multi-line Comments

- Komentar banyak baris dimuali dengan simbol /_ dan diakhiri dengan _/
- Setiap text yang berada diantara simbol tersebut tidak akan dieksekusi

## Contoh:

```go
package main
import ("fmt")

func main() {
  /* The code below will print Hello World
  to the screen, and it is amazing */
  fmt.Println("Hello World!")
}
```

**Selanjutnya :** [Variable](variable.md)
