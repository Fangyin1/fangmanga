# FangManga — Telegram Mini App

Static Next-free website for Vercel + Supabase. Includes reader, dark/light mode, profile/contact links and protected admin page.

## 1. Supabase
You already created `manga`, `chapters`, `pages` and the Storage bucket `manga`.
Run `supabase-policies.sql` in SQL Editor to enable public reading and admin writes.

## 2. Configure
Open `script.js`, `reader.js`, and `admin.js`. Replace:
- `PASTE_PROJECT_URL`
- `PASTE_PUBLISHABLE_KEY`
- In `script.js`, also set Telegram username/channel/email.

Use the same URL/key in all three files. The publishable key is okay in frontend code; never put a Supabase secret/service-role key here.

## 3. Admin
The `/admin.html` page uses Supabase Auth. Create your admin user in Authentication > Users. The password stays in Supabase; it is not hardcoded in the site.

## 4. Vercel
Upload this folder to GitHub or import it directly into Vercel as a static project. No build command is required. Output/root directory is the project root.

## 5. Telegram Mini App
Create a BotFather bot and set its Mini App/Web App URL to your Vercel URL. The same website can run in a normal browser and inside Telegram.

Only upload manga pages you own or have permission to redistribute.

## Fitur tambahan

- Banner Manga Populer berputar otomatis tiap 6 detik; daftar banner diurutkan berdasarkan jumlah pembaca dan mengambil hingga 5 manga teratas. Tombol panah dan titik navigasi juga tersedia.
- Lanjutkan membaca menyimpan manga, chapter, dan halaman terakhir pada localStorage browser/perangkat yang sedang digunakan.
- Komentar dan balasan per chapter.
- Dashboard admin menampilkan jumlah manga, chapter, halaman, komentar, total dibaca, dan daftar manga paling populer.

### Aktivasi Supabase
1. Buka Supabase Dashboard → SQL Editor.
2. Jalankan isi file `supabase-features.sql` satu kali untuk menambahkan kolom statistik, fungsi penghitung pembaca, tabel komentar, indeks, dan RLS komentar.
3. Deploy semua file website ke Vercel (termasuk `supabase-features.sql` untuk dokumentasi; SQL dijalankan manual, bukan oleh Vercel).

Catatan: riwayat lanjut membaca disimpan di browser/perangkat yang sama, belum disinkronkan antarperangkat. Komentar publik dapat dibaca dan ditulis oleh pengunjung; bila perlu, moderasi/admin dapat ditambahkan.
