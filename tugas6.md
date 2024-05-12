![image](https://github.com/gedehariyogananda/SysAdmin-3122500005/assets/123063394/78519177-124f-4f72-8e69-5fc63a6b62d4)![image](https://github.com/gedehariyogananda/SysAdmin-3122500005/assets/123063394/e48b2b1f-be13-4f21-ac25-52474e7713e9)﻿<h1 align="center">
LAPORAN PRAKTIKUM WORKSHOP

**ADMINISTRASI JARINGAN**

</h1>
<p align="center">
“Architecture Web Server & Web Browser”
</p>

<p align="center">
    <img src="/img/covernobg.png" alt="Cover Image" width="480" height="420">
</p>

<h4 align="center">

Disusun Oleh:

**Gede Hari Yoga Nanda  					3122500005**

**Handaru Dwiki Yuntara     				3122500017**

**Muhammad Syahrul Ramadhan				3122500030**

</h4>

<h3 align="center">

2 D3 INFORMATIKA A

DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER JURUSAN TEKNIK INFORMATIKA
POLITEKNIK ELEKTRONIKA NEGERI SURABAYA

2023/2024

</h3>

<h2>Architecture Web Sever & Web Browser</h2>

<p align="center">
    <img src="/img/client_server.png" >
</p>

1. **Web Browser:**
   1. Web browser adalah aplikasi perangkat lunak yang diinstal di perangkat pengguna seperti komputer, ponsel, atau tablet.
   2. Browser memungkinkan pengguna untuk menjelajah internet dengan mengakses halaman web melalui protokol HTTP atau HTTPS.
   3. Ketika pengguna memasukkan URL atau melakukan pencarian, browser mengirimkan permintaan ke web server yang menghosting situs web yang diminta.
   4. Browser kemudian menerima respons dari web server, yang berisi kode HTML, CSS, JavaScript, dan konten lainnya yang membentuk halaman web.
   5. Browser menggunakan rendering engine untuk menguraikan kode tersebut dan menampilkan halaman web kepada pengguna dengan antarmuka pengguna yang sesuai.
2. **Web Server:**
   1. Web server adalah perangkat lunak yang berjalan di server dan menyimpan berbagai situs web.
   2. Web server menerima permintaan dari web browser melalui protokol HTTP atau HTTPS.
   3. Setelah menerima permintaan, web server mengambil halaman web yang diminta dari sistem file atau basis data server.
   4. Web server kemudian mengirimkan halaman web tersebut kembali kepada browser yang melakukan permintaan.
   5. Selain mengirimkan konten, web server juga dapat menangani proses seperti otentikasi pengguna, penyimpanan sesi, atau log aktivitas.

<h2>Perbedaan dan Peran Server Aplikasi dan Server Web:</h2>
<p align="center">
    <img src="/img/docker.jpg">
</p>

**Server Aplikasi:**
1. **Protokol Lebih dari HTTP:** 
   - Server aplikasi mampu bekerja dengan berbagai jenis protokol selain HTTP, memungkinkannya untuk menangani berbagai jenis program.
2. **Fungsionalitas Tambahan:** 
   - Selain menjalankan permintaan HTTP, server aplikasi menawarkan kemampuan tambahan yang memperluas fungsionalitasnya, seperti transaksi, personalisasi, dan layanan pesan.
3. **Komponen Penting dalam Layanan:** 
   - Server aplikasi seringkali mengintegrasikan server web sebagai bagian penting dari layanannya, memungkinkan untuk memberikan fitur tambahan dan menangani permintaan yang lebih kompleks.
4. **Manajemen Situs Web yang Efektif:** 
   - Dalam pengelolaan situs web, kombinasi antara server aplikasi dan server web sering memberikan hasil yang lebih baik, dengan server web menangani permintaan dasar dan konten statis, sementara server aplikasi menangani permintaan yang lebih dinamis.

**Server Web:**
1. **Fokus pada HTTP:** 
   - Server web secara khusus menjalankan permintaan HTTP untuk menampilkan halaman web kepada pengguna.
2. **Fungsi Utama Terbatas:** 
   - Meskipun server web bisa menyediakan fitur tambahan seperti penyimpanan sementara, fungsinya utamanya adalah menjalankan permintaan HTTP untuk menampilkan halaman web.
3. **Universal dalam Penyajian Konten:** 
   - Server web menyajikan konten yang sama kepada pengguna tanpa memandang lokasi atau perangkat pengguna, memungkinkan pengguna mengakses halaman web dengan mudah.
4. **Dukungan untuk Teknologi Adaptif:** 
   - Meskipun server web dapat menyajikan konten statis dengan baik, halaman web dengan komponen adaptif biasanya didukung oleh teknologi lain selain server web.
  

<h2>Container Docker</h2>
1. uninstall config docker sebelumnya : 
<p align="center">
    <img src="/img/jar1.png">
</p>

2. ** install docker engine, terdiri dari : **
   - docker official GPG KEY
   sudo apt-get install ca-certificates curl
<p align="center">
    <img src="/img/jar2.png">
</p>
   - lalu add repository to apt sources 
<p align="center">
    <img src="/img/jar3.png">
</p>


3. install docker-ce
<p align="center">
    <img src="/img/jar4.png">
</p>
yes all persetujuan 

4. selesai instalasi, coba docker run hello world
   karena unnable fine, jadi otomatis akan pull
<p align="center">
    <img src="/img/jar5.png">
</p>

dan berhasil 

5. coba cek container dengan docker ps -a
<p align="center">
    <img src="/img/jar6.png">
</p>

dan ada beberapa tampilan container yang berjalan 

<h2>instalasi uptime-kuma</h2>
1. instalasi kuma dengan membuka dokumentasi di github nya uptime-kuma dan lakukan instalasi 
https://github.com/louislam/uptime-kuma

<p align="center">
    <img src="/img/jar7puma.png">
</p>


2. lalu setelah berhasil, coba buka dengan url localhost:3001 port
<p align="center">
    <img src="/img/jar8success.png">
</p>

dan kuma berhasil tersintall :)
  

