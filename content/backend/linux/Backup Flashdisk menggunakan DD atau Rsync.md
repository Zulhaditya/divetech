---
title: Backup Flashdisk menggunakan DD atau Rsync
created: '2025-04-21T12:56:23.392Z'
modified: '2025-04-21T12:56:41.961Z'
---

# Backup Flashdisk menggunakan DD atau Rsync
### **Apakah Aman Menggunakan `dd`?**
`dd` adalah alat yang sangat **powerful**, tetapi juga **berisiko tinggi** jika digunakan sembarangan karena:
- **Overwrite langsung ke device** (`/dev/sdb`, dll.) tanpa konfirmasi.
- Salah memilih `of=` (target) bisa **menghapus disk sistem** (misal: `/dev/sda`) dan merusak OS.
- Tidak ada fitur "undo" — data yang tertimpa **hilang permanen**.

---

### **Alternatif yang Lebih Aman Selain `dd`**
#### **1. Backup Tanpa `.img` (Copy Manual File/Folder)**
Jika hanya ingin **backup data** (bukan backup sector-by-sector), gunakan `rsync` atau `cp`:
```bash
rsync -avh /media/user/flashdisk/ ~/backup_flashdisk/
```
atau
```bash
cp -r /media/user/flashdisk/* ~/backup_flashdisk/
```
**Keuntungan**:
- Hanya menyalin file, bukan seluruh disk.
- Lebih cepat untuk data kecil.
- Bisa memilih file tertentu.

**Kekurangan**:
- Tidak menyimpan **metadata filesystem**, partisi, atau file terhapus.
- Tidak berguna jika flashdisk **corrupt/unreadable**.

#### **2. Backup Partisi ke `.img` dengan `partclone` (Lebih Aman)**
Jika ingin backup **hanya partisi** (bukan seluruh disk), gunakan `partclone`:
```bash
sudo partclone.fat32 -c -s /dev/sdb1 -o ~/flashdisk_partition.img
```
- Ganti `fat32` dengan filesystem flashdisk (ext4, ntfs, dll.).
- Lebih aman karena hanya bekerja di **partisi tertentu** (`/dev/sdb1`).

#### **3. Gunakan GUI Tools (e.g., `gnome-disk-utility`)**
- Buka **Disks** (`gnome-disk-utility`) di Parrot OS.
- Pilih flashdisk → klik ikon gear → **Create Disk Image**.
- Untuk restore: Pilih **Restore Disk Image**.

**Keuntungan**:
- Antarmuka visual, lebih sulit salah pilih device.

---

### **Kapan Harus Pakai `dd`?**
Gunakan `dd` **hanya** jika:
1. Ingin backup **seluruh disk** (termasuk partisi, bootloader, dll.).
2. Flashdisk bermasalah (bad sector, corrupt) dan perlu clone 1:1.
3. Tidak ada alternatif lain.

---

### **Tips Penggunaan `dd` yang Aman**
1. **Selalu double-check** `if=` (source) dan `of=` (target):
   ```bash
   lsblk  # Pastikan /dev/sdb adalah flashdisk!
   ```
2. Gunakan `status=progress` untuk memantau proses:
   ```bash
   sudo dd if=/dev/sdb of=~/backup.img bs=4M status=progress
   ```
3. Untuk restore, pastikan kapasitas flashdisk **≥ ukuran `.img`**.

---

### **Alternatif Restore Tanpa `dd`**
Jika Anda hanya menyalin file manual (bukan `.img`), restore bisa dilakukan dengan:
```bash
rsync -avh ~/backup_flashdisk/ /media/user/flashdisk/
```
atau
```bash
cp -r ~/backup_flashdisk/* /media/user/flashdisk/
```

---

### **Kesimpulan**
| Metode          | Keamanan | Kelebihan                         | Kekurangan                |
|-----------------|----------|-----------------------------------|---------------------------|
| `dd`            | ⚠️ Risiko tinggi | Backup sector-level, lengkap      | Bisa merusak sistem       |
| `rsync`/`cp`    | ✅ Aman   | Cepat, hanya file penting         | Tidak backup struktur disk|
| `partclone`     | ✅ Aman   | Backup partisi saja               | Hanya untuk partisi       |
| GUI Tools       | ✅ Aman   | Mudah digunakan                  | Tidak fleksibel untuk kasus advanced |

**Rekomendasi**:
- Jika hanya butuh **file**, gunakan `rsync`/`cp`.
- Jika butuh **backup partisi**, gunakan `partclone`.
- Jika flashdisk **rusak/corrupt**, baru gunakan `dd`.
