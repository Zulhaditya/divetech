---
title: Data Type Composite
tags:
  - go
---

# Non-Reference Types

## Arrays

- Array pada Go adalah barisan value / nilai dengan panjang tetap dari tipe yang sama
- Saat kita menetapkan array ke variable lain, seluruh array akan disalin.
- Jika kita meneruskan array sebagai argumen pada sebuah fungsi, akan membuat seluruh salinan array, tidak hanya meneruskan alamatnya saja
- Kita tidak dapat menetapkan array ke array lain dengan tipe yang sama dengan panjang yang berbeda
- Jika meneruskan array sebagai argumen sebuah fungsi, maka size juga akan mengikuti

**Contoh:**

```go
package main

import "fmt"

func main() {
    //Declare a array
    sample := [3]string{"a", "b", "c"}
    print(sample)
}

func print(sample [3]string) {
    fmt.Println(sample)
}
```

**Hasil:**

```go
[a b c]
```

## Structs

Pada Go, struct merupakan sebuah collection field atau bisa juga disebut tipe data object. Struct merupakan sebuah wadah yang menyimpan tipe data yang beragam. Misalnya, jika kita mempunyai data karyawan, karyawan dapat memiliki atribute seperti dibawah ini:

- Name - tipe string
- Usia - tipe int
- Gaji - tipe float64

**Contoh:**

```go
package main
import (
    "fmt"
)
//Declare a struct
type employee struct {
    name   string
    age    int
    salary float64
}
func main() {
    //Initialize a struct without named fields
    employee1 := employee{"John", 21, 1000}
    fmt.Println(employee1)

    //Initialize a struct with named fields
    employee2 := employee{
        name:   "Sam",
        age:    22,
        salary: 1100,
    }
    fmt.Println(employee2)

    //Initializing only some fields. Other values are initialized to default zero value of that type
    employee3 := employee{name: "Tina", age: 24}
    fmt.Println(employee3)
}
```

**Hasil:**

```go
{John 21 1000}
{Sam 22 1100}
{Tina 24 0}
```

# References Types

## Slices

Slice merupakan tipe data yang dinamis yang mengacu pada elemen array. Berbeda dengan array karena memiliki ukuran yang tetap, slice memiliki ukuran yang dinamis dan lebih fleksible. Slice merupakan tipe referensi karena secara internal mereferensikan kepada array tertentu. Terbagi menjadi 3 yaitu:

- Alamat ke array yang mendasarinya
- Length
- Capacity

Slice dibuat berdasarkan tipe elemen array yang mendasarinya, bukan berdasarkan panjang atau kapasitasnya. Jadi, 2 slice akan memiliki tipe yang sama jika tipe array yang mendasarinya sama. Fungsi append bawaan dapat digunakan untuk menambahkan lebih banyak nilai array ke array yang mendasarinya. Jika saat menggunakan fungsi append panjang slice bertambah sesuai kapasitas saat ini, maka slice baru akan dialokasikan dengan kapasitas 2 kali lipat dan elemen slice saat ini akan disalin kedalam array yang mendasarinya.

**Contoh:**

```go
package main

import "fmt"

func main() {
    //Declare a slice using make
    s := make([]string, 2, 3)
    fmt.Println(s)

    //Direct intialization
    p := []string{"a", "b", "c"}
    fmt.Println(p)

    //Append function
    p = append(p, "d")
    fmt.Println(p)

    //Iterate over a slcie
    for _, val := range p {
        fmt.Println(val)
    }
}
```

**Hasil:**

```go
[ ]
[a b c]
[a b c d]
a
b
c
d
```

## Channels

Channels menyediakan sinkronisasi dan komunikasi antar goroutine. Kita dapat menganggapnya sebagai sebuah pipa yang melalui goroutine untuk dapat mengirim dan menerima nilai. Operasi <- digunakan untuk mengirim atau menerima, dengan arah panah untuk menentukan arah aliran data.

```go
ch <- val    //Sending a value present in var variable to channel
val := <-cha  //Receive a value from  the channel and assign it to val variable
```

Channel terbagi menjadi 2 jenis yaitu:

- **Unbuffered Channel**
  - Pengiriman data pada suatu channel akan diblokir kecuali ada goroutine lain yang akan diterima
  - Penerimaan data akan diblokir hingga ada goroutine lain yang akan dikirim
- **Buffered Channel**
  - Pengiriman data pada saluran buffer hanya diblokir ketika buffer penuh
  - Menerima satu-satunya blok yang buffer salurannya kosong

Channel menyimpan data jenis tertentu pada suatu waktu. Saat membuat channel, tipe data 1 harus ditentukan untuk menginisialisasi channel baru. Channel dapat dibuat menggunakan perintah make. Contoh dibawah ini, kita akan membuat channel yang menampung data dengan tipe string:

```go
events := make(chan string)  //Unbuffered channel
events2 := make(chan string, 2)  //Buffered channel of length 2
```

**Closing channel:**
Fungsi close() dapat digunakan untuk menutup channel. Menutup channel berarti tidak ada lagi nilai yang dapat dikirim ke channel tersebut.

**Contoh Buffered Channel:**

```go
package main

import "fmt"

func main() {
    //Creating a buffered channel of length 3
    eventsChan := make(chan string, 3)
    eventsChan <- "a"
    eventsChan <- "b"
    eventsChan <- "c"
    //Closing the channel
    close(eventsChan)
    for event := range eventsChan {
        fmt.Println(event)
    }
}
```

