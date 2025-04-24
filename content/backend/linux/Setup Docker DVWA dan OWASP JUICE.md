---
tags: [hacking]
title: Setup Docker DVWA dan OWASP JUICE
created: '2025-04-07T05:30:22.150Z'
modified: '2025-04-21T10:09:01.803Z'
---

# Setup Docker DVWA dan OWASP JUICE
### **🔥 Langkah 1: Install DVWA (Damn Vulnerable Web App)**
#### **1. Pull Image DVWA**
```bash
docker pull vulnerables/web-dvwa
```

#### **2. Jalankan Container**
```bash
docker run -d -p 8080:80 --name dvwa vulnerables/web-dvwa
```

#### **3. Akses DVWA**
Buka browser dan ketik:
```
http://localhost:8080
```
- **Login Default**:  
  Username: `admin`  
  Password: `password`

---

### **🍊 Langkah 3: Install OWASP Juice Shop**
#### **1. Pull Image Juice Shop**
```bash
docker pull bkimminich/juice-shop
```

#### **2. Jalankan Container**
```bash
docker run -d -p 3000:3000 --name juice-shop bkimminich/juice-shop
```

#### **3. Akses Juice Shop**
Buka browser dan ketik:
```
http://localhost:3000
```
- **No login required** (langsung bisa eksploitasi).

---

### **🛠️ Manajemen Container**
#### **Perintah Dasar Docker**
| Perintah | Deskripsi |
|----------|-----------|
| `docker ps` | Lihat container yang sedang berjalan |
| `docker stop dvwa` | Hentikan container DVWA |
| `docker start dvwa` | Jalankan kembali container |
| `docker rm dvwa` | Hapus container (harus di-stop dulu) |
| `docker system prune` | Bersihkan cache/residu |

---

### **💡 Tips Optimasi**
1. **Atur Limit RAM** (untuk laptop 8GB):
   ```bash
   docker run -d -p 8080:80 --memory="512m" --name dvwa vulnerables/web-dvwa
   ```
2. **Gunakan Docker Compose** untuk multi-container:
   ```bash
   sudo apt install docker-compose
   ```
3. **Monitor Resource**:
   ```bash
   docker stats
   ```

---

### **⚠️ Troubleshooting**
- **Error port sudah dipakai**?  
  Ganti port (misal: `-p 8081:80`).
- **Docker permission denied**?  
  Jalankan:
  ```bash
  sudo chmod 666 /var/run/docker.sock
  ```
- **DVWA tidak bisa konek database**?  
  Restart container:
  ```bash
  docker restart dvwa
  ```

---

### **🎯 Apa yang Bisa Dipelajari?**
| Aplikasi | Jenis Kerentanan |
|----------|------------------|
| **DVWA** | SQLi, XSS, CSRF, File Upload |
| **Juice Shop** | API Security, SSTI, RCE |

Dengan setup ini, Anda siap melakukan latihan hacking secara legal dan aman! 🚀
