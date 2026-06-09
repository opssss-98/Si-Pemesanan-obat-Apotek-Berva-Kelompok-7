# Dokumentasi Skenario Pengujian (Test Case) - Kelompok 7
**Proyek:** Sistem Informasi Pemesanan Obat Berbasis Website pada Apotek Berva
**Kelas:** 4/G Sistem Informasi

---

## 1. POSITIVE CASE (Jalur Sukses)
*Skenario di mana pengguna memasukkan data yang valid dan sistem berjalan sesuai ekspektasi.*

### [TC-POS-01] Fitur Registrasi Akun Pelanggan Baru
* **Objektif:** Memastikan pengguna dapat membuat akun baru dengan data yang valid.
* **Langkah Pengujian:**
    1. Buka halaman registrasi website Apotek Berva.
    2. Masukkan Nama Lengkap, Email aktif, Nomor WhatsApp, dan Password yang kuat.
    3. Klik tombol "Daftar".
* **Hasil yang Diharapkan:** Sistem berhasil menyimpan data, memunculkan notifikasi "Registrasi Berhasil", dan mengarahkan pengguna otomatis ke halaman login atau beranda.

### [TC-POS-02] Fitur Unggah Resep Dokter
* **Objektif:** Memastikan pelanggan berhasil mengunggah foto resep dokter untuk pemesanan obat khusus.
* **Langkah Pengujian:**
    1. Masuk ke menu "Unggah Resep".
    2. Klik tombol "Pilih File" dan pilih gambar resep berformat `.jpg` atau `.png` dengan ukuran 2 MB.
    3. Klik tombol "Kirim Resep".
* **Hasil yang Diharapkan:** File berhasil terunggah, muncul pesan "Resep Berhasil Dikirim, Harap Tunggu Konfirmasi Apoteker", dan status pesanan berubah menjadi "Menunggu Verifikasi".

---

## 2. NEGATIVE CASE (Penanganan Error)
*Skenario di mana pengguna memasukkan data yang salah/tidak valid dan sistem mampu menangani error tersebut dengan memberikan peringatan yang jelas.*

### [TC-NEG-01] Validasi Format Email pada Form Login
* **Objektif:** Memastikan sistem menolak proses login jika format email tidak sesuai standar.
* **Langkah Pengujian:**
    1. Buka halaman Login.
    2. Masukkan email tanpa tanda `@` (contoh: `sittirahmadhanigmail.com`).
    3. Masukkan password yang benar, lalu klik "Login".
* **Hasil yang Diharapkan:** Sistem menolak proses login dan menampilkan pesan error tepat di bawah kolom email: *"Format email tidak valid, pastikan menggunakan tanda '@'"*.

### [TC-NEG-02] Unggah File Resep dengan Format Terlarang
* **Objektif:** Memastikan sistem menolak file resep dokter yang bukan berformat gambar.
* **Langkah Pengujian:**
    1. Masuk ke menu "Unggah Resep".
    2. Pilih file dokumen berformat `.pdf` atau `.docx`.
    3. Klik tombol "Kirim Resep".
* **Hasil yang Diharapkan:** Sistem memblokir proses unggah dan memunculkan notifikasi error merah: *"Gagal mengunggah. Format file tidak didukung! Hanya diperbolehkan file gambar (.jpg, .jpeg, .png)"*.

---

## 3. EDGE CASE (Kondisi Ekstrem)
*Skenario pengujian pada batas kondisi ekstrem atau tidak biasa yang jarang terjadi, untuk memastikan sistem tidak crash.*

### [TC-EDG-01] Unggah File Gambar Resep dengan Ukuran Sangat Besar
* **Objektif:** Memastikan sistem tidak mengalami *crash/server timeout* jika pengguna mengunggah gambar beresolusi sangat tinggi.
* **Langkah Pengujian:**
    1. Masuk ke menu "Unggah Resep".
    2. Pilih file gambar berukuran 25 MB (melebihi batas maksimal standar yang biasanya hanya 5 MB).
    3. Klik tombol "Kirim Resep".
* **Hasil yang Diharapkan:** Sistem tidak mengalami *loading* tanpa akhir (*hang*), melainkan langsung memberikan respons penolakan secara cepat: *"Ukuran file terlalu besar! Maksimal ukuran file adalah 5 MB"*.

### [TC-EDG-02] Input Kuantitas Obat dengan Angka Minus atau Nol
* **Objektif:** Memastikan sistem keranjang belanja tidak menerima jumlah pemesanan obat yang tidak masuk akal.
* **Langkah Pengujian:**
    1. Buka katalog obat digital Apotek Berva, pilih salah satu obat (misal: Paracetamol).
    2. Pada kolom jumlah (kuantitas), ketik secara manual angka `-5` atau `0`.
    3. Klik tombol "Tambah ke Keranjang".
* **Hasil yang Diharapkan:** Sistem secara otomatis mengubah angka tersebut kembali menjadi `1` atau menampilkan peringatan: *"Jumlah pembelian minimal adalah 1 botol/strip"*.
