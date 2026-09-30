# NexByte Monitor

NexByte Monitor adalah aplikasi desktop Windows untuk melihat kualitas koneksi internet. Aplikasi menampilkan ping, kecepatan download, dan kecepatan upload, dengan pilihan ukuran, transparansi, serta tema.

Repositori ini berisi situs unduhan dan kebijakan privasi, serta backend Google Apps Script untuk mencatat klik unduhan dan feedback. Source code aplikasi desktop tidak termasuk di repositori ini.

## Fitur

- Situs unduhan untuk NexByte Monitor di Windows 10 dan Windows 11.
- Galeri pratinjau aplikasi.
- Form rating dan feedback pengguna.
- Pencatatan klik unduhan secara anonim.
- Backend menyimpan klik dan feedback hingga 30 hari, dengan batas 1.000 catatan klik dan 300 feedback.
- Kebijakan privasi yang menjelaskan penggunaan data dan layanan pihak ketiga.

## Isi Repositori

- `index.html` dan `index.min.css`: halaman unduhan.
- `app.min.js`: interaksi halaman, tautan unduhan, pengiriman feedback, dan URL Google Apps Script.
- `privacy.html` dan `privacy.min.css`: halaman kebijakan privasi.
- `Code.gs`: backend Google Apps Script untuk klik unduhan dan feedback.
- `preview-*` dan file gambar lainnya: aset visual situs.

## Menjalankan Secara Lokal

Situs tidak memerlukan proses build atau instalasi dependensi. Dari direktori repositori, jalankan server web lokal:

```powershell
py -m http.server 8000
```

Kemudian buka <http://localhost:8000> di browser. Membuka `index.html` langsung juga dapat digunakan untuk melihat sebagian besar halaman, tetapi server lokal lebih sesuai untuk menguji situs.

## Deploy Situs ke GitHub Pages

1. Push file situs dan asetnya ke repositori GitHub.
2. Buka **Settings > Pages** di repositori.
3. Pada **Build and deployment**, pilih **Deploy from a branch**.
4. Pilih branch dan folder sumber yang berisi `index.html`, lalu simpan.
5. Pastikan URL situs serta halaman `privacy.html` dapat dibuka setelah deployment.

Tautan installer ditentukan oleh konstanta `DOWNLOAD_URL` di `app.min.js` dan saat ini mengarah ke GitHub Release `v1.0.0`. Perbarui URL tersebut jika nama file atau versi rilis berubah.

## Backend Google Apps Script

`Code.gs` menyediakan endpoint `doPost` untuk dua jenis request: `click` dan `feedback`. Data disimpan di Script Properties; catatan yang lebih lama dari 30 hari dibersihkan dan jumlah catatan dibatasi.

Untuk menggunakan deployment Apps Script sendiri:

1. Buat project di Google Apps Script dan salin isi `Code.gs`.
2. Deploy sebagai **Web app**, dengan eksekusi sebagai pemilik script dan akses yang mengizinkan pengunjung situs mengirim request.
3. Salin URL Web app yang berakhiran `/exec`.
4. Ganti konstanta `APPS_SCRIPT_URL` di `app.min.js` dengan URL deployment tersebut, lalu deploy ulang situs.

URL Apps Script saat ini sudah dikonfigurasi di `app.min.js`. Jangan masukkan kredensial atau rahasia ke file frontend publik.

## Privasi

Klik unduhan tidak menyertakan nama pengunjung. Feedback berisi rating, komentar, dan waktu pengiriman. Informasi koneksi untuk speed test diproses oleh layanan Cloudflare. Baca [Kebijakan Privasi](privacy.html) untuk detailnya.

## Rilis Aplikasi

Installer Windows tersedia melalui [GitHub Releases](https://github.com/zenkscammer/zenkscammer.github.io/releases). Situs saat ini menautkan `NexByte.Monitor.1.0.0.exe` dari rilis `v1.0.0`.
