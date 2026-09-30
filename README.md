# NexByte

Repositori ini berisi situs unduhan NexByte untuk aplikasi desktop Windows NexByte Monitor, halaman kebijakan privasi, serta backend Google Apps Script untuk mencatat klik unduhan dan feedback. Source code aplikasi desktop tidak termasuk dalam repositori ini.

## Fitur

- Halaman unduhan untuk Windows 10 dan Windows 11.
- Galeri pratinjau aplikasi.
- Form rating dan feedback pengguna.
- Pencatatan klik unduhan secara anonim.
- Penyimpanan maksimal 1.000 catatan klik dan 300 feedback; data dihapus setelah 30 hari.
- Halaman kebijakan privasi.

## Struktur File

- `index.html`: halaman utama, metadata SEO, dan markup situs.
- `index.min.css` dan `privacy.min.css`: stylesheet produksi yang sudah diminifikasi.
- `app.min.js`: interaksi carousel, pengiriman feedback, pencatatan klik, serta URL installer dan Apps Script. File ini sudah diminifikasi.
- `privacy.html`: kebijakan privasi.
- `Code.gs`: backend Apps Script untuk klik unduhan dan feedback.
- `preview-1.webp` sampai `preview-4.webp`: pratinjau aplikasi resolusi penuh; halaman juga memakai varian thumbnail berukuran kecil dan `preview-1-960.webp` untuk tampilan carousel responsif.
- `nexbyte-icon.webp`: varian kecil ikon aplikasi untuk halaman; file WebP logo sumber dan `batik-pattern.svg` melengkapi aset visual.

## Menjalankan Secara Lokal

Situs statis ini tidak memerlukan proses build atau instalasi dependensi. Dari folder repositori, jalankan server lokal:

```powershell
py -m http.server 8000
```

Buka <http://localhost:8000>. Server lokal lebih sesuai daripada membuka file HTML langsung untuk memeriksa semua aset dan tautan.

## Rilis Situs dengan GitHub Pages

Repositori ini memakai nama `nexbyteexe.github.io`, sehingga alamat situsnya adalah <https://nexbyteexe.github.io/>.

1. Push file situs beserta semua aset yang digunakan ke branch `main`.
2. Buka **Settings > Pages** pada repositori GitHub.
3. Di **Build and deployment**, pilih **Deploy from a branch**.
4. Pilih branch `main` dan folder `/ (root)`, lalu simpan.
5. Tunggu deployment selesai, kemudian periksa halaman utama dan <https://nexbyteexe.github.io/privacy.html>.

## Rilis Installer Windows

Installer tersedia di [GitHub Releases](https://github.com/nexbyteexe/nexbyteexe.github.io/releases). URL file yang saat ini dipakai situs adalah:

```text
https://github.com/nexbyteexe/nexbyteexe.github.io/releases/download/v1.0.0/NexByte.1.0.0.exe
```

Saat menerbitkan versi baru:

1. Buat GitHub Release dengan tag versi, misalnya `v1.0.1`.
2. Upload installer `.exe` ke release dan catat nama file persis, termasuk huruf besar/kecil.
3. Ubah konstanta `DOWNLOAD_URL` di `app.min.js` agar menunjuk ke URL aset release baru.
4. Ubah nama file, ukuran, dan tanggal pembaruan pada `index.html` agar sesuai dengan installer yang diunggah.
5. Pastikan URL unduhan langsung berhasil dibuka sebelum push perubahan situs.

## Apps Script

`Code.gs` menerima request `click` dan `feedback`, lalu menyimpan data di Script Properties. Untuk memakai backend sendiri:

1. Buat project di Google Apps Script dan salin isi `Code.gs`.
2. Deploy sebagai **Web app**, dijalankan sebagai pemilik script, dengan akses yang mengizinkan pengunjung situs mengirim request.
3. Salin URL deployment yang berakhiran `/exec`.
4. Ganti konstanta `APPS_SCRIPT_URL` di `app.min.js`, lalu deploy ulang situs.

URL Apps Script saat ini sudah dikonfigurasi di `app.min.js`. Jangan menyimpan kredensial atau rahasia di file frontend publik.

## Pemanggilan Resource

JavaScript halaman utama memakai `defer`, sedangkan script Google Ads memakai `async`. CSS dan JavaScript sudah disediakan sebagai file minified. Halaman memakai system font stack, jadi tidak mengunduh web font dari layanan pihak ketiga. Gambar preview dimuat secara lazy dan menggunakan WebP terkompresi.

## Privasi

Klik unduhan tidak menyertakan nama pengunjung. Feedback mencakup rating, komentar, dan waktu pengiriman. Cloudflare memproses data teknis koneksi untuk menjalankan speed test. Detailnya tersedia di [Kebijakan Privasi](privacy.html).
