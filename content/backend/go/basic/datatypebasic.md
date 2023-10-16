---
title: Data Type Basic
tags:
  - go
---

Golang adalah bahasa pemrograman yang diketik secara statis dimana setiap variabel memiliki tipe datanya masing-masing. Go memiliki beberapa tipe data bawaan dan dibagi menjadi dua tipe yaitu:

- Basic Type
- [[7 - Tipe Data (Composite)]]

# Basic Type

## Integers (Signed dan UnSigned)

### Signed

| Type  | Size               |
| ----- | ------------------ |
| int   | Platform Dependent |
| int8  | 8 bits / 1 byte    |
| int16 | 16 bits / 2 byte   |
| int32 | 32 bits / 4 byte   |
| int64 | 64 bits / 8 byte   |

#### int

**Size: Bergantung pada platform**

- Pada mesin 32 bit, ukuran int akan menjadi 32 bit atau 4 byte
- Pada mesin 64 bit, ukuran int akan menjadi 64 bit atau 8 byte

**Range: Bergantung pada platform**

- Pada mesin 32 bit, kisaran int adalah -2 pangkat 31 hingga 2 pangkat 31 -1
- Pada mesin 64 bit, kisaran int adalah -263 hingga 263 -1

**Penggunaan:**

- Jika mesinnya 32 bit dan rentang yang dibutuhkan lebih besar dari -2 pangkat 31 sampai 2 pangkat 31 -1, gunakan int64 sebagai gantinya int. Perhatikan bahwa dalam kasus ini untuk int64, 2 alamat memori 32-bit membentuk angka 64-bit secara bersamaan
- Jika rentangnya lebih kecil maka gunakan tipe integer yang sesuai.

**Contoh:**

```go
package main

import (
    "fmt"
    "math/bits"
    "reflect"
    "unsafe"
)

func main() {
    sizeOfIntInBits := bits.UintSize
    fmt.Printf("%d bits\n", sizeOfIntInBits)

    var a int
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))

    b := 2
    fmt.Printf("b's typs is %s\n", reflect.TypeOf(b))
}
```

**Hasil:**

```go
64 bits
8 bytes
a's type is int
b's typs is int
```

#### int32

**Size: 32 bits atau 4 byte**

**Range: -2 pangkat 31 sampai 2 pangkat 31 -1**

**Contoh:**

```go
package main

import (
    "fmt"
    "reflect"
    "unsafe"
)

func main() {
    //Declare a int32
    var a int32 = 2

    //Size of int32 in bytes
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))
}
```

**Hasil:**

```go
4 bytes
a's type is int32
```

### UnSigned

| Type   | Size               |
| ------ | ------------------ |
| uint   | Platform Dependent |
| uint8  | 8 bits / 1byte     |
| uint16 | 16 bits / 2byte    |
| uint32 | 32 bits / 4 byte   |
| uint64 | 64 bits / 8 byte   |

#### uint

**Size: Bergantung pada platform**

- Pada mesin 32 bit, ukuran int akan menjadi 32 bit atau 4 byte
- Pada mesin 64 bit, ukuran int akan menjadi 64 bit atau 8 byte

**Range: Bergantung pada platform**

- Pada mesin 32 bit, kisaran int adalah -2 pangkat 31 hingga 2 pangkat 31 -1
- Pada mesin 64 bit, kisaran int adalah -2 pangkat 63 hingga 2 pangkat 63 -1

**Penggunaan:**

- Jika mesinnya 32 bit dan rentang yang dibutuhkan lebih besar dari -2 pangkat 31 sampai 2 pangkat 31 -1, gunakan int64 sebagai gantinya int. Perhatikan bahwa dalam kasus ini untuk int64, 2 alamat memori 32-bit membentuk angka 64-bit secara bersamaan
- Jika rentangnya lebih kecil maka gunakan tipe integer yang sesuai.

**Contoh:**

```go
package main

import (
    "fmt"
    "math/bits"
    "reflect"
    "unsafe"
)

func main() {
    //This is computed as const uintSize = 32 << (^uuint(0) >> 32 & 1) // 32 or 64
    sizeOfuintInBits := bits.UintSize
    fmt.Printf("%d bits\n", sizeOfuintInBits)

    var a uint
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))
}
```

**Hasil:**

```go
64 bits
8 bytes
a's type is uint
```

