---
title: Setup
tags:
  - go
---

# Instalasi

- Link download go: https://golang.org/dl
- Ikuti instruksi berdasarkan sistem operasi yang digunakan.

```bash
# check versi go
go version
```

# Project Hello World

- Buat folder hello
- Masuk ke folder hello
- Jalankan perintah berikut:

```bash
go mod init example.com/hello
```

- Buat file helloworld.go

```go
package main
import "fmt"

func main(){
    fmt.Println("Hello World!")
}
```

- Jalankan file helloworld.go

```bash
go run .\helloworld.go
```

- Atau simpan menjadi executable file

```bash
go build .\helloworld.go
```

- Hasil eksekusi

```bash
Hello World!
```

**Selanjutnya :** [Syntax](syntax.md)
