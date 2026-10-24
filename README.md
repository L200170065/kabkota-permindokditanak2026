# Deploy Vercel dengan Environment Variable

Paket ini menggunakan Vite agar URL Apps Script dapat dibaca dari Environment Variable pada saat build.

## 1. Environment Variable di Vercel

Buka project `kabkota-permindokditanak2026` → Settings → Environment Variables, lalu tambahkan:

- **Key:** `VITE_APPS_SCRIPT_URL`
- **Value:** `https://script.google.com/macros/s/AKfycbw1Ta-W-MR10_FYkw4pGXelXdVw_rSnD_lIyv9X4WGan7XEypL1a5kwKzDlgVGeDeBB6g/exec`
- **Environment:** Production (tambahkan Preview juga jika perlu menguji preview deployment)

Klik Save.

## 2. Unggah file ke repository GitHub

Ganti/unggah tiga file berikut pada root repository:
- `index.html`
- `package.json`
- `README.md` (opsional)

Pastikan `index.html` yang lama diganti dengan file dari paket ini.

## 3. Pengaturan Build Vercel

Di Settings → Build and Deployment, atur:
- Framework Preset: **Vite**
- Build Command: `npm run build`
- Output Directory: `dist`
- Install Command: `npm install`

Simpan pengaturan.

## 4. Redeploy

Buka Deployments, lalu lakukan Redeploy atau commit perubahan ke GitHub. Tunggu status `Ready`, kemudian buka domain produksi.

## Catatan penting tentang error 401

Environment Variable hanya menyimpan URL backend; ia tidak memperbaiki error 401 Google Apps Script dengan sendirinya. Jika domain Vercel tampil tetapi konten iframe masih 401, buka URL Apps Script secara langsung dan periksa deployment/access Apps Script. Jangan menyimpan password, PIN admin, atau secret privat dalam variabel `VITE_*`, karena variabel berawalan `VITE_` disertakan ke bundle frontend publik.
