---
title: Variable
tags:
  - go
---

# Tipe variable pada Go

Go mempunyai beberapa tipe variabel yang dapat digunakan yaitu:

- **int** - menyimpan integer (angka) seperti 123 atau -123
- **float32** - menyimpan angka float seperti bilangan desimal. Contoh 19.99 atau -17.2
- **string** - menyimpan text, seperti "Hello World". Nilai string diapit oleh tanda kutip dua.
- **bool** - menyimpan value true atau false

Untuk penjelasan lebih lanjut mengenai tipe data dapat diakses di link ini:
https://www.w3schools.com/go/go_data_types.php

# Deklarasi variable

Pada Go, ada dua cara untuk mendeklarasikan variable yaitu:

1. Menggunakan **var**

```go
var variableName type = value
```

**Note**: kita harus selalu tentukan jenis tipe data dan value yang digunakan

2. Menggunakan simbol **:=**

```go
variablename := value
```

**Note:**

- Pada contoh tersebut, tipe variable dapat ditentukan dari nilainya (kompiler akan menentukan nilai berdasarkan value yang diberikan)
- Kita tidak mungkin menggunakan := tanpa memberikan nilai pada variable-nya

# Deklarasi variable dengan initial value

Jika nilai suatu variabel diketahui sejak awal, Anda dapat mendeklarasikan variabel tersebut dan menetapkan nilainya dalam satu baris:

```go
package main
import ("fmt")

func main() {
  var student1 string = "John" //type is string
  var student2 = "Jane" //type is inferred
  x := 2 //type is inferred

  fmt.Println(student1)
  fmt.Println(student2)
  fmt.Println(x)
}
```

# Deklarasi variable tanpa initial value

Di Go, semua variabel diinisialisasi. Jadi, jika Anda mendeklarasikan variabel tanpa nilai awal, nilainya akan ditetapkan ke nilai default dari tipenya:

```go
package main
import ("fmt")

func main() {
  var a string
  var b int
  var c bool

  fmt.Println(a)
  fmt.Println(b)
  fmt.Println(c)
}
```

# Penetapan nilai setelah deklarasi

Variabel dapat diberi nilai setelah dideklarasikan. Hal ini berguna jika nilainya pada awalnya tidak diketahui:

```go
package main
import ("fmt")

func main() {
  var student1 string
  student1 = "John"
  fmt.Println(student1)
}
```

# Perbedaan var dan :=

| **var**                                                                | **:=**                                                                       |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Dapat digunakan didalam dan diluar function                            | Hanya bisa digunakan didalam function                                        |
| Deklarasi variable dan penetapan value dapat dilakukan secara terpisah | Deklarasi variable dan penetapan value tidak dapat dilakukan secara terpisah |

# Multiple Declaration Variable

Pada Go, dimungkinkan untuk mendeklarasikan beberapa variabel dalam satu baris:

```go
package main
import ("fmt")

func main() {
  var d, e, f, g int = 1, 3, 5, 7

  fmt.Println(d)
  fmt.Println(e)
  fmt.Println(f)
  fmt.Println(g)
}
```

Jika kata kunci type tidak ditentukan, Anda dapat mendeklarasikan tipe variabel yang berbeda di baris yang sama:

```go
package main
import ("fmt")

func main() {
  var h, i = 6, "Hello"
  j, k := 7, "World!"

  fmt.Println(h)
  fmt.Println(i)
  fmt.Println(j)
  fmt.Println(k)
}
```

# Deklarasi variable didalam block

Deklarasi beberapa variabel juga dapat dikelompokkan menjadi satu blok agar lebih mudah dibaca:

```go
package main
import ("fmt")

func main() {
   var (
     x int
     y int = 1
     z string = "hello"
   )

  fmt.Println(x)
  fmt.Println(y)
  fmt.Println(z)
}
```

# Aturan penamaan variable

Variable dapat memiliki nama yang singkat seperti x dan y atau nama yang lebih deskriptif (usia, harga, nama mobil, dan sebagainya). Berikut adalah aturan penamaan-nya:

- Nama variabel harus dimulai dengan huruf atau karakter garis bawah \_
- Nama variabel tidak boleh diawali dengan angka
- Nama variabel hanya boleh berisi karakter alfanumerik dan garis bawah (a-z, A-Z, 0-9, dan \_ )
- Nama variabel peka case-sensitive (usia, Usia, dan AGE adalah tiga variabel berbeda)
- Tidak ada batasan panjang nama variabel
- Nama variabel tidak boleh mengandung spasi
- Nama variabel tidak boleh berupa keyword Go apapun

## Camel Case

```go
myVariableName = "John"
```

## Pascal Case

```go
MyVariableName = "John"
```

## Snake Case

```go
my_variable_name = "John"
```

**Selanjutnya :** [Data Type Basic](datatypebasic.md)
