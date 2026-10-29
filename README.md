[README.md](https://github.com/user-attachments/files/34125162/README.md)
# Titik Temu Kopi — POS Web

Aplikasi latihan Fullstack Web App. Teknologi: PHP Native (PDO), MySQL, HTML, CSS, JavaScript.

## Fitur
- Login berbasis sesi dan role `admin` / `kasir`, password hash, CSRF token.
- Dashboard: omzet hari ini, pesanan selesai, menu terlaris, stok rendah, grafik 7 hari, transaksi terbaru.
- Transaksi Dine-In/Takeaway, banyak item, catatan khusus, diskon, pajak restoran 10%, tunai/QRIS/transfer/debit, kembalian, invoice unik, cetak struk.
- Stok diperiksa dan dikurangi dalam transaksi database; kegagalan akan rollback.
- Laporan berdasarkan rentang tanggal, kategori, metode pembayaran, ringkasan dan ekspor CSV.
- Admin dapat menambah/edit/hapus menu serta mengelola harga dan stok.


## Cara menjalankan dengan XAMPP
1. Ekstrak folder `pos_titik_temu` ke `C:\xampp\htdocs\pos_titik_temu`.
2. Jalankan Apache dan MySQL melalui XAMPP Control Panel.
3. Buka `http://localhost/phpmyadmin`.
4. Pilih tab **Import**, pilih file `database.sql` dari folder proyek, lalu tekan **Import/Go**. File ini membuat database `pos_titik_temu` dan data demo.
5. Jika username/password MySQL berbeda dari default XAMPP, sesuaikan di `config.php`. Default XAMPP umumnya `root` dengan password kosong.
6. Buka `http://localhost/pos_titik_temu/login.php`.

## Akun demo
- Administrator: `admin` / `admin`
- Kasir: `kasir` / `kasir`

Akun demo dibuat untuk pengujian lokal. Password disimpan dalam bentuk hash menggunakan `password_hash()`, bukan teks biasa. Jangan gunakan password demo ini jika aplikasi dipasang di internet.

## Uji cepat
1. Login sebagai `admin`, buka **Menu & Stok**, tambah/edit menu.
2. Buka **Transaksi Baru**, pilih Dine-In dan isi meja, tambah dua item, masukkan diskon.
3. Coba metode Tunai dengan nominal kurang dari tagihan; sistem harus menolak.
4. Simpan transaksi dengan pembayaran cukup; struk akan terbuka dan dapat dicetak.
5. Buka Dashboard dan Laporan untuk memeriksa data.
6. Login sebagai `kasir`; halaman Menu & Stok tidak boleh bisa dibuka.
7. Ekspor laporan melalui tombol **Ekspor CSV**.

## Catatan pengembangan
- Aplikasi ini merupakan starter project untuk tes, bukan sistem produksi yang sudah diaudit.
- Password demo perlu diganti. Untuk produksi, tambahkan pengelolaan akun admin, rate limiting login, logging audit, dan kebijakan backup.
- Ekspor PDF belum disertakan; ekspor CSV tersedia dan dapat dibuka di Excel. Untuk PDF, tambahkan library seperti Dompdf.
- `harga_pokok` tersedia untuk pengembangan laporan laba; laporan saat ini merangkum omzet, diskon, pajak dan rata-rata transaksi, bukan laporan laba rugi lengkap.
- Data stok pada starter ini merupakan stok menu yang berkurang saat terjual. Manajemen resep bahan baku (misalnya gram biji kopi/ml sirup per menu) 
