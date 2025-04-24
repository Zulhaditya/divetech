---
tags: [hacking, tools]
title: Host Scanner Python
created: '2025-04-06T15:31:22.255Z'
modified: '2025-04-21T10:11:33.971Z'
---

# Host Scanner Python
### 📌 **Kode Python untuk Scan Host Aktif**
```python
import os
import socket
import struct
import threading
from scapy.all import *
from concurrent.futures import ThreadPoolExecutor

# Konfigurasi jaringan
NETWORK = "192.168.1.0/24"
TIMEOUT = 1  # Timeout dalam detik
THREADS = 50  # Jumlah thread untuk parallel scanning

def ping_host(ip):
    """Deteksi host dengan ICMP Ping (Linux/Windows compatible)."""
    try:
        # Gunakan sistem operasi's ping command
        response = os.system(f"ping -c 1 -W {TIMEOUT} {ip} > /dev/null 2>&1")
        if response == 0:
            return ip
    except:
        pass
    return None

def arp_scan(ip):
    """Deteksi host dengan ARP Request (lebih cepat di LAN)."""
    try:
        # Buat ARP packet
        arp_pkt = ARP(pdst=ip)
        # Broadcast the packet
        resp = srp1(arp_pkt, timeout=TIMEOUT, verbose=0)
        if resp:
            return resp.psrc  # Return IP yang merespon
    except:
        pass
    return None

def scan_network():
    """Scan seluruh host di jaringan."""
    active_hosts = set()
    
    # Generate semua IP di subnet 192.168.1.0/24
    ip_list = [f"192.168.1.{i}" for i in range(1, 255)]
    
    # Gunakan ThreadPool untuk parallel scan
    with ThreadPoolExecutor(max_workers=THREADS) as executor:
        # Pilih metode: ping_host atau arp_scan
        results = executor.map(arp_scan, ip_list)
        
        for ip in results:
            if ip:
                active_hosts.add(ip)
    
    return sorted(active_hosts)

if __name__ == "__main__":
    print("🔍 Memulai scan jaringan 192.168.1.0/24...")
    active_hosts = scan_network()
    
    print("\n🎯 Host Aktif:")
    for i, ip in enumerate(active_hosts, 1):
        try:
            hostname = socket.gethostbyaddr(ip)[0]
        except:
            hostname = "Unknown"
        print(f"{i}. {ip} ({hostname})")
```

---

### 🔧 **Cara Menggunakan**
1. **Install Scapy** (untuk ARP scan):
   ```bash
   pip install scapy
   ```
   Jika error, jalankan dengan root:
   ```bash
   sudo pip install scapy
   ```

2. **Jalankan script**:
   ```bash
   sudo python3 scanner.py
   ```
   (Perlu `sudo` karena ARP scan butuh akses raw socket).

---

### 📊 **Contoh Output**
```
🔍 Memulai scan jaringan 192.168.1.0/24...

🎯 Host Aktif:
1. 192.168.1.1 (router.home)
2. 192.168.1.102 (android-device)
3. 192.168.1.105 (laptop-user)
```

---

### 🚀 **Penjelasan Fitur**
1. **Dua Metode Scanning**:
   - **ICMP Ping**: Cross-platform, tapi bisa di-block firewall.
   - **ARP Request**: Lebih cepat dan akurat di jaringan lokal (LAN).

2. **Multithreading**:
   - Menggunakan `ThreadPoolExecutor` untuk mempercepat scan.

3. **Resolusi Hostname**:
   - Mendapatkan nama device (jika tersedia).

4. **Kompatibilitas**:
   - Bisa di Linux, Windows, atau Termux (Android).

---

### 💡 **Optimasi & Troubleshooting**
- **Jika tidak ada host terdeteksi**:
  - Pastikan perangkat Anda terhubung ke jaringan `192.168.1.0/24`.
  - Coba ganti metode ke `ping_host` jika ARP tidak bekerja.
  - Matikan firewall sementara di target:
    ```bash
    sudo ufw disable  # Untuk Linux
    ```

- **Scan lebih cepat**:
  - Kurangi `TIMEOUT` (misal `0.5`).
  - Tingkatkan `THREADS` (misal `100`), tapi hati-hati overload.

- **Scan subnet berbeda**:
  - Ganti `NETWORK` di kode (misal `"10.0.0.0/24"`).

---

### 🛠️ **Alternatif tanpa Scapy**
Jika Scapy tidak bisa diinstall, gunakan **pure Python socket** (hanya ICMP):
```python
import socket

def ping_host(ip):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_ICMP)
        sock.settimeout(TIMEOUT)
        sock.sendto(b'\x08\x00\x00\x00', (ip, 1))  # ICMP Echo Request
        sock.recvfrom(1024)
        return ip
    except:
        return None
```
> ⚠️ Butuh **root/sudo** untuk akses raw socket.

---

### 📌 **Catatan Keamanan**
- **Hanya untuk jaringan Anda sendiri**! Scan tanpa izin ilegal di banyak negara.
- **Gunakan untuk**:
  - Audit keamanan LAN.
  - Monitoring perangkat IoT.
  - Belajar jaringan.

Dengan script ini, Anda bisa **melihat semua perangkat** yang terhubung ke WiFi Anda! 🕵️♂️
