# InvoCanteen

InvoCanteen adalah platform manajemen kantin yang menggabungkan backend berbasis Express/Prisma dengan frontend Next.js modern untuk mengelola produk, keranjang, pesanan, invoice, serta statistik penjualan dalam satu dashboard.

## Deskripsi Singkat
- Memudahkan kasir dan admin kantin dalam mengelola menu, transaksi, dan pencetakan invoice.
- Mendukung upload gambar produk lewat Supabase Storage serta pencatatan data pada PostgreSQL melalui Prisma ORM.
- Menyediakan antarmuka web responsif dengan dashboard statistik, manajemen keranjang, dan fitur invoice siap cetak.

## Stack Teknologi
- **Backend:** Node.js, Express, TypeScript, Prisma, PostgreSQL, Supabase Storage, JSON Web Token, Multer.
- **Frontend:** Next.js 15 (App Router), React 19, Tailwind CSS 4, Radix UI, Chart.js, Axios, Sonner.
- **Dev & Tools:** Turbopack dev server, ESLint, Prisma Migrate, ts-node-dev.

## Fitur Utama
- **Autentikasi & Otorisasi** kasir/admin (register, login, logout, pembaruan profil & password) dengan proteksi JWT dan cookie.
- **Manajemen Produk** lengkap (CRUD, kategori, upload foto) terintegrasi Supabase.
- **Keranjang & Checkout** untuk membuat pesanan, menambahkan item, dan menghitung subtotal/pajak/total secara otomatis.
- **Order & Invoice** termasuk daftar invoice, status pembayaran, detail pesanan, serta halaman cetak siap print.
- **Dashboard Statistik** visualisasi penjualan harian/bulanan/tahunan memakai Chart.js.
- **Integrasi API** modular dengan validasi request, middleware error handling, dan struktur usecase terpisah.

## Cara Menjalankan

### 1. Persiapan Umum
- Pastikan Node.js >= 18 dan PostgreSQL tersedia.
- Siapkan akun Supabase (untuk storage file) bila ingin mengunggah gambar produk.

### 2. Menjalankan Backend (`invocanteen-api`)
```bash
cd invocanteen-api
npm install
```
1. Buat berkas `.env` berdasarkan variabel berikut:
   ```bash
   DATABASE_URL="postgresql://username:password@localhost:5432/invocanteen"
   FRONTEND_URL="http://localhost:3000"
   SUPABASE_URL="https://your-project.supabase.co"
   SUPABASE_ANON_KEY="your-anon-key"
   SUPABASE_SERVICE_ROLE_KEY="your-service-role-key"
   JWT_SECRET="ganti-dengan-rahasia"
   PORT=4500
   ```
2. Jalankan migrasi & generate Prisma:
   ```bash
   npx prisma generate
   npx prisma migrate dev
   ```
3. Start server pengembangan:
   ```bash
   npm run dev
   ```
   API akan tersedia di `http://localhost:4500`.

### 3. Menjalankan Frontend (`invocanteen-ui/invocanteen`)
```bash
cd invocanteen-ui/invocanteen
npm install
```
1. Buat `.env.local` dengan konfigurasi API:
   ```bash
   NEXT_PUBLIC_BACKEND_API="http://localhost:4500"
   ```
2. Jalankan aplikasi:
   ```bash
   npm run dev
   ```
   Antarmuka akan dapat diakses pada `http://localhost:3000`.

> **Catatan:** Pastikan backend berjalan terlebih dahulu agar frontend dapat memuat data produk, keranjang, dan invoice.

## Screenshot UI
![Cuplikan Landing Page](invocanteen-ui/invocanteen/public/hero-illustration.jpg)

## Link Demo
- [Demo Aplikasi (perbarui dengan URL deployment kamu)](https://invocanteen-demo.vercel.app)
