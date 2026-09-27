1. Ringkasan Produk

Landing page profil kelompok KKN, dibangun dari awal, menampilkan identitas tim, struktur organisasi, dan dokumentasi kegiatan/proker, dengan tata letak mengikuti pola referensi (hero besar, kartu overlap, grid kategori, CTA section) dan palet warna pink soft serta hijau soft.

2. Latar Belakang

Kelompok KKN membutuhkan media publikasi digital untuk mendokumentasikan kegiatan dan memperkenalkan tim ke DPL, pihak kampus, aparat desa, dan masyarakat luas.

3. Tujuan
Memperkenalkan identitas tim KKN dan afiliasinya
Menampilkan struktur organisasi tim per divisi
Mendokumentasikan kegiatan/proker secara visual dan terstruktur
Menjadi portofolio kerja divisi PDD
4. Target Pengguna

DPL/pihak kampus, aparat desa/kabupaten, masyarakat desa, dan anggota tim sendiri (arsip dokumentasi), semua bertemu di satu landing page yang sama.

5. Ruang Lingkup

In scope: landing page single-page (scroll dengan anchor), konten statis, responsif.
Out of scope: login/admin panel, backend kompleks, database dinamis.

6. Struktur Konten (Sections)
Navbar — logo KKN, logo kabupaten/desa, nama tim, menu (Beranda, Tentang, Struktur Tim, Proker, Dokumentasi, Kontak), tombol CTA (misal link Instagram tim)
Hero — headline besar (nama/tema KKN), subheadline (lokasi dan tujuan singkat), dua tombol CTA, foto (cutout atau background biasa dengan overlay) dalam bingkai lingkaran bergaris putus-putus dengan elemen dekoratif melayang
Info/Highlight Card — foto kegiatan berbentuk blob/rounded-mask, kartu info berisi Lokasi Desa, Periode KKN, Jumlah Anggota, tombol "Lihat Struktur Tim" dan "Hubungi Kami"
Kategori Program Kerja — grid kartu kategori proker (Sosial, Pendidikan, Lingkungan, Budaya) tersusun overlap dengan rotasi ringan
Struktur Organisasi — foto masing-masing anggota dikelompokkan per divisi, koordinator ditonjolkan
Dokumentasi Kegiatan — grid kartu kegiatan (foto, judul, tanggal, badge kategori) dari foto kegiatan yang sudah ada
Sorotan Kegiatan — satu kegiatan besar ditonjolkan dengan foto besar dan ringkasan cerita, tombol "Baca Selengkapnya"
CTA Penutup — foto tim/kegiatan dengan ajakan (misal "Kenali Tim Kami Lebih Dekat") dan link ke struktur tim atau kontak
Footer — kolom Didukung Oleh, Kontak, Ikuti Kami (sosmed dan hashtag), hak cipta
7. Gaya Desain

Palet warna:

Primary: pink soft dan hijau soft, dipakai bergantian untuk aksen kartu, badge kategori, dan elemen dekoratif (misal kartu proker pakai nuansa hijau, kartu dokumentasi pakai nuansa pink, atau sebaliknya per kategori)
Secondary: putih sebagai warna dasar/background utama supaya kedua warna soft tadi tidak bentrok
Untuk tombol CTA dan teks, gunakan versi yang sedikit lebih gelap dari pink/hijau soft tersebut (bukan warna pastelnya langsung) supaya kontras terhadap putih tetap terbaca jelas
Footer bisa pakai hijau tua/gelap sebagai variasi, dengan teks putih, supaya tetap dalam keluarga warna yang sama tapi kontrasnya cukup

Elemen visual lain:

Tipografi sans-serif tebal untuk headline
Kartu bersudut membulat besar dengan bayangan lembut
Masking foto berbentuk blob/organik pada section highlight
Garis putus-putus dan ikon melayang di sekitar hero
Grid kartu overlap dengan rotasi ringan untuk kategori proker
Tombol rounded-full/pill

untuk contoh fullnya seperti pada gambar yang saya lampirkan
8. Aset Konten

Sudah tersedia: foto masing-masing anggota tim dan foto-foto dokumentasi kegiatan. Tidak perlu sesi foto tambahan. Hero memakai foto kegiatan/anggota yang paling representatif, di-cutout atau dipakai sebagai background dengan overlay warna.

9. Arsitektur Teknis & Hosting

Konten statis, tanpa database, hosting di Vercel. Data kegiatan dan anggota disimpan sebagai JSON/Markdown di repo, update lewat git push. Domain memakai domain bawaan .vercel.app.

10. Tech Stack Usulan
Framework: Vue 3 + Vite + Tailwind CSS, project baru dari nol
Gambar: folder /public, format WebP, lazy load
11. Non-Functional Requirements
Mobile-first
Waktu muat cepat, gambar teroptimasi
SEO dasar (meta title/description, Open Graph image)
Alt text pada semua gambar
Kontras warna teks terhadap background tetap terjaga meski memakai palet pastel
12. Sitemap

Single page dengan anchor scroll:
Beranda → Highlight → Kategori Proker → Struktur Organisasi → Dokumentasi → Sorotan Kegiatan → CTA → Kontak/Footer

13. Metrik Keberhasilan
Landing page live dan bisa diakses publik
Seluruh dokumentasi kegiatan dan struktur tim tertampil terstruktur
Feedback positif dari DPL/desa saat presentasi akhir KKN
