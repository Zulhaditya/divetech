---
title: Range
tags:
  - go
---

# Penjelasan

- Range mengulang elemen-elemen dalam berbagai struktur data.
- Range pada array menyediakan index dan nilai untuk setiap entri.

# Contoh:

```go
package main

import "fmt"

func main() {
    nums := []int{2, 3, 4}
    sum := 0

    for _, num := range nums {
        sum += num
    }

    fmt.Println("hasil penjumlahan:", sum)

    for i, num := range nums {
        if num == 4 {
          fmt.Println("index:", i)
        }
    }

    kvs := map[string]string{"a": "apple", "b": "banana"}
    for k, v := range kvs {
        fmt.Printf("%s -> %s\n", k, v)
    }

    pegawai := map[string]string{"nama": "aditya", "alamat": "jogja"}
    for nama, alamat := range pegawai {
        fmt.Printf("%s : %s\n", nama, alamat)
    }

    for k := range kvs {
        fmt.Println("key:", k)
    }

    for i, c := range "halo" {
        fmt.Println(i, c)
    }
}
```
