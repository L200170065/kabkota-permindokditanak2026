# Vercel wrapper — kabkota-permindokditanak2026

Folder ini berisi `index.html` sebagai tampilan depan Vercel. Formulir dan proses simpan tetap berjalan melalui Google Apps Script.

URL Apps Script:
https://script.google.com/macros/s/AKfycbw1Ta-W-MR10_FYkw4pGXelXdVw_rSnD_lIyv9X4WGan7XEypL1a5kwKzDlgVGeDeBB6g/exec

## Langkah pemasangan

1. Di Google Apps Script, buka file `Code.gs`.
2. Pastikan fungsi `doGet()` mengizinkan iframe. Ganti menjadi:

```javascript
function doGet() {
  return HtmlService.createHtmlOutputFromFile('Index')
    .setTitle('Permintaan Data Daerah AMPK — Kabupaten/Kota')
    .addMetaTag('viewport', 'width=device-width, initial-scale=1')
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
}
```

3. Simpan perubahan lalu buka **Deploy → Manage deployments**.
4. Edit deployment Web App yang sesuai (atau buat deployment baru), pilih versi terbaru, dan pastikan akses sesuai kebutuhan pengguna kabupaten/kota. Klik **Deploy**.
5. Uji URL Apps Script langsung terlebih dahulu. Pastikan formulir tampil dan pengiriman data berhasil.
6. Di repository GitHub yang terhubung ke project Vercel `kabkota-permindokditanak2026`, unggah/ganti file `index.html` pada root repository dengan file dari folder ini.
7. Commit dan push. Tunggu deployment Vercel berstatus **Ready**, lalu uji domain Vercel di desktop dan HP.

## Catatan penting

- Jangan unggah `Code.gs` atau `Index.html` Apps Script ke root Vercel untuk menggantikan wrapper ini. Frontend tersebut memakai `google.script.run`, yang tersedia di Google Apps Script HTML Service.
- `ALLOWALL` memungkinkan halaman dimuat dalam iframe, tetapi juga mengizinkan situs lain menyematkan aplikasi. Gunakan hanya jika memang diperlukan untuk wrapper ini.
- Jika form tidak tampil di Vercel, buka URL Apps Script langsung. Jika URL langsung berjalan tetapi iframe gagal, periksa deployment Apps Script dan pengaturan `XFrameOptionsMode`.
