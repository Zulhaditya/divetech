---
title: Syntax
tags:
  - go
---

# Syntax pada Go

File Go memiliki beberapa bagian yaitu:

- Package declaration
- Import packages
- Functions
- Statement dan expressions

## Contoh:

```go
package main
import ("fmt")

func main() {
  fmt.Println("Hello World!")
}
```

### Penjelasan:

- Baris 1 : Pada Go, setiap program adalah bagian dari package. Kita mendefinisikannya menggunakan keyword **package**. Pada contoh diatas, program tersebut ada di **main** package
- Baris 2 : **import ("fmt")** adalah import package **fmt**
- Baris 3 : Blank line untuk mempermudah membaca code
- Baris 4 : **func main() {}** adalah function. Setiap kode yang ada di kurung kurawal akan dieksekusi
- Baris 5 : **fmt.Println()** adalah fungsi yang tersedia di package **fmt**. Digunakan untuk mengirim output/print text. Pada contoh diatas kita akan membuat output "Hello World!"
- Pada Go, semua executable file ada di **main** package

# Statement pada Go

- Pada Go, statement dipisahkan menggunakan tombol enter, atau dengan titik koma (;)
- Menekan tombol enter akan menambahkan ";" ke akhir baris secara implisit (tidak muncul pada kode)
- Tanda kurung kurawal kiri "{" tidak boleh berada di awal baris dan akan menghasilkan error

## Contoh:

```go
package main
import ("fmt")

func main()
{
  fmt.Println("Hello World!")
}
```

### Hasil:

```bash
./prog.go:4:6: missing function body
./prog.go:5:1: syntax error: unexpected semicolon or newline before {
```

# Compact Code pada Go

Kita dapat menulis kode yang lebih ringkas, seperti yang ditunjukkan di bawah ini (tidak disarankan karena membuat kode lebih sulit dibaca):

```go
package main; import ("fmt"); func main() { fmt.Println("Hello World!");}
```

**Selanjutnya :** [Comment](/backend/go/basic/comment.md)
