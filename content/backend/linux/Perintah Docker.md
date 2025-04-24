---
tags: [cheatsheet]
title: Perintah Docker
created: '2025-04-07T05:58:26.038Z'
modified: '2025-04-21T10:12:36.722Z'
---

# Perintah Docker

### **🐳 Daftar Perintah Docker Umum**
#### **Manajemen Container**
| Perintah | Deskripsi | Contoh |
|----------|-----------|--------|
| `docker ps` | Lihat container yang sedang berjalan | `docker ps` |
| `docker ps -a` | Lihat semua container (termasuk yang stopped) | `docker ps -a` |
| `docker start` | Jalankan container yang stopped | `docker start dvwa` |
| `docker stop` | Hentikan container | `docker stop juice-shop` |
| `docker restart` | Restart container | `docker restart dvwa` |
| `docker rm` | Hapus container | `docker rm juice-shop` |
| `docker logs` | Lihat log container | `docker logs -f dvwa` |

#### **Manajemen Image**
| Perintah | Deskripsi | Contoh |
|----------|-----------|--------|
| `docker pull` | Download image dari Docker Hub | `docker pull vulnerables/web-dvwa` |
| `docker images` | Lihat daftar image | `docker images` |
| `docker rmi` | Hapus image | `docker rmi bkimminich/juice-shop` |

---

### **📌 Perintah Khusus DVWA**
#### **1. Menjalankan DVWA**
```bash
docker run -d -p 8080:80 --name dvwa vulnerables/web-dvwa
```
- **`-d`**: Detached mode (jalan di background).
- **`-p 8080:80`**: Port forwarding (host:container).
- **`--name dvwa`**: Beri nama container.

#### **2. Setup Database DVWA**
1. Akses DVWA di browser:  
   ```
   http://localhost:8080
   ```
2. Login default:  
   - Username: `admin`  
   - Password: `password`  
3. Klik **"Setup / Reset DB"** untuk inisialisasi database.

#### **3. Hentikan dan Hapus DVWA**
```bash
docker stop dvwa && docker rm dvwa
```

---

### **🍊 Perintah Khusus OWASP Juice Shop**
#### **1. Menjalankan Juice Shop**
```bash
docker run -d -p 3000:3000 --name juice-shop bkimminich/juice-shop
```
- Port default: `3000`.

#### **2. Akses Juice Shop**
- Buka di browser:  
  ```
  http://localhost:3000
  ```
- Tidak perlu login untuk mulai eksploitasi.

#### **3. Update Juice Shop ke Versi Terbaru**
```bash
docker pull bkimminich/juice-shop
docker stop juice-shop && docker rm juice-shop
docker run -d -p 3000:3000 --name juice-shop bkimminich/juice-shop
```

---

### **⚙️ Perintah Troubleshooting**
| Masalah | Solusi |
|---------|--------|
| **Port sudah digunakan** | Ganti port (`-p 8081:80`) atau hentikan proses yang memakai port: <br> `sudo kill $(sudo lsof -t -i:3000)` |
| **Container crash** | Lihat log: <br> `docker logs juice-shop` |
| **Disk space penuh** | Bersihkan cache: <br> `docker system prune -a` |

---

### **🔧 Tips Lanjutan**
1. **Limit Resource** (RAM/CPU):  
   ```bash
   docker run -d -p 8080:80 --memory="512m" --cpus="1" --name dvwa vulnerables/web-dvwa
   ```

2. **Backup Data Container**:  
   ```bash
   docker cp dvwa:/var/www/html /backup/dvwa-html
   ```

3. **Jalankan Command di Dalam Container**:  
   ```bash
   docker exec -it dvwa bash
   ```

---

### **📂 Struktur File Penting**
| Container | Path | Keterangan |
|-----------|------|------------|
| **DVWA** | `/var/www/html` | File source code dan config |
| **Juice Shop** | `/juice-shop` | File aplikasi |

---

### **🎯 Contoh Workflow Pentesting**
1. Start DVWA:  
   ```bash
   docker run -d -p 8080:80 --name dvwa vulnerables/web-dvwa
   ```
2. Eksploitasi SQLi/XSS di DVWA.  
3. Hentikan container setelah selesai:  
   ```bash
   docker stop dvwa
   ```

---

Dengan catatan ini, Anda bisa dengan mudah **mengontrol DVWA dan Juice Shop** via Docker. Simpan sebagai referensi cepat! 🚀  

**Tips**: Buat alias di `~/.bashrc` untuk perintah yang sering dipakai:  
```bash
alias dvwa-start='docker run -d -p 8080:80 --name dvwa vulnerables/web-dvwa'
alias dvwa-stop='docker stop dvwa && docker rm dvwa'
```
