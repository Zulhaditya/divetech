---
tags: [hacking]
title: Tools dan Resource Hacking
created: '2025-04-07T05:09:56.097Z'
modified: '2025-04-21T10:08:01.035Z'
---

# Tools dan Resource Hacking
### **1. Local Vulnerable Web Apps (Install di PC/Lab)**
#### 🛠️ **A. Docker-Based (Paling Direkomendasikan)**
| Nama | Deskripsi | Link |
|------|-----------|------|
| **DVWA** (Damn Vulnerable Web App) | Web app dengan kerentanan tingkat dasar sampai lanjut (SQLi, XSS, RCE, dll) | [github.com/digininja/DVWA](https://github.com/digininja/DVWA) |
| **OWASP Juice Shop** | Aplikasi e-commerce vulnerable (modern JavaScript, API, dan IoT) | [github.com/juice-shop/juice-shop](https://github.com/juice-shop/juice-shop) |
| **WebGoat** | Aplikasi Java untuk belajar OWASP Top 10 | [github.com/WebGoat/WebGoat](https://github.com/WebGoat/WebGoat) |
| **bWAPP** | 100+ vulnerability dalam satu app (PHP/MySQL) | [sourceforge.net/projects/bwapp](https://sourceforge.net/projects/bwapp/) |

**Cara Install (Contoh DVWA)**:
```bash
git clone https://github.com/digininja/DVWA
cd DVWA
docker-compose up -d
```
Akses: `http://localhost:8080`  
Login: `admin`/`password`

---

#### 💻 **B. Virtual Machines (VM)**
| Nama | Deskripsi | Link |
|------|-----------|------|
| **Metasploitable** | OS Linux dengan service vulnerable (SSH, FTP, Web, dll) | [github.com/rapid7/metasploitable3](https://github.com/rapid7/metasploitable3) |
| **OWASP Broken Web Apps** | Kumpulan 10+ web app vulnerable dalam satu VM | [sourceforge.net/projects/owaspbwa](https://sourceforge.net/projects/owaspbwa/) |
| **Damn Vulnerable Linux (DVL)** | Distro Linux khusus untuk latihan exploitasi | [www.vulnhub.com/entry/damn-vulnerable-linux-1.1,71/](https://www.vulnhub.com/entry/damn-vulnerable-linux-1.1,71/) |

**Cara Pakai**:
- Download VM → Import ke VirtualBox/VMware → Boot dan eksploitasi.

---

### **2. Online Labs (Tanpa Install)**
#### 🌐 **A. Platform Interaktif**
| Nama | Deskripsi | Link |
|------|-----------|------|
| **Hack The Box** | Lab realistik dengan mesin vulnerable (free & premium) | [hackthebox.com](https://www.hackthebox.com/) |
| **TryHackMe** | Pembelajaran berbasis jalur (path) + lab terpandu | [tryhackme.com](https://tryhackme.com/) |
| **PentesterLab** | Latihan khusus web vulnerability | [pentesterlab.com](https://pentesterlab.com/) |
| **OverTheWire** | Game hacking berbasis level (SSH) | [overthewire.org](https://overthewire.org/) |

**Contoh Challenge**:
- TryHackMe: **"OWASP Juice Shop"** room  
- HackTheBox: Mesin **"Broken"** (easy level)

---

#### 🎮 **B. Gamified Challenges**
| Nama | Deskripsi | Link |
|------|-----------|------|
| **Google Gruyere** | Lab XSS, CSRF, dan Path Traversal | [google-gruyere.appspot.com](https://google-gruyere.appspot.com/) |
| **HackThisSite** | Challenge klasik (basic hingga advanced) | [hackthissite.org](https://www.hackthissite.org/) |
| **RingZer0** | CTF dengan berbagai kategori | [ringzer0team.com](https://ringzer0team.com/) |

---

### **3. Mobile Vulnerable Apps**
| Nama | Deskripsi | Link |
|------|-----------|------|
| **Damn Vulnerable Hybrid App (DVHA)** | Aplikasi mobile (Android/iOS) dengan kerentanan web + API | [github.com/logicalhacking/DVHAP](https://github.com/logicalhacking/DVHAP) |
| **InsecureBankv2** | Aplikasi banking vulnerable untuk Android | [github.com/dineshshetty/Android-InsecureBankv2](https://github.com/dineshshetty/Android-InsecureBankv2) |

**Cara Install**:
```bash
git clone https://github.com/dineshshetty/Android-InsecureBankv2
cd Android-InsecureBankv2
adb install InsecureBankv2.apk
```

---

### **🔧 Tools Pendukung Pentesting**
1. **Burp Suite Community** (Analisis traffic HTTP): [portswigger.net](https://portswigger.net/burp/communitydownload)  
2. **OWASP ZAP** (Alternatif Burp Suite): [owasp.org/zap](https://www.zaproxy.org/)  
3. **sqlmap** (Automated SQLi): [sqlmap.org](https://sqlmap.org/)  

---

### **📌 Rekomendasi untuk Pemula**
1. Mulai dengan **DVWA** atau **OWASP Juice Shop** (local install).  
2. Lanjut ke **TryHackMe** (online) untuk latihan terstruktur.  
3. Gabung komunitas seperti **Hack The Box** untuk tantangan realistik.  

---

### **⚠️ Catatan Penting**
- **Gunakan hanya di lingkungan legal** (milik sendiri/lab resmi).  
- **Jangan eksploitasi sistem tanpa izin** (bisa kena UU ITE).  

Dengan tools ini, Anda bisa belajar hacking **tanpa merugikan siapapun**! 🚀
