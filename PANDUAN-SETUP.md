# Panduan Setup Dashboard Admin — Portal Kelurahan Letta

Website ini sudah dilengkapi dashboard admin (folder `/admin`) menggunakan **Decap CMS**
(sebelumnya bernama Netlify CMS) — CMS gratis dan open-source berbasis Git.

Staf kelurahan **tidak perlu tahu Git/GitHub sama sekali**. Mereka cukup login ke halaman
`namadomain.com/admin`, isi form, klik simpan — dan website otomatis ter-update.

## Yang sudah disiapkan di paket ini

Website ini sekarang terdiri dari **beberapa halaman terpisah** (bukan satu halaman panjang):

- `index.html` — **Beranda**: hero, Profil Kelurahan, Visi & Misi, Sejarah, Info Terkini, dan Peta
- `struktur.html` — halaman **Struktur Organisasi** (Lurah, RW, RT)
- `wisata.html` — halaman **Wisata & Kuliner** (pencarian & filter)
- `galeri.html` — halaman **Galeri**
- `pengaduan.html` — halaman **Pengaduan** (form ke WhatsApp)
- `assets/styles.css` — semua gaya/tampilan (dipakai bersama oleh semua halaman)
- `assets/nav.js` — kode menu navigasi (dipakai bersama oleh semua halaman)
- `content/team.json` — struktur organisasi (nama, jabatan, foto)
- `content/items.json` — daftar wisata & kuliner
- `content/berita.json` — daftar berita & informasi
- `admin/index.html` + `admin/config.yml` — dashboard admin (Decap CMS)
- `images/team/` — folder tempat foto anggota otomatis tersimpan saat diunggah lewat dashboard

**Penting:** karena sekarang banyak file HTML yang saling terhubung, saat mengunggah ke GitHub/Netlify pastikan **semua file dan folder di atas ikut terunggah dalam struktur yang sama** (jangan sampai ada yang tertinggal), supaya link antar halaman dan tampilannya tetap utuh.

## Langkah setup (dilakukan sekali oleh tim IT Diskominfo)

### 1. Aktifkan login untuk dashboard admin
1. Di dashboard Netlify, buka **Site configuration → Identity**, klik **Enable Identity**
2. Di bagian **Registration**, pilih **Invite only** (supaya tidak sembarang orang bisa daftar)
3. Buka tab **Services → Git Gateway**, klik **Enable Git Gateway**
4. Kembali ke tab **Identity**, klik **Invite users**, masukkan email staf kelurahan yang akan mengelola konten
5. Staf akan menerima email undangan, klik link di email untuk membuat password

## Cara staf kelurahan menggunakan dashboard

1. Buka `namadomain.com/admin` (atau `nama-acak-123.netlify.app/admin` sebelum domain disambungkan)
2. Login dengan email & password yang sudah dibuat
3. Pilih salah satu dari 3 menu:
   - **Struktur Organisasi** — isi/ubah nama, jabatan, dan unggah foto Lurah & staf
4. Klik **Save**, lalu klik **Publish** — perubahan otomatis tayang di website dalam 1-2 menit

## Catatan penting

- **Konten yang bisa diedit lewat dashboard saat ini terbatas** pada 3 hal di atas (statistik, struktur organisasi, wisata & kuliner). Teks naratif lain (Profil Daerah, Sejarah, Sorotan Wilayah) masih tertulis langsung di kode `index.html` — mengubahnya perlu edit HTML manual atau minta bantuan lagi untuk dijadikan bagian dashboard.
- Uji coba lokal: karena browser membatasi `fetch()` file lokal (`file://`), buka `index.html` lewat server lokal sederhana untuk testing (`python3 -m http.server` di folder ini, lalu akses `localhost:8000`), atau langsung uji setelah di-deploy ke Netlify.
- Semua perubahan tersimpan sebagai riwayat di GitHub — jika ada kesalahan, bisa dikembalikan ke versi sebelumnya lewat riwayat commit di GitHub.
