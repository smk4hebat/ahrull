---
layout: post
title:  "Welcome to Jekyll!"
date:   2024-01-23 11:43:38 +0800
categories: jekyll update
---
1. Persiapkan Lingkungan Ruby:
Pastikan Ruby sudah terinstal di sistem Anda. Jika belum, instalasi dapat dilakukan melalui manajer paket atau unduh dari situs resmi Ruby.
2. Instal Jekyll:
Buka terminal atau command prompt, dan jalankan perintah berikut untuk menginstal Jekyll melalui RubyGems (manajer paket Ruby):
 bash
 Copy code
> gem install jekyll bundler
3. Buat Proyek Jekyll Baru:
 Setelah Jekyll terinstal, buat proyek baru dengan perintah:

 bash
 Copy code
 > jekyll new nama-situs
 4. Masuk ke Direktori Proyek:
 Pindah ke direktori proyek yang baru dibuat:

 bash
 Copy code
 > cd nama-situs
 5. Jalankan Server Lokal:
 Untuk melihat situs Anda secara lokal, jalankan server bawaan Jekyll:

 bash
 Copy code
 > bundle exec jekyll serve
 Situs akan tersedia di http://localhost:4000/ secara default. Buka browser dan kunjungi alamat tersebut.
 6. Edit Situs:
    Direktori proyek akan berisi struktur dasar situs Jekyll. Anda dapat mulai mengedit konten dan layout di direktori _posts dan _layouts. Untuk menambahkan halaman baru, Anda dapat membuat berkas Markdown (.md) di direktori utama.
 7. Build Situs:
   Jika sudah puas dengan perubahan Anda, hentikan server lokal (tekan Ctrl+C di terminal) dan bangun situs dengan perintah:

  bash
  Copy code
  > bundle exec jekyll build
  Berkas statis situs akan dihasilkan di direktori _site.
 8. Deploy Situs:
    Berkas di dalam direktori _site dapat diunggah ke penyedia hosting atau platform seperti GitHub Pages.