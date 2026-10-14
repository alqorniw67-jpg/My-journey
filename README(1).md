# English Journey — 30 Days Challenge

Aplikasi pelacak belajar bahasa Inggris 30 hari: dashboard, checklist + timer, absensi, kalender, catatan, pencapaian, pengingat, dan ekspor/impor data. Satu halaman statis (tanpa server, tanpa build) dan bisa dipasang di HP sebagai aplikasi (PWA).

## Isi folder
| File | Fungsi |
|---|---|
| `index.html` | Seluruh aplikasi (HTML + CSS + JavaScript) |
| `manifest.webmanifest` | Data agar bisa "Install / Tambahkan ke Layar Utama" |
| `sw.js` | Service worker agar bisa dibuka offline |
| `icon.svg`, `icon-192.png`, `icon-512.png` | Ikon aplikasi |

Semua path bersifat relatif, jadi aman di alamat seperti `https://username.github.io/nama-repo/`.
**Jangan ubah nama file** dan simpan semuanya dalam satu folder yang sama.

## Deploy ke GitHub Pages (tanpa Git/terminal)
1. Buat akun di https://github.com (gratis).
2. Klik **+ → New repository**. Nama bebas, misalnya `english-journey`. Pilih **Public**, lalu **Create repository**.
3. Klik **uploading an existing file**, lalu seret **keenam file (index.html, manifest.webmanifest, sw.js, icon.svg, dan dua ikon PNG)** dari folder ini (bukan foldernya) ke halaman. Klik **Commit changes**.
4. Buka **Settings → Pages**. Di *Build and deployment*, pilih **Source: Deploy from a branch**, **Branch: main**, folder **/(root)**, lalu **Save**.
5. Tunggu 1–3 menit. Alamatnya: `https://USERNAME.github.io/english-journey/`.
6. Buka alamat itu di Chrome Android → menu ⋮ → **Instal aplikasi / Tambahkan ke layar utama**.

### Mengubah/memperbarui
Edit atau upload ulang file di GitHub, lalu **naikkan angka versi** di `sw.js` (`english-journey-v1` → `v2`) agar HP mengambil versi terbaru.

## Alternatif gratis lain
- **Netlify Drop**: buka https://app.netlify.com/drop, seret folder ini. Langsung online.
- **Cloudflare Pages**: Create project → Direct Upload → unggah folder.

## Keterbatasan (jujur)
- **Data hanya di satu browser/perangkat.** Disimpan di localStorage; tidak sinkron antar HP/laptop, dan hilang jika data browser dihapus. Dibatasi per alamat situs: jika pindah alamat (mis. dari Netlify ke GitHub), data tidak ikut. Pakai **Pengaturan → Unduh JSON** secara rutin, lalu **Impor** di perangkat baru.
- **Pengingat tidak berjalan saat aplikasi ditutup.** Aplikasi tidak memakai server, jadi notifikasi hanya muncul saat halaman masih terbuka. Untuk pengingat yang andal, pakai **Unduh .ics** / **Google Calendar** di Pengaturan, atau alarm bawaan HP.
- **Offline & instalasi butuh HTTPS.** GitHub Pages/Netlify sudah HTTPS. Jika `index.html` dibuka langsung dari file (`file://`), aplikasi tetap jalan tetapi service worker dan instalasi tidak aktif.
- Safari iOS dapat menghapus data situs yang lama tidak dibuka; ekspor cadangan secara berkala.
- Tanggal mengikuti jam perangkat. Mengubah jam sistem dapat mempengaruhi hari yang terbuka.
- Dibangun dengan JavaScript biasa (bukan React/TypeScript/Tailwind) dan ikon emoji, agar tanpa proses build.

## Menjalankan di komputer sendiri
Di folder ini jalankan `python3 -m http.server 8000`, lalu buka http://localhost:8000.

## Masalah umum
- **Halaman 404**: pastikan `index.html` ada di akar repo dan Pages sudah aktif; tunggu beberapa menit.
- **Tampilan lama setelah update**: naikkan versi di `sw.js`, lalu muat ulang dua kali.
- **Impor gagal**: file harus hasil ekspor aplikasi ini dan belum diubah manual.
