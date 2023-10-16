---
title: Looping
tags:
  - go
---

- Go hanya memiliki satu jenis perulangan, yaitu perulangan for
- Perulangan for dasar memiliki tiga komponen yang dipisahkan oleh titik koma:
  - Pernyataan init: dieksekusi sebelum iterasi pertama
  - Ekspresi kondisi: dievaluasi sebelum setiap iterasi
  - Pernyataan post: dieksekusi pada akhir setiap iterasi
- Pernyataan init sering kali merupakan deklarasi variable pendek, dan variable yang dideklarasikan di init hanya digunakan pada scope perulangan for
- Perulangan akan berhenti melakukan iterasi setelah kondisi boolean bernilai false

**Note:**
Tidak seperti bahasa lain seperti C, Java, atau JavaScript, tidak ada tanda kurung yang mengelilingi tiga komponen pernyataan for dan tanda kurung kurawal { } selalu diperlukan.

**Contoh:**

```go
package main

import "fmt"

func main() {
    perulangan_for()
}

// perulangan for
func perulangan_for() {
    fmt.Printf("===== Perulangan For =====\n")

    sum := 0
    for i := 0; i < 10; i++ {
        sum += i
    }
    fmt.Println(sum)

}
```

**Selanjutnya :** [Condition](condition.md)
