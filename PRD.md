# PRD: Toko Buku Novel

## 1. Ringkasan Produk
Aplikasi manajemen toko buku novel skala kecil yang dirancang khusus untuk pengguna dengan koneksi internet rendah dan perangkat HP mid-low end. Aplikasi ini beroperasi secara offline-first dengan kemampuan menyimpan data secara lokal.

## 2. Tujuan & Sasaran
- Membantu pemilik toko buku novel mencatat transaksi dengan mudah
- Mengurangi ketergantungan pada koneksi internet
- Antarmuka mobile-friendly untuk HP dengan spesifikasi rendah
- Fitur utama: pencatatan pemasukan, pengeluaran, dan kasbon

## 3. Target Pengguna
- Pemilik toko buku novel skala kecil
- Pengguna HP Android/iOS dengan spek mid-low (RAM 2-4GB)
- Lokasi dengan koneksi internet terbatas/batas kuota
- Usia 25-55 tahun, teknikal dasar

## 4. Personas Pengguna

### Persona 1: Pak Budi
- Pemilik toko buku di desa
- Pakai HP Android murah (RAM 2GB)
- Koneksi internet cuma pakai kuota kecil
- Butuh catat transaksi sederhana tanpa ribet

### Persona 2: Bu Siti
- Karyawan toko buku
- Sering input data buku baru
- Perlu lihat stok dan harga cepat
- Sering cek kasbon pelanggan

## 5. Kebutuhan Fungsional

### 5.1 Autentikasi
- Sistem login sederhana (opsional, bisa di-skip)
- Data disimpan lokal per browser/device

### 5.2 Dashboard
- Ringkasan pemasukan/pengeluaran hari ini
- Total kasbon aktif
- Tombol aksi cepat (+ pemasukan, + pengeluaran)

### 5.3 Modul Buku
- CRUD data buku (judul, penulis, harga beli/jual, stok)
- Pencarian by judul/penulis
- Informasi stok buku

### 5.4 Modul Transaksi
- Catat pemasukan (penjualan, lainnya)
- Catat pengeluaran (pembelian buku, operasional)
- Riwayat transaksi
- Opsi tambah buku saat input pengeluaran

### 5.5 Modul Kasbon
- Catat kasbon pelanggan (nama, jumlah)
- Status: aktif/lunas
- Pelunasan kasbon otomatis jadi pemasukan
- Daftar kasbon aktif

### 5.6 Modul Laporan
- Ringkasan harian
- Export data ke CSV
- Filter by tanggal

## 6. Kebutuhan Non-Fungsional

### 6.1 Kinerja
- Loading < 3 detik di HP mid-low
- Ukuran file < 200KB (tanpa library eksternal)
- IndexedDB untuk penyimpanan lokal

### 6.2 Kompatibilitas
- Browser: Chrome 60+, Firefox 55+, Safari 12+
- Responsif di semua ukuran layar
- PWA - bisa diinstall di HP

### 6.3 Keamanan
- Data tidak dikirim ke server (lokal)
- Tidak ada kredential sensitif
- Validasi input dasar

## 7. User Interface

### 7.1 Desain Mobile-First
- Bottom navigation bar
- Tombol besar untuk input mudah
- Warna kontras untuk k readability
- Font minimal 14px

### 7.2 Layout Halaman
1. **Dashboard**: Summary hari ini + kasbon aktif
2. **Buku**: Daftar buku + pencarian + tambah
3. **Transaksi**: Pilihan pemasukan/pengeluaran + riwayat
4. **Kasbon**: Daftar kasbon + tambah + bayar
5. **Laporan**: Filter tanggal + ringkasan keuangan

## 8. Arsitektur Teknis

### 8.1 Teknologi
- HTML5 + CSS3 + vanilla JavaScript
- IndexedDB untuk penyimpanan
- Service Worker untuk offline
- PWA manifest

### 8.2 Struktur File
```
/index.html          - Entry point
/css/style.css       - Styling
/js/app.js           - Router & utilities
/js/db.js            - IndexedDB layer
/js/pages/*.js       - Halaman-halaman
/sw.js              - Service worker
/manifest.json       - PWA config
```

### 8.3 Data Model
- `buku`: id, judul, penulis, harga_beli, harga_jual, stok
- `transaksi`: id, tipe, jumlah, keterangan, tanggal
- `kasbon`: id, nama_pelanggan, jumlah, status, tanggal

## 9. Rencana Implementasi

### Fase 1: Setup Dasar
- [x] Struktur folder
- [x] Service worker & manifest
- [x] IndexedDB setup

### Fase 2: UI Core
- [x] Styling mobile-first
- [x] Bottom navigation
- [x] Sistem routing

### Fase 3: Modul
- [x] Dashboard
- [x] Buku
- [x] Transaksi
- [x] Kasbon
- [x] Laporan

### Fase 4: Fitur Pendukung
- [ ] Export CSV
- [ ] Validasi form
- [ ] Loading states

## 10. Success Metrics
- Aplikasi bisa dijalankan di HP tanpa internet
- Input transaksi < 5 detik
- Pengguna bisa export data untuk backup
- UI responsif di layar kecil

## 11. Constraints
- Tidak boleh pakai library bundel (React/Vue)
- Ukuran total < 500KB
- Harus work di iOS Safari