#### uint8

**Penggunaan:**

- Tujuannya adalah untuk digunakan bersama dengan unsafe.Pointer terutama digunakan untuk akses memori yang tidak aman
- Bila kita ingin menyimpan nilai alamat penunjuk untuk mencetak atau menyimpannya. Karena alamatnya hanya disimpan dan tidak merujuk apa pun, objek terkait dapat dikumpulkan dari sampah.

**Contoh:**

```go
package main
import (
    "fmt"
    "unsafe"
)
type sample struct {
    a int
    b string
}
func main() {
    s := &sample{a: 1, b: "test"}

   //Getting the address of field b in struct s
    p := unsafe.Pointer(uintptr(unsafe.Pointer(s)) + unsafe.Offsetof(s.b))

    //Typecasting it to a string pointer and printing the value of it
    fmt.Println(*(*string)(p))
}
```

#### uintptr

Merupakan tipe data unsigned yang cukup besar untuk menampung pointer apapun. Size dan range tergantung pada jenis platform.

**Properti:**

- Dapat diubah menjadi unsafe.pointer dan sebaliknya
- Dapat melakukan fungsi aritmatika
- uintptr merupakan alamat penunjuk / pointer yang tidak mereferensikan objek apapun. Nilainya tidak akan diperbaharui jika objek nya diubah. Misalnya ketika goroutine berubah, objek yang bersangkutan hanya berupa sampah yang dikumpulkan

**Penggunaan:**

- Digunakan bersama dengan unsafe.Pointer untuk akses memori yang tidak aman / unsafe
- Jika kita ingin menyimpan alamat pointer dengan tujuan mencetak atau menyimpannya. Karena alamat hanya disimpan dan tidak merujuk pada objek tertentu

**Contoh:**

```go
package main

import (
    "fmt"
    "reflect"
    "unsafe"
)

func main() {
    //Declare a uint8

    var a uint8 = 2

    //Size of uint8 in bytes
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))
}
```

**Hasil:**

```go
1 bytes
a's type is uint8
```

## Float

Float merupakan tipe data untuk menyimpan bilangan desimal. Ada 2 jenis float yaitu:

| Type    | Size              |
| ------- | ----------------- |
| float32 | 32 bits / 4 bytes |
| float64 | 64 bits / 8 bytes |

float64 adalah tipe float default. Saat kita menginisialisasi variabel dengan nilai desimal dan tidak menentukan tipe float, tipe default yang disimpulkan adalah float64.

### float32

float32 menggunakan format floating point presisi tunggal untuk menyimpan nilai. Pada dasarnya ini adalah kumpulan semua angka floating-point 32-bit IEEE-754. 32 bit tersebut dibagi menjadi – 1 bit tanda, 8 bit eksponen, dan 23 bit mantissa. float 32 berukuran setengah dari float 64 dan relatif lebih cepat pada beberapa arsitektur mesin.

**Penggunaan:**

- Jika di memori sistem Anda ada hambatan dan jangkauannya kurang, maka float32 dapat digunakan

**Contoh:**

```go
package main

import (
    "fmt"
    "reflect"
    "unsafe"
)

func main() {
    //Declare a float32
    var a float32 = 2

    //Size of float32 in bytes
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))
}
```

**Hasil:**

```go
4 bytes
a's type is float32
```

### float64

float64 menggunakan format titik mengambang presisi ganda untuk menyimpan nilai. Pada dasarnya ini adalah kumpulan semua angka floating-point 64-bit IEEE-754. 64 bit dibagi menjadi – 1-bit tanda, 11 bit eksponen, 52 bit mantissa. float64 membutuhkan ukuran dua kali lebih besar dibandingkan float32 tetapi dapat mewakili angka lebih akurat daripada float32.

**Penggunaan:**

- Ketika presisi yang dibutuhkan sangat tinggi

**Contoh:**

```go
package main

import (
    "fmt"
    "reflect"
    "unsafe"
)

func main() {
    //Declare a float64
    var a float64 = 2

    //Size of float64 in bytes
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))

    //Default is float64 when you don't specify a type
    b := 2.3
    fmt.Printf("b's type is %s\n", reflect.TypeOf(b))
}
```

**Hasil:**

```go
8 bytes
a's type is float64
b's type is float64
```

## Complex Numbers

Complex Numbers terbagi menjadi 2 yaitu:

