# Permintaan Data Daerah AMPK — Kabupaten/Kota

Paket ini memuat frontend Vercel auto-direct dan source Google Apps Script dari paket Kabupaten/Kota yang tersedia dalam percakapan.

## Isi paket
- `vercel/index.html`: halaman loading hijau yang otomatis mengalihkan ke deployment Apps Script, tanpa iframe.
- `apps-script/Code.gs`: backend Google Apps Script.
- `apps-script/Index.html`: formulir web app Apps Script.

## Perbaikan error iframe
Formulir Apps Script dapat dibuka langsung, tetapi browser menolak menampilkannya dalam iframe lintas domain. Frontend Vercel sekarang menggunakan `window.location.replace(APP_URL)` untuk membuka URL Apps Script secara langsung.

## Deploy frontend Vercel
1. Unduh/ekstrak ZIP.
2. Salin isi folder `vercel/` ke root repository GitHub `L200170065/kabkota-permindokditanak2026` (pastikan `index.html` berada di root).
3. Commit dan push ke branch yang terhubung dengan Vercel.
4. Pastikan deployment selesai, lalu buka `https://kabkota-permindokditanak2026.vercel.app/`.

## Apps Script
File di `apps-script/` adalah salinan source Apps Script yang tersedia di sesi ini. Frontend auto-direct memakai URL deployment yang sudah tersimpan di konfigurasi sebelumnya. Jika deployment Apps Script berubah, perbarui konstanta `APP_URL` di `vercel/index.html`.

## Penting
- Pengalihan langsung tidak mempertahankan loading screen setelah pengguna berpindah ke domain Apps Script; itu perilaku yang memang diperlukan untuk menghindari penolakan iframe.
- Paket ini dibuat dari file source yang tersedia di sesi ini. Saya tidak dapat melakukan push langsung ke GitHub dari sesi ini.
