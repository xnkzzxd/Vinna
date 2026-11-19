# Coach Vinna

Situs aplikasi personal training Coach Vinna (panel coach + portal klien), tersambung ke spreadsheet XNK milik
Vinna (sama dengan `xnk.web.id/vinna`), tetapi di **domain sendiri**. Gratis lewat GitHub Pages dan bisa dibuka
tanpa sinyal.

- `/` → panel coach (masuk dengan PIN)
- `/klien/` → portal klien (masuk dengan nomor WhatsApp). Link inilah yang dibagikan ke klien.

`config.json` sudah berisi link `/exec` dan nama usaha Vinna. **PIN, data klien, harga dan jadwal tidak disimpan di
repo ini**: semuanya ada di spreadsheet Vinna (repo ini publik).

## Setup (sekali)

1. **Settings → Pages → Source**: pilih **GitHub Actions**.
2. **Actions → Setup situs → Run workflow** (isian boleh kosong). Tunggu ±1 menit sampai centang hijau.
   Situs tayang di `https://xnkzzxd.github.io/Vinna/`. Coba buka dan masuk dengan PIN.

## Pasang domain sendiri

Contoh di bawah memakai `coachvinna.com`; ganti dengan domain Vinna.

1. **DNS** (di tempat domain didaftarkan), pilih salah satu:

   **a. Domain utama** (`coachvinna.com`):

   | Jenis | Nama | Nilai |
   | --- | --- | --- |
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | AAAA | `@` | `2606:50c0:8000::153` |
   | AAAA | `@` | `2606:50c0:8001::153` |
   | AAAA | `@` | `2606:50c0:8002::153` |
   | AAAA | `@` | `2606:50c0:8003::153` |
   | CNAME | `www` | `xnkzzxd.github.io` |

   **b. Subdomain** (mis. `app.coachvinna.com`): cukup satu baris `CNAME` · `app` · `xnkzzxd.github.io`.

   Bila GitHub mengubah alamat ini, ikuti dokumentasi *GitHub Pages → custom domain* yang terbaru.
2. **Settings → Pages → Custom domain**: isi domainnya, **Save**, tunggu centang DNS hijau (beberapa menit sampai
   beberapa jam), lalu centang **Enforce HTTPS**.
3. (Disarankan) **Verifikasi domain** di pengaturan akun GitHub (Settings → Pages → Add a domain), supaya orang lain
   tidak bisa memasang domain itu di repo mereka.
4. Di spreadsheet Vinna: **XNK → Mulai setup → langkah 4**, isi alamat utama situs (mis. `https://coachvinna.com`,
   tanpa `/klien/`). Link di pesan WhatsApp ke klien otomatis menuju `<alamat>/klien/`.

Setelah domain aktif, bagikan `https://<domain>/klien/` ke klien. Alamat lama `xnk.web.id/vinna/klien/` tetap jalan
selama Vinna masih ada di hub, tetapi penyimpanan offline dan login di browser terpisah per alamat, jadi klien
perlu masuk sekali lagi di alamat baru.

## Mengubah situs

| Mau mengubah | Caranya |
| --- | --- |
| Link /exec atau nama usaha | Jalankan lagi **Setup situs**, isi yang berubah saja. Atau ubah `config.json`. |
| Ikon, halaman tambahan | Taruh berkas di folder `custom/` (lihat `custom/README.md`). |
| Domain | Settings → Pages → Custom domain. |

Setiap perubahan di `main` membangun ulang situs. Setiap hari jam 03:17 WIB situs dibangun ulang dari kode XNK yang
sudah lulus pemeriksaan (tag `hub-stable`, sama dengan hub). `config.json` dan `custom/` tidak pernah ditimpa.

## Kalau ada masalah

- **Workflow merah "GitHub Pages belum dinyalakan"**: ulangi langkah Setup 1, lalu jalankan workflow lagi.
- **Masuk dengan PIN gagal terus**: cek PIN di spreadsheet (**XNK → Mulai setup → langkah 2**).
- **Halaman lama masih tampil**: tutup lalu buka lagi situsnya (salinan offline diperbarui di latar).

Belum ada di situs ini: halaman info publik (profil, paket, harga; di hub ada di `xnk.web.id/vinna/info/`) dan
notifikasi push ke HP.
