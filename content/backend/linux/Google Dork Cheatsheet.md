---
tags: [cheatsheet]
title: Google Dork Cheatsheet
created: '2025-04-11T12:18:10.907Z'
modified: '2025-04-21T10:13:07.522Z'
---

# Google Dork Cheatsheet

## Pengertian Google Dork
Teknik menggunakan operator pencarian Google untuk menemukan informasi sensitif yang terpublikasi secara tidak sengaja di internet.

## Operator Dasar

| Operator | Fungsi | Contoh |
|----------|--------|--------|
| `site:` | Mencari di domain tertentu | `site:example.com` |
| `intitle:` | Mencari kata di judul halaman | `intitle:"login"` |
| `inurl:` | Mencari kata di URL | `inurl:admin` |
| `filetype:` | Mencari jenis file tertentu | `filetype:pdf` |
| `ext:` | Mencari ekstensi file | `ext:sql` |
| `intext:` | Mencari teks dalam konten | `intext:"password"` |
| `cache:` | Menampilkan versi cache | `cache:example.com` |
| `link:` | Mencari situs yang menautkan ke URL | `link:example.com` |
| `related:` | Mencari situs terkait | `related:example.com` |

## Kombinasi Penting untuk Pentesting

### 1. Mencari Halaman Login
```
intitle:"login" inurl:admin
intitle:"index of" intext:"login"
```

### 2. Mencari File Konfigurasi Sensitif
```
filetype:env intext:"DB_PASSWORD"
ext:ini intext:"password"
```


### 3. Mencari Database Terpapar

```
filetype:sql intext:"CREATE TABLE"
ext:sql intitle:"phpmyadmin"
```


### 4. Mencari Kamera IP

```
inurl:/view.shtml intitle:"Live View"
intitle:"webcamXP 5"
```


### 5. Mencari Panel Admin

```
inurl:/admin/login.php
intitle:"Admin Panel" intext:"Username"
```


### 6. Mencari Informasi Login Default

```
intitle:"default password" filetype:pdf
"default login" ext:txt
```


### 7. Mencari Directory Listing

```
intitle:"index of" intext:"/etc/passwd"
intitle:"index of" "parent directory"
```

### 8. Mencari Dokumen Sensitif

```
filetype:docx intext:"confidential"
filetype:xls intext:"password"
```


### 9. Mencari Sistem Vulnerable

```
intext:"Powered by WordPress 4.0"
intitle:"Apache Tomcat" intext:"Manage"
```


### 10. Mencari Informasi Error

```
intext:"error occurred while processing" filetype:log
"warning mysql" ext:log
```




