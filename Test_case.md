# Dokumentasi Skenario Pengujian (Test Case) - Kelompok 7
**Proyek:** Sistem Informasi Pemesanan Obat Berbasis Website pada Apotek Berva  
**Kelas:** 4/G Sistem Informasi  
**Tim Pengembang:**
* **Manajer Proyek:** 701240208 - Muhammad Ilyas Kurniawan
* **System Analyst:** 701240187 - Galuh Ayuwandira
* **System Design:** 701240190 - Chintiya Dara
* **System Testing:** 701240192 - Sitti Rahmadhani

---

## 1. POSITIVE CASE (Jalur Sukses)

| Test Case ID | Test Item | Description | Pre-conditions | Input Data | Test Steps | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-POS-01** | Registrasi Akun | Menguji keberhasilan pendaftaran pelanggan baru dengan data valid. | Pengguna berada di halaman registrasi Apotek Berva. | - Nama: Sitti Rahmadhani<br>- Email: sitti@gmail.com<br>- No.WA: 0812345678<br>- Pass: Berva2026! | 1. Buka form registrasi.<br>2. Isi semua data valid.<br>3. Klik tombol "Daftar". | Sistem menyimpan data, menampilkan pesan "Registrasi Berhasil", dan mengalihkan ke halaman Login. | Berhasil menyimpan data dan beralih ke halaman Login. | Pass |
| **TC-POS-02** | Unggah Resep Dokter | Menguji pelanggan mengunggah foto resep dokter format gambar. | Pelanggan sudah login dan berada di halaman "Unggah Resep". | File gambar resep: `resep_dokter.png` (Ukuran: 1.5 MB). | 1. Klik tombol "Pilih File".<br>2. Pilih file `resep_dokter.png`.<br>3. Klik "Kirim Resep". | File berhasil terunggah, muncul notifikasi sukses, dan status pesanan menjadi "Menunggu Verifikasi". | File terunggah dan status berubah menjadi Menunggu Verifikasi. | Pass |

---

## 2. NEGATIVE CASE (Penanganan Error)

| Test Case ID | Test Item | Description | Pre-conditions | Input Data | Test Steps | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-NEG-01** | Validasi Login Email | Menguji sistem menolak login jika format email salah. | Pengguna berada di halaman Login. | - Email: sittirahmadhanigmail.com (tanpa @)<br>- Pass: Berva2026! | 1. Masukkan email salah.<br>2. Masukkan password.<br>3. Klik tombol "Login". | Sistem menolak login dan menampilkan pesan error: "Format email tidak valid, gunakan tanda '@'". | Sistem menolak login dan memunculkan pesan error sesuai ekspektasi. | Pass |
| **TC-NEG-02** | Validasi Ekstensi File | Menguji sistem memblokir format file selain gambar pada fitur resep. | Pelanggan sudah login dan berada di halaman "Unggah Resep". | File dokumen: `resep_obat.pdf` (Format dilarang). | 1. Klik tombol "Pilih File".<br>2. Pilih file `resep_obat.pdf`.<br>3. Klik "Kirim Resep". | Sistem memblokir unggahan dan memunculkan error: "Format file tidak didukung! Hanya file gambar (.jpg, .png)". | Unggahan diblokir dan muncul peringatan format merah. | Pass |

---

## 3. EDGE CASE (Kondisi Ekstrem)

| Test Case ID | Test Item | Description | Pre-conditions | Input Data | Test Steps | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **TC-EDG-01** | Batas Ukuran File (Size) | Menguji sistem menangani unggahan file gambar dengan ukuran sangat ekstrem. | Pelanggan berada di halaman "Unggah Resep". | File gambar: `resep_ultra_hd.jpg` (Ukuran: 25 MB). | 1. Pilih file gambar ukuran 25 MB.<br>2. Klik tombol "Kirim Resep". | Sistem menolak file sebelum diunggah ke server dengan pesan: "Ukuran file terlalu besar! Maksimal 5 MB". | File langsung ditolak secara cepat dengan notifikasi batas ukuran. | Pass |
| **TC-EDG-02** | Batas Kuantitas Belanja | Menguji keranjang belanja menolak input kuantitas angka minus atau nol. | Pelanggan berada di halaman Detail Produk/Obat. | Input Kuantitas Belanja: `-5` atau `0`. | 1. Buka produk Paracetamol.<br>2. Ketik manual angka -5 pada kolom jumlah.<br>3. Klik "Tambah ke Keranjang". | Sistem otomatis mengubah kuantitas menjadi angka `1` atau memunculkan pesan batas minimal pembelian. | Angka otomatis berbalik menjadi 1 saat tombol tambah diklik. | Pass |
 
