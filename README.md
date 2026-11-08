# Backend Setup Service (PHP & MySQL Docker)

Repository ini berisi konfigurasi lingkungan backend berbasis **PHP** dan **Database MySQL** menggunakan **Docker Compose** secara lokal.

---

## Deskripsi Singkat

Proyek ini dirancang agar lingkungan pengembangan (*development environment*) dapat dijalankan secara konsisten tanpa perlu melakukan instalasi web server (Apache/Nginx), PHP, atau MySQL secara manual di sistem lokal.

---

## Prasyarat Sistem

Sebelum menjalankan layanan, pastikan sistem kamu telah terinstall:
- **Docker Engine** & **Docker Compose**
- **Git**

---

## Panduan Memulai (Quick Start)

### 1. Duplikasi Konfigurasi Environment
Salin file  menjadi  untuk menentukan variabel kredensial database:
```bash
cp .env.example .env
```

### 2. Jalankan Container Docker
Nyalakan seluruh layanan (PHP & MySQL) di latar belakang (*detached mode*):
```bash
docker compose up -d
```

### 3. Eksekusi Database Seeding
Jalankan skrip *seeder* untuk menggenerasi tabel dan data awal ke dalam MySQL:
```bash
docker compose exec php php /var/www/html/seed.php
```

---

## Pengelolaan Service

- **Melihat Status Log Container:**
  ```bash
  docker compose logs -f
  ```
- **Menghentikan Seluruh Service:**
  ```bash
  docker compose down
  ```

---

## Arsitektur Layanan

| Service | Container Name | Deskripsi |
| :--- | :--- | :--- |
| **PHP** | `php` | Memproses skrip logika backend & koneksi DB |
| **MySQL** | `db` | Menyimpan data utama aplikasi |