| Type       | Size                                       |
| ---------- | ------------------------------------------ |
| complex64  | Bilangan nyata dan imajiner adalah float32 |
| complex128 | Bilangan nyata dan imajiner adalah float64 |

Bilangan complex numbers secara default menggunakan complex128

### complex64

**Contoh:**

```go
package main
import (
    "fmt"
    "reflect"
    "unsafe"
)
func main() {
    var a float32 = 3
    var b float32 = 5

    //Initialize-1
    c := complex(a, b)

    //Initialize-2
    var d complex64
    d = 4 + 5i

    //Print Size
    fmt.Printf("c's size is %d bytes\n", unsafe.Sizeof(c))
    fmt.Printf("d's size is %d bytes\n", unsafe.Sizeof(d))

    //Print type
    fmt.Printf("c's type is %s\n", reflect.TypeOf(c))
    fmt.Printf("d's type is %s\n", reflect.TypeOf(d))

    //Operations on complex number
    fmt.Println(c+d, c-d, c*d, c/d)
}
```

**Hasil:**

```go
c's size is 8 bytes
d's size is 8 bytes
c's type is complex64
d's type is complex64
(7+10i) (-1+0i) (-13+35i) (0.902439+0.12195122i)
```

### complex128

**Contoh:**

```go
package main

import (
    "fmt"
    "reflect"
    "unsafe"
)

func main() {
    var a float64 = 3
    var b float64 = 5

    //Initialize-1
    c := complex(a, b)

    //Initialize-2. When don't specify a type , the default type will be complex128
    d := 4 + 5i

    //Print Size
    fmt.Printf("c's size is %d bytes\n", unsafe.Sizeof(c))
    fmt.Printf("d's size is %d bytes\n", unsafe.Sizeof(d))

    //Print type
    fmt.Printf("c's type is %s\n", reflect.TypeOf(c))
    fmt.Printf("d's type is %s\n", reflect.TypeOf(d))

    //Operations on complex number
    fmt.Println(c+d, c-d, c*d, c/d)
}
```

**Hasil:**

```go
c's size is 16 bytes
d's size is 16 bytes
c's type is complex128
d's type is complex128
(7+10i) (-1+0i) (-13+35i) (0.902439024390244+0.12195121951219513i)
```

## Byte

Tipe data byte pada Go adalah alias untuk uint8 yang berarti nilai integer. Nilai integer ini terdiri dari 8 bit dan mewakili satu byte yaitu angka antara 0 - 255. Oleh karena itu, satu byte mewakili karakter ASCII. Go tidak memiliki tipe data 'char'.

**Contoh:**

```go
package main
import (
    "fmt"
    "reflect"
    "unsafe"
)
func main() {
    var r byte = 'a'

    //Print Size
    fmt.Printf("Size: %d\n", unsafe.Sizeof(r))

    //Print Type
    fmt.Printf("Type: %s\n", reflect.TypeOf(r))

    //Print Character
    fmt.Printf("Character: %c\n", r)
    s := "abc"

    //This will the decimal value of byte
    fmt.Println([]byte(s))
}
```

**Hasil:**

```go
Size: 1
Type: uint8
Character: a
[97 98 99]
```

## Rune

Tipe data rune pada Go adalah alias untuk int32 yang berarti nilai integer. Nilai ini dimaksudkan untuk mewakili titik kode unicode. Untuk memahami lebih jelas terkait rune dan unicode dapat mengunjungi blog ini : http://www.joelonsoftware.com/articles/Unicode.html

### UniCode

Unicode merupakan superset karakter ASCII yang memberikan nomor unik pada setiap karakter yang ada. Nomor unik ini disebut Unicode Code Point.

**Contoh:**

- Angka 0 direpresentasikan sebagai Unicode Point U+0030 (nilai desimal -48)
- Small case b direpresentasikan sebagai Unicode Point U+0062 (nilai desimal -98)
- Simbol pound £ direpresentasikan sebagai Unicode Point U+00A3 (nilai desimal – 163)

### UTF-8

