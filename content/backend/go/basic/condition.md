---
title: Condition
tags:
  - go
---

# If Else

Percabangan if pada Go seperti perulangan for, ekspresi tidak perlu diapit oleh tanda kurung ( ) tetapi harus diberi tanda kurung kurawal.
**Contoh:**

```go
package main

import (
	"fmt"
)

func main() {
	fmt.Printf("========= If-else =========\n")
	x := 7
	maksimal := 10

	if x > maksimal {
		fmt.Printf("Nilai x adalah %d, lebih besar dari nilai max\n", x)
	} else {
		fmt.Printf("Nilai x adalah %d, lebih kecil dari nilai max\n", x)
	}

	fmt.Printf("========= Dengan Init Statement =========\n")
	if angka := 7; angka < 0 {
		fmt.Println(angka, "adalah bilangan negatif")
	} else if angka < 10 {
		fmt.Println(angka, "memiliki 1 digit")
	} else {
		fmt.Println(angka, "memiliki banyak digit")
	}
}
```

# Switch

Switch digunakan untuk memilih salah satu pilihan dari banyak blok kode yang akan dieksekusi:

```go
package main

import {
  "fmt"
  "time"
}

func main() {
  fmt.Printf("========= Switch =========\n")
	today := time.Now()

	switch today.Day() {
	case 5:
		fmt.Println("Ini adalah hari ke-5, bersihkan rumah!")
	case 10:
		fmt.Println("Ini adalah hari ke-10, isi galon di dispenser.")
	case 15:
		fmt.Println("Ini adalah hari ke-15, mandikan kucingmu!")
	case 25:
		fmt.Println("Ini adalah hari ke-25, beli peralatan kos.")
	case 31:
		fmt.Println("Ini adalah hari ke-31, pergi ke pasar!")
	default:
		fmt.Println("Tidak ada informasi yang tersedia hari ini!")
	}
}
```

# Switch dengan fallthrough

Fallthrough digunakan untuk memaksa eksekusi berturut-turut pada blok kode tertentu:

```go
package main

import (
  "fmt"
  "date"
)

func main() {
  fmt.Printf("========= Switch Fallthrough =========\n")
	today := time.Now()

	switch today.Day() {
	case 5:
		fmt.Println("Pergi memancing.")
		fallthrough
	case 10:
		fmt.Println("Memasak indomie")
		fallthrough
	case 15:
		fmt.Println("Kunjungi rumah nenek")
		fallthrough
	case 25:
		fmt.Println("Bermain petak umpet")
		fallthrough
	case 31:
		fmt.Println("Lari di pinggi kolam")
	default:
		fmt.Println("Tidak terdapat kegiatan hari ini")
	}
}
```

# Switch dengan multiple cases

Switch multiple case digunakan untuk memlih blok kode umum untuk banyak kasus yang sama:

```go
package main

import (
  "fmt"
  "main"
)

func main() {
	fmt.Printf("========= Switch Multiple Cases =========\n")

  today := time.Now()
	var t int = today.Day()

	switch t {
	case 5, 10, 15:
		fmt.Println("Bersihkan kebun dibelakang rumah")
	case 25, 26, 27:
		fmt.Println("Nonton anim favorit")
	case 31:
		fmt.Println("Pergi nongkrong")
	default:
		fmt.Println("Tidak ada kegiatan hari ini!")
	}
}
```

# Switch dengan conditional operator

Case statement dapat juga menggunakan conditional operator:

```go
package main

import (
  "fmt"
  "date"
)

func main() {
  fmt.Printf("========= Switch Conditional Cases =========\n")

	today := time.Now()

	switch {
	case today.Day() < 5:
		fmt.Println("Belajar Golang")
	case today.Day() <= 10:
		fmt.Println("Beli beberapa snack")
	case today.Day() > 15:
		fmt.Println("Berobat ke apotek")
	case today.Day() == 25:
		fmt.Println("Pergi ke bioskop")
	default:
		fmt.Println("Kegiatan hari ini kosong, bebas menggabut")
	}
}
```

# Switch dengan inisialisasi

Keyword switch dapat dibuat dengan inisialisasi sederhana dimana variable lokal pada blok dapat dideklarasikan dan digunakan:

```go
package main
import(
  "fmt"
  "date"
)

fmt.Printf("========= Switch Initializer =========\n")

	switch today := time.Now(); {
	case today.Day() < 5:
		fmt.Println("Clean your house.")
	case today.Day() <= 10:
		fmt.Println("Buy some wine.")
	case today.Day() > 15:
		fmt.Println("Visit a doctor.")
	case today.Day() == 25:
		fmt.Println("Buy some food.")
	default:
		fmt.Println("No information available for that day.")
	}
```

**Selanjutnya** : [Range](range.md)