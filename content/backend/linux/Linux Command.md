---
title: Linux Command
created: '2025-04-23T16:45:03.186Z'
modified: '2025-04-23T16:47:04.783Z'
---

# Linux Command

---

## **📌 Daftar Perintah Linux Umum & Fungsinya**

### **1. 🗂️ Perintah Dasar Sistem**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `ls` | Menampilkan file & direktori | `ls -l` (detail) |
| `pwd` | Menampilkan direktori saat ini | `pwd` |
| `cd` | Pindah direktori | `cd /home` |
| `mkdir` | Buat direktori | `mkdir folder_baru` |
| `rm` | Hapus file/direktori | `rm -rf folder` (force) |
| `cp` | Salin file | `cp file1 file2` |
| `mv` | Pindah/rename file | `mv file1 /path/baru` |
| `touch` | Buat file kosong | `touch file.txt` |

---

### **2. 📄 Manajemen File & Teks**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `cat` | Tampilkan isi file | `cat file.txt` |
| `less` | Baca file (scroll) | `less log.txt` |
| `head` | Tampilkan 10 baris pertama | `head -n 5 file.txt` |
| `tail` | Tampilkan 10 baris terakhir | `tail -f log.txt` (real-time) |
| `grep` | Cari teks dalam file | `grep "error" log.txt` |
| `chmod` | Ubah izin file | `chmod 755 script.sh` |

---

### **3. 💻 Proses & Sistem**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `ps` | Lihat proses | `ps aux` |
| `top` | Monitor proses (real-time) | `top` |
| `kill` | Hentikan proses | `kill -9 1234` |
| `df` | Cek penggunaan disk | `df -h` |
| `free` | Cek RAM | `free -m` |

---

### **4. 🌐 Jaringan**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `ping` | Tes koneksi | `ping google.com` |
| `ifconfig`/`ip` | Konfigurasi jaringan | `ip a` |
| `ssh` | Remote ke server | `ssh user@192.168.1.1` |
| `scp` | Transfer file via SSH | `scp file.txt user@host:/path` |

---

### **5. 📦 Manajemen Paket**
#### **Debian/Ubuntu (APT)**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `apt update` | Update daftar paket | `sudo apt update` |
| `apt install` | Install paket | `sudo apt install nginx` |

#### **RHEL/CentOS (YUM)**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `yum install` | Install paket | `sudo yum install httpd` |

---

### **6. 🗜️ Kompresi & Arsip**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `tar` | Buat/ekstrak arsip | `tar -czvf arsip.tar.gz folder` |
| `zip` | Kompres ke `.zip` | `zip arsip.zip file1 file2` |

---

### **7. 👥 Pengguna & Grup**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `sudo` | Jalankan sebagai root | `sudo nano /etc/file` |
| `passwd` | Ubah password | `passwd` |

---

### **8. 🔍 Informasi Sistem**
| Perintah | Fungsi | Contoh |
|----------|--------|--------|
| `uname -a` | Info kernel & sistem | `uname -a` |
| `date` | Tampilkan tanggal/waktu | `date` |

---

### **9. 🔄 Pipe & Redirect**
| Contoh | Fungsi |
|--------|--------|
| `ls > file.txt` | Simpan output ke file |
| `grep "foo" file.txt | less` | Pipe output ke `less` |

---

### **10. ⚡ Shortcut Terminal**
| Shortcut | Fungsi |
|----------|--------|
| `Ctrl + C` | Berhentikan proses |
| `Ctrl + Z` | Pause proses |
| `!!` | Jalankan perintah terakhir |

---

### **🔎 Tips:**
- Gunakan `man [perintah]` untuk manual (contoh: `man ls`).
- `[perintah] --help` untuk bantuan cepat (contoh: `grep --help`).

---

Format **Markdown** ini siap digunakan di **GitHub**, **Notion**, atau dokumen lainnya. Mau ditambahkan contoh lebih detail untuk kategori tertentu? 😊