- utf-8 menyimpan setiap Unicode Point baik menggunakan 1, 2, 3 atau 4 byte. Poin ASCII disimpan menggunakan 1 byte. Itu sebabnya rune adalah alias untuk int32 karena Unicode Point bisa maksimal 4 byte di Go karena di GO setiap string dikodekan menggunakan utf-8.
- Setiap rune dimaksudkan untuk merujuk pada satu Unicode Point. Misalnya jika Anda mencetak string setelah mengetiknya ke array rune maka itu akan mencetak Unicode Point untuk setiap karakter. Untuk string di bawah ini keluaran “0b£” akan menjadi – [U+0030 U+0062 U+00A3]

**Contoh:**

```go
package main
import (
    "fmt"
    "reflect"
    "unsafe"
)
func main() {
    r := 'a'

    //Print Size
    fmt.Printf("Size: %d\n", unsafe.Sizeof(r))

    //Print Type
    fmt.Printf("Type: %s\n", reflect.TypeOf(r))

    //Print Code Point
    fmt.Printf("Unicode CodePoint: %U\n", r)

    //Print Character
    fmt.Printf("Character: %c\n", r)
    s := "0b£"

    //This will print the Unicode Points
    fmt.Printf("%U\n", []rune(s))

    //This will the decimal value of Unicode Code Point
    fmt.Println([]rune(s))
}
```

**Hasil:**

```go
Size: 4
Type: int32
Unicode CodePoint: U+0061
Character: a
[U+0030 U+0062 U+00A3]
[48 98 163]
```

## String

String adalah tipe data byte yang read-only pada Go. String dapat diinisialisasikan dengan dua cara yaitu:

- Menggunakan double quotes "contoh string"
  String dalam tanda double quotes mengikuti urutan escape. Misalnya jika string berisi \n maka saat mencetak akan ada baris baru
- Menggunakan back quotes `contoh string`
  String dalam tanda back quotes hanyalah string mentah dan tidak mengikuti rangkaian escape apa pun

Setiap karakter dalam string akan menempati beberapa byte tergantung pada pengkodean yang digunakan. Misalnya dalam string yang dikodekan utf-8, setiap karakter akan menempati antara 1-4 byte. Dalam utf-8 , karakter a atau b dikodekan menggunakan 1 byte sedangkan karakter tanda pagar £ dikodekan menggunakan dua byte . Oleh karena itu string “ab£” akan menghasilkan 4 byte ketika Anda mengonversi string menjadi array byte dan mencetaknya seperti di bawah ini:

```go
s := "ab£"
fmt.Println([]byte(s))
```

**Hasil:**

```go
[48 98 194 163]
```

**Contoh:**

```go
package main
import (
    "fmt"
)
func main() {
    //String in double quotes
    x := "this\nthat"
    fmt.Printf("x is: %s\n", x)

    //String in back quotes
    y := `this\nthat`
    fmt.Printf("y is: %s\n", y)
    s := "ab£"

    //This will print the byte sequence.
    //Since character a and b occupies 1 byte each and £ character occupies 2 bytes.
    //The final output will 4 bytes
    fmt.Println([]byte(s))

    //The output will be 4 for same reason as above
    fmt.Println(len(s))

    //range loops over sequences of byte which form each character
    for _, c := range s {
        fmt.Println(string(c))
    }

    //Concatenation
    fmt.Println("c" + "d")
}
```

**Hasil:**

```go
x is: this
that
y is: this\nthat
[97 98 194 163]
4
a
b
£
cd
```

## Booleans

Tipe data boolean akan mengembalikan nilai **true** atau **false**. Default valuenya adalah false
**Operasi:**

- AND - &&
- OR - ||
- Negasi - !

**Contoh:**

```go
package main

import "fmt"

func main() {
    //Default value will be false it not initialized
    var a bool
    fmt.Printf("a's value is %t\n", a)

    //And operation on one true and other false
    andOperation := 1 < 2 && 1 > 3
    fmt.Printf("Ouput of AND operation on one true and other false %t\n", andOperation)

    //OR operation on one true and other false
    orOperation := 1 < 2 || 1 > 3
    fmt.Printf("Ouput of OR operation on one true and other false: %t\n", orOperation)

    //Negation Operation on a false value
    negationOperation := !(1 > 2)
    fmt.Printf("Ouput of NEGATION operation on false value: %t\n", negationOperation)
}
```

**Hasil:**

```go
a's value is false
Ouput of AND operation on one true and other false false
Ouput of OR operation on one true and other false: true
Ouput of NEGATION operation on false value: true
```

**Selanjutnya :** [Data Type Composite](datatypecomposite.md)