**Hasil:**

```go
a
b
c
```

**Contoh UnBuffered Channel:**

```go
package main

import "fmt"

func main() {
    eventsChan := make(chan string)
    go sendEvents(eventsChan)
    for event := range eventsChan {
        fmt.Println(event)
    }
}

func sendEvents(eventsChan chan<- string) {
    eventsChan <- "a"
    eventsChan <- "b"
    eventsChan <- "c"
    close(eventsChan)
}
```

**Hasil:**

```go
a
b
c
```

## Maps

Maps merupakan tipe data bawaan Go yang mirip dengan hash untuk memetakan key pada suatu value. Maps adalah tipe data yang direferensikan. Saat kita menugaskan satu map ke map yang lainnya, keduanya mengacu pada map dasar yang sama.

**Zero Value** : Nilai zero value pada maps adalah nil

**Declare:**

- Sebuah map dapat dideklarasikan menggunakan keyword var yang menentukan tipe key dan valuenya. Contoh untuk deklarasi map dengan nama:

```go
var employeeSalary map[string]int
```

**Inisialisasi:**

- Menggunakan make

```go
var employeeSalary make(map[string]int)
```

- Menggunakan kurung kurawal. Kita dapat menentukan nilai literal map atau membiarkan tanda kurung kurawalnya kosong

```go
//Empty braces
employeeSalary := map[string]int{}

//Specify values
employeeSalary := map[string]int{
"John": 1000
"Sam": 2000
}
```

**Operasi:**

- Menambahkan ke map

```go
employeeSalary["John"] = 1000
```

- Mendapatkan value dari map

```go
salary := employeeSalary["John"]
```

- Hapus key dari map

```go
delete(employeeSalary, "John")
```

**Contoh lengkap:**

```go
package main

import "fmt"

func main() {
    //Declare
    var employeeSalary map[string]int
    fmt.Println(employeeSalary)

    //Intialize using make
    employeeSalary2 := make(map[string]int)
    fmt.Println(employeeSalary2)

    //Intialize using map lieteral
    employeeSalary3 := map[string]int{
        "John": 1000,
        "Sam":  1200,
    }
    fmt.Println(employeeSalary3)

    //Operations
    //Add
    employeeSalary3["Carl"] = 1500

    //Get
    fmt.Printf("John salary is %d\n", employeeSalary3["John"])

    //Delete
    delete(employeeSalary3, "Carl")

    //Print map
    fmt.Println("\nPrinting employeeSalary3 map")
    fmt.Println(employeeSalary3)
}
```

**Hasil:**

```go
map[]
map[]
map[John:1000 Sam:1200]
John salary is 1000

Printing employeeSalary3 map
map[John:1000 Sam:1200]
```

## Pointers

Pointer adalah variabel yang menyimpan alamat memori dari variabel lain. Nilai nol dari sebuah pointer adalah nil.
**Contoh:**

```go
package main

import "fmt"

func main() {
    //Declare
    var b *int
    a := 2
    b = &a

    //Will print a address. Output will be different everytime.
    fmt.Println(b)
    fmt.Println(*b)
    b = new(int)
    *b = 10
    fmt.Println(*b)
}
```

**Hasil:**

```go
0xc000018080
2
10
```

## Functions

Pada Go, fungsi memiliki nilai dan dapat diberikan seperti sebuah nilai. Pada dasarnya, fungsi dapat digunakan sebagai objek pertama dan dapat diteruskan:

```go
func some_func_name(arguments) return_values
```

Suatu fungsi memiliki nama, argumen, dan return value. Ada beberapa perbedaan antara method dan function pada Go.

**Method:**

```go
func (receiver receiver_type) some_func_name(arguments) return_values
```

Dari contoh diatas, method memiliki argumen penerima. Penerima dapat berupa struct atau tipe lainnya. Method memiliki akses ke properti penerima dan dapat memanggil metode penerima lainnya.

**Contoh:**

```go
package main

import "fmt"

func main() {
    add := func(x, y int) int {
        return x + y
    }
    fmt.Println(add(1, 2))
}

func doOperation(fn func(int, int) int, x, y int) int {
    return fn(x, y)
}
```

**Hasil:**

```go
3
```

## Interface

Interface adalah tipe data pada Go yang merupakan koleksi dari method. Tipe data apapun yang mengimplementasikan semua method dari interface adalah jenis tipe data interface. Nilai nol dari sebuah interface adalah nil.

### Interface diimplementasikan secara implisit

Tidak ada deklarasi secara eksplisit untuk menggunakan interface. Faktanya, pada Go tidak ada keyword implements yang mirip dengan Java.

**Contoh:**

```go
package main

import "fmt"

type shape interface {
    area() int
}

type square struct {
    side int
}

func (s *square) area() int {
    return s.side * s.side
}

func main() {
    var s shape
    s = &square{side: 4}
    fmt.Println(s.area())
}
```

**Hasil:**

```go
16
```

### Special case pada interface yang kosong

Interface kosong tidak memiliki metode, maka secara default semua tipe konkret mengimplementasikan interface yang kosong. Jika kita menulis fungsi yang menerima interface kosong maka kita dapat meneruskan tipe apa pun ke fungsi itu. Lihat kode berikut:

```go
package main

import "fmt"

func main() {
    test("thisisstring")
    test("10")
    test(true)
}

func test(a interface{}) {
    fmt.Printf("(%v, %T)\n", a, a)
}
```

**Selanjutnya :** [Looping](looping.md)
