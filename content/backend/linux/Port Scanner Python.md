---
tags: [hacking, tools]
title: Port Scanner Python
created: '2025-04-06T13:56:08.023Z'
modified: '2025-04-21T10:09:51.145Z'
---

# Port Scanner Python

Berikut adalah program **Port Scanner** yang mencakup fitur:
- **Multi-threading** untuk mempercepat scanning
- **Deteksi service** (HTTP, SSH, FTP, dll)
- **Timeout** untuk menghindari hanging
- **Output yang informatif**

## **📌 Kode Lengkap**
```python
import socket
import threading
from queue import Queue
import time

# Konfigurasi
TARGET = "127.0.0.1"  # Ganti dengan target IP
PORT_RANGE = (1, 1024)  # Range port yang akan di-scan
THREADS = 100  # Jumlah thread untuk multi-threading
TIMEOUT = 1  # Timeout koneksi (detik)

# Daftar port dan service umum (bisa ditambah)
SERVICES = {
    21: "FTP",
    22: "SSH",
    80: "HTTP",
    443: "HTTPS",
    3306: "MySQL",
    8080: "HTTP-Alt",
}

# Queue untuk manajemen thread
queue = Queue()
open_ports = []

def scan_port(port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(TIMEOUT)
        result = sock.connect_ex((TARGET, port))
        if result == 0:
            service = SERVICES.get(port, "Unknown")
            print(f"[+] Port {port} ({service}) terbuka")
            open_ports.append(port)
        sock.close()
    except Exception as e:
        pass

def worker():
    while not queue.empty():
        port = queue.get()
        scan_port(port)

def run_scanner():
    print(f"\n🔍 Memulai scan pada {TARGET} (Port {PORT_RANGE[0]}-{PORT_RANGE[1]})")
    start_time = time.time()

    # Masukkan port ke queue
    for port in range(PORT_RANGE[0], PORT_RANGE[1] + 1):
        queue.put(port)

    # Buat thread
    threads = []
    for _ in range(THREADS):
        thread = threading.Thread(target=worker)
        threads.append(thread)
        thread.start()

    # Tunggu semua thread selesai
    for thread in threads:
        thread.join()

    # Hasil akhir
    print("\n📊 Hasil Scanning:")
    if open_ports:
        for port in sorted(open_ports):
            service = SERVICES.get(port, "Unknown")
            print(f"  - Port {port}: {service}")
    else:
        print("❌ Tidak ada port terbuka yang ditemukan.")

    elapsed_time = time.time() - start_time
    print(f"\n⏱ Waktu eksekusi: {elapsed_time:.2f} detik")

if __name__ == "__main__":
    run_scanner()
```

---

## **📌 Penjelasan Kode**
### **1. Fungsi Utama**
- **`scan_port(port)`**  
  - Mencoba koneksi ke port tertentu menggunakan `socket`.  
  - Jika koneksi berhasil (`result == 0`), port dianggap terbuka.  
  - Mendeteksi service berdasarkan daftar `SERVICES`.  

- **`worker()`**  
  - Mengambil port dari `queue` dan memanggil `scan_port()`.  

- **`run_scanner()`**  
  - Mengatur threading dan menjalankan scan.  
  - Menghitung waktu eksekusi.  

---

### **2. Multi-threading**
- **`Queue()`** digunakan untuk membagi tugas ke beberapa thread.  
- **100 thread** dipakai untuk mempercepat scanning (bisa diubah).  

---

### **3. Deteksi Service**
```python
SERVICES = {
    21: "FTP",
    22: "SSH",
    80: "HTTP",
    443: "HTTPS",
    # Tambahkan port lain sesuai kebutuhan
}
```
Program memeriksa apakah port yang terbuka termasuk dalam daftar service umum.

---

### **4. Cara Menjalankan**
1. Simpan kode sebagai `port_scanner.py`.
2. Jalankan di terminal:
   ```bash
   python port_scanner.py
   ```
3. Ubah `TARGET` dan `PORT_RANGE` sesuai kebutuhan.

---

## **🚀 Contoh Output**
```
🔍 Memulai scan pada 127.0.0.1 (Port 1-1024)

[+] Port 22 (SSH) terbuka
[+] Port 80 (HTTP) terbuka
[+] Port 443 (HTTPS) terbuka

📊 Hasil Scanning:
  - Port 22: SSH
  - Port 80: HTTP
  - Port 443: HTTPS

⏱ Waktu eksekusi: 3.14 detik
```

---

## **💡 Optimasi & Tambahan**
### **1. Scan Lebih Cepat**
- Kurangi `TIMEOUT` (tapi risiko false-negative).  
- Tambah jumlah `THREADS` (jangan terlalu banyak, bisa kena blokir).  

### **2. Fitur Tambahan**
- **Scan IP range** (misal `192.168.1.1-192.168.1.100`).  
- **Simpan hasil ke file**:
  ```python
  with open("hasil_scan.txt", "w") as f:
      for port in open_ports:
          f.write(f"Port {port} terbuka\n")
  ```

### **3. Error Handling**
- Handle `KeyboardInterrupt` untuk stop manual:
  ```python
  try:
      run_scanner()
  except KeyboardInterrupt:
      print("\n❌ Scan dihentikan pengguna.")
  ```

---

## **📚 Referensi**
- [Python `socket` Docs](https://docs.python.org/3/library/socket.html)  
- [Threading in Python](https://realpython.com/intro-to-python-threading/)  

Program ini cocok untuk **pemula** yang ingin belajar networking dan multi-threading. Selamat mencoba! 🚀
