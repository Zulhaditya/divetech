# 1. Project Overview

- **Nama Client:** Affioca
- **Nama Project:** Engineering Portfolio Website
- **Tipe Project:** Website Development
- **Deadline:** Sebulan

# 2. Requirements Gathering

- **Tipe Website:** Career Portfolio Website
- **Teknologi yang digunakan** React or Next.js
- **Jumlah Halaman:** At least 3 pages
- **Konten:** Projects page, Resume page, Admin page
- **Database:** MySQL Database for project data
- **Fitur di halaman project:**
  - Menampilkan project menggunakan database MySQL
  - Dapat upload 4 tags, 4 gambar, dan 1 video, serta deskripsi
- **Fitur di halaman resume:**
  - Terdapat bagian skill dan experience
  - Optional: Filter berdasarkan work experience
- **Fitur di halaman admin:**
  - Dapat menambahkan/edit project
  - Dapat update resume
- **UI/UX Design:** Design professional dan clean tanpa ada profile picture.

# 3. Development Phases

## Phase 1 - Figma Design

### Home Page

- [x] Buat halaman home
- [x] Animasi
- [x] Navigasi ke seluruh menu

### Project Page

- [x] Membuat list project
- [x] Membuat tech stack yang digunakan
- [ ] Animasi
- [ ] Navigate ke seluruh menu

**Referensi:**

- https://www.moritzpetersen.com/#work
- https://thatcoffeeeguy.com/#/ (Tech stack and project)
- https://www.adhamdannaway.com/portfolio (Portfolio)

### Resume Page

- [x] Membuat halaman resume
- [ ] Fitur dark mode
- [ ] Navigasi ke seluruh menu

**Referensi:**

- https://saurabhgupta.netlify.app
- https://resume.hshekhar.com (resume template)

### Admin Page

#### Form untuk tambah dan update projects:

- Title
- Category
- Description
- 1 Video
- 4 Images
- 4 Tags

#### Form untuk update resume:

1. Biodata

- Name
- Location
- Email
- Link Website

2. Social

- Linkedin
- Twitter
- Github

3. Education

- Gelar
- Study
- Location Education
- Years

4. Skills

- Icon
- Title

5. Experience

- Title
- Years
- Company
- Technology

7. Certificates

- Title
- Years
- Credential ID

8. Languages

9. Interest

- Icon
- Title

## Phase 2 - Frontend Development

- Buat React atau Next.js template untuk seluruh halaman
- Implementasi responsive design untuk berbagai layar
- Design menu navigasi

## Phase 3 - Backend Development

- Setup MySQL database untuk menyimpan data project
- Membuat API untuk mengolah data
- Implementasi autentikasi user di admin page (opsi)

## Phase 4 - Dynamic Pages

### Projects Page

- Menerima dan menampilkan project dari database
- Implementasi fitur upload untuk tags, gambar, video, dan deskripsi

### Resume Page

- Create dynamic sections for skills and work experience
- Membuat dynamic section untuk menampilkan skill dan work experience

### Phase 5 - Admin Page

- Build the admin panel for adding/editing projects
- Implement resume section editing functionality

### Phase 6 - Testing

- Testing keseluruhan fitur pada website
- Memperbaiki bugs dan issue
- Optimasi performance

### Phase 7 - Deployment

- Deploy website ke server hosting
- Setup konfigurasi pada server
- Memastikan website sudah live dan dapat diakses

# 4. Documentation

- Membuat dokumentasi terkait website dan struktur database untuk kebutuhan update dan maintenance.

# 5. Delivered

- Mengirimkan project ke client.
