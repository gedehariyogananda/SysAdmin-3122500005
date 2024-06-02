<div align="center">
  <h1 style="text-align: center;font-weight: bold">Project Charter Container Based App<br>
Mobile Apps e-TOEFL</h1>
  <h3 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h3>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : <br>Kelompok 3 dan 5</h3>
  <div style="align: center;">
    <table>
      <tr>
        <th>No</th>
        <th>Nama</th>
        <th>NRP</th>
      </tr>
      <tr>
        <td>1</td>
        <td>Gede Hari Yoga Nanda</td>
        <td>3122500005</td>
      </tr>
      <tr>
        <td>2</td>
        <td>Arsyita Devanaya Arianto</td>
        <td>3122500008</td>
      </tr>
      <tr>
        <td>3</td>
        <td>Ali Azhar</td>
        <td>3122500011</td>
      </tr>
      <tr>
        <td>4</td>
        <td>Mahendra Khibrah R. S</td>
        <td>3122500013</td>
      </tr>
      <tr>
        <td>5</td>
        <td>Mayada Azizah</td>
        <td>3122500015</td>
      </tr>
      <tr>
        <td>6</td>
        <td>Gandi Rukmaning Ayu</td>
        <td>3122500016</td>
      </tr>
      <tr>
        <td>7</td>
        <td>Adam Rasyid Nurmuhammad</td>
        <td>3122500018</td>
      </tr>
      <tr>
        <td>8</td>
        <td>Adinda Zahra Q</td>
        <td>3122500020</td>
      </tr>
      <tr>
        <td>9</td>
        <td>M Reza Muktasib</td>
        <td>3122500024</td>
      </tr>
      <tr>
        <td>10</td>
        <td>Adira Callysta</td>
        <td>3122500025</td>
      </tr>
      <tr>
        <td>11</td>
        <td>Shofira Izza N</td>
        <td>3122500026</td>
      </tr>
    </table>
  </div>

<h2 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2023/2024</h2>
</div>

## Daftar Isi

- [Daftar Isi](#daftar-isi)
- [Pendahuluan](#pendahuluan)
- [Ruang Lingkup](#ruang-lingkup)
- [Desain Sistem](#desain-sistem)
- [Tim dan Tugas](#tim-dan-tugas)
- [Tahapan Pelaksaan](#tahapan-pelaksaan)
- [Implementasi](#implementasi)
- [Sistem testing](#sistem-testing)
- [Kesimpulan](#kesimpulan)

<hr>

## Abstrak

E-TOEFL adalah aplikasi mobile berbasis Flutter yang dirancang untuk membantu mahasiswa PENS dalam mempersiapkan tes e-TOEFL. Aplikasi ini menawarkan pengalaman belajar yang dipersonalisasi, memungkinkan pengguna memilih topik latihan dan memantau skor simulasi. Backend aplikasi menggunakan Laravel untuk autentikasi dan berinteraksi dengan MongoDB NoSQL yang menyimpan data dan melakukan operasi CRUD. Docker Engine digunakan untuk mengembangkan, mengirimkan, dan menjalankan aplikasi dalam kontainer, memastikan portabilitas, isolasi, dan kemudahan deployment. Desain sistem meliputi Storage Server pada port 3000 untuk penyimpanan file, Web Server Laravel pada port 80 untuk logika bisnis dan komunikasi dengan Storage Server dan MongoDB, serta MongoDB pada port 27017 untuk penyimpanan data aplikasi. Docker Engine menghubungkan antarmuka pengguna mobile dengan layanan backend. Tahapan pelaksanaan mencakup perencanaan dan analisis, desain dan prototyping, pengembangan dan implementasi, serta deployment dan pemeliharaan. Pada sistem testing terdapat pengujian unit, integrasi, sistem, dan uji pengguna. Docker memastikan konsistensi lingkungan pengujian. Aplikasi e-TOEFL diharapkan meningkatkan aksesibilitas dan efektivitas persiapan tes e-TOEFL bagi mahasiswa dengan sistem backend yang handal dan terkontainerisasi.

*Keywords:* *e-toefl, container, docker*

## Tahap Pelaksanaan

Proyek berlangsung selama 6 minggu, mulai dari tanggal 25 April 2024 hingga 30 Mei 2024. Dimana tahapan pelaksanaannya mencakup perencanaan dan analisis hingga pengujian.

## Pendahuluan

Docker adalah platform perangkat lunak yang memudahkan pembuatan, pengujian, dan penerapan aplikasi dengan cepat. Docker mengemas perangkat lunak ke dalam kontainer yang berisi semua kebutuhan perangkat lunak agar bisa berfungsi, seperti pustaka, alat sistem, kode, dan runtime. Dengan Docker, kita dapat dengan mudah menerapkan dan menskalakan aplikasi di berbagai lingkungan. Docker memiliki beberapa manfaat yaitu, portabilitas aplikasi yang dapat dijalankan di lingkungan apapun tanpa perlu mengubah konfigurasi, isolasi yang memastikan setiap kontainer berjalan terpisah dan aman dari aplikasi lain, kemudahan deployment dan skalabilitas aplikasi untuk menambah atau mengurangi instance kontainer dengan mudah.

Pada aplikasi eTOEFL, kami menggunakan Storage Server untuk menyimpan dan mengambil data, seperti file atau dokumen besar. Kami juga memanfaatkan Web Server yang menggunakan framework Laravel untuk mengelola request pengguna serta berinteraksi dengan Storage Server dan MongoDB Database untuk operasi CRUD. Selanjutnya, MongoDB Database digunakan untuk menyimpan data aplikasi. Terakhir, Docker Engine dipakai untuk mengembangkan, mmengirimkan dan menjalankan aplikasi dalam kontainer. Kemudian, Docker akan menghubungkan antarmuka pengguna pada perangkat mobile dengan backend seperti Web Server, MongoDB, dan Storage Server.

## Ruang Lingkup

eTOEFL adalah aplikasi berbasis mobile yang dikembangkan dengan Flutter dan memungkinkan pengguna untuk mengakses berbagai fitur dengan mudah. Kemudian, backend aplikasi menggunakan framework Laravel untuk mengatur autentikasi pengguna dan berinteraksi dengan database untuk penyimpanan dan pengambilan data. Untuk database aplikasi menggunakan MongoDB NoSQL yang berfungsi menyimpan dan mengambil data dari database serta memberikan respons terhadap permintaan pengguna. Terakhir, Server berfungsi sebagai perantara antara aplikasi mobile, backend, dan database. Server juga menerima request dari pengguna, kemudian meneruskannya ke backend dan database yang nantinya akan mengirimkan kembali respons kepada pengguna

## Desain Sistem

<div align="center">
  <img src="./img/arsitectur.png" alt="" width="80%" />
</div>

1. **Storage Server** berjalan pada port 3000 yang bertanggung jawab untuk menyimpan dan mengambil data, khususnya file atau dokumen besar yang diperlukan oleh aplikasi.

2. **Web Server Laravel** berjalan pada port 80, dikembangkan dengan framework laravel dengan peran sebagai pusat logika bisnis aplikasi dan mengelola permintaan dari frontend. Web server laravel bekerja untuk menerima permintaan dari docker engine, berkomunikasi dengan storage server untuk manajemen file, dan menjalankan operasi CRUD ke MongoDB database.

3. **MongoDB Database** berjalan pada port 27017 dan menerima permintaan dari web server larave melalui Docker Engine. MongoDB database bertugas untuk menyimpan data aplikasi dalam format NoSQL dan menjalankan operasi CRUD yang diminta oleh web server Laravel.

4. **Docker Engine** berperan sebagai perantara antara Mobile FE dan layanan backend seperti web server laravel, storage server, dan MongoDB database. Docker Engine berkomunikasi dengan Mobile FE melalui layanan backend yang sesuai, menerima permintaan, dan mengirimkan response.

5. **Mobile FE** berfungsi untuk menyajikan antarmuka pengguna yang dapat diakses melalui perangkat mobile. Mobile FE berinteraksi dengan Docker Engine untuk mengakses layanan backend dan menerima response.

## Tim dan Tugas

**Link Backlog:** https://docs.google.com/spreadsheets/d/1H3uiufmB5BPQeNi5vA3qUKwm-h5uV2LpxK4VTh3sPIg/edit?usp=sharing

<table class="tableizer-table">
<thead><tr class="tableizer-firstrow"><th>BACKLOG</th><th>TODO</th><th>EKSEKUTOR</th></tr></thead><tbody>
 <tr><td>Mobile Homepage</td><td>Slicing Card Target Score</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>&nbsp;</td><td>Consume Api Target Score</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Chart Pie Lingkaran</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Consume Rank User</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Card Navigasi Rank</td><td>Ali Azhar P.B</td></tr>
 <tr><td>&nbsp;</td><td>Consume For You List</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing For You Card</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Simulation Card</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>&nbsp;</td><td>Consume Learning Path Category Quiz</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Learning Path Card</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>&nbsp;</td><td>Design Card Set Target</td><td>Gandi Rukmaning Ayu, Adinda Zahra Q, Mayada Azizah</td></tr>
 <tr><td>&nbsp;</td><td>Design Chart Pie Lingkaran</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>&nbsp;</td><td>Design For You Card</td><td>Mayada Azizah, Adinda Zahra Q</td></tr>
 <tr><td>&nbsp;</td><td>Design Learning Path Card</td><td>Mayada Azizah, Adinda Zahra Q</td></tr>
 <tr><td>&nbsp;</td><td>Design Simulation Card</td><td>Adinda Zahra Q, Adinda Zahra Q</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Bottom Nav Bar</td><td>M Reza Muktasib</td></tr>
 <tr><td>Mobile Bookmark</td><td>Slicing Card Bookmark</td><td>Adam Rasyid Nurmuhammad</td></tr>
 <tr><td>&nbsp;</td><td>Consume Bookmark List</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Design Card Bookmark</td><td>Mayada Azizah, Adinda Zahra Q</td></tr>
 <tr><td>Mobile Profile</td><td>Design Profile Page</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>&nbsp;</td><td>Consume Profile User</td><td>Shofira Izza N</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Profile Page</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>Target Score</td><td>Slicing Target Score List</td><td>Adam Rasyid Nurmuhammad</td></tr>
 <tr><td>&nbsp;</td><td>Consume Target Score List</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Design Target Score Page</td><td>Mayada Azizah, Adinda Zahra Q</td></tr>
 <tr><td>Simulation Test List Page</td><td>Slicing Test List Page</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Consume List Test Page</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>Simulation Test Page</td><td>Slicing Bottom Nav Bar</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Design Bottom Nav Bar</td><td>Mayada Azizah, Adinda Zahra Q</td></tr>
 <tr><td>&nbsp;</td><td>Slicing List Soal Bottom Sheet</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Design List Soal Bottom Sheet</td><td>Mayada Azizah, Adinda Zahra Q</td></tr>
 <tr><td>&nbsp;</td><td>Implementasi Logic Test Question</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Consume Test Question Option dan Key</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Implementasi Logic Test Session</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Membuat State Management Test</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Test Result</td><td>Adam Rasyid Nurmuhammad</td></tr>
 <tr><td>&nbsp;</td><td>Logic Test Result</td><td>Mahendra Khibrah R. S</td></tr>
 <tr><td>Leaderboard</td><td>Design Leaderboard</td><td>Gandi Rukmaning Ayu, Mayada Azizah</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Leaderboard</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>&nbsp;</td><td>Consume Leaderboard</td><td>Arsyita Devanaya Arianto</td></tr>
 <tr><td>Quiz List Page</td><td>Design Quiz List Page</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Quiz List Page</td><td>Arsyita Devanaya Arianto, M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Consume Quiz List Page</td><td>M Reza Muktasib</td></tr>
 <tr><td>Quiz Page</td><td>Consume Quiz Question</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Logic Take Quiz</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Logic Result</td><td>M Reza Muktasib</td></tr>
 <tr><td>Game Page</td><td>Design Layout Game Path</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Layout Game Path</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Create Logic Path Background</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Consume List Game To Path</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Logic Resume Session</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Logic Quiz In Review</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Consume Quiz Question</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Quiz Page</td><td>Shofira Izza N</td></tr>
 <tr><td>&nbsp;</td><td>Logic Save User Answer</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Result Quiz</td><td>Shofira Izza N</td></tr>
 <tr><td>&nbsp;</td><td>Logic Result Quiz</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Quiz Game State </td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Bottom Sheet Game Detail</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Bottom App Bar Game Level</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Slicing Slash Screen</td><td>Shofira Izza N</td></tr>
 <tr><td>&nbsp;</td><td>Design Result Quiz</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>&nbsp;</td><td>Design Bottom Sheet Game Detail</td><td>Gandi Rukmaning Ayu</td></tr>
 <tr><td>Component</td><td>Base Button</td><td>Mahendra Kibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Background Question</td><td>Mahendra Kibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Setup TextTheme, Color Pallete</td><td>Mahendra Kibrah R. S, M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Answer Button Template</td><td>Mahendra Kibrah R. S, Shofira Izza N</td></tr>
 <tr><td>&nbsp;</td><td>Answer Validation Container</td><td>Mahendra Kibrah R. S</td></tr>
 <tr><td>&nbsp;</td><td>Design Component Base Button</td><td>Gandi Rukmaning Ayu, Adinda Zahra Q, Mayada Azizah</td></tr>
 <tr><td>&nbsp;</td><td>Design Answer Button</td><td>Gandi Rukmaning Ayu, Adinda Zahra Q, Mayada Azizah</td></tr>
 <tr><td>&nbsp;</td><td>Design Validation Answer</td><td>Gandi Rukmaning Ayu, Adinda Zahra Q, Mayada Azizah</td></tr>
 <tr><td>Assets</td><td>Membuat Maskot</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Ikon Bottom Navbar</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Ikon For You Card</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Ikon Representasi Part TOEFL</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Ikon Badge Game</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Ikon Rank</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Figur Orang Onboarding</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Figur Orang Login</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Assets Buku Game</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Ikon Reusable Black White</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Logo MyToefl</td><td>Ali Azhar P. B</td></tr>
 <tr><td>&nbsp;</td><td>Recreate Pilihan Target Onboarding asset</td><td>Ali Azhar P. B</td></tr>
 <tr><td>PostMan</td><td>Setup Postman</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Test Docs</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>QuiZGameDocs</td><td>M Reza Muktasib</td></tr>
 <tr><td>Admin Panel</td><td>Setup Web Server Service</td><td>M Reza Muktasib, Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Setup Mazer</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Form Input Test</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Membuat Form Input Question Answer</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Setup Login User Admin Panel</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Setup Swagger</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Quiz Form</td><td>M Reza Muktasib</td></tr>
 <tr><td>User Service</td><td>Setup User Service Container</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Setup Laravel Auth</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>JWT AUTH</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>User Api</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>User OTP SMTP</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>Test Service</td><td>Setup Test Service Container</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Packet Test Api</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Answer Test Api</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Bookmark Test Api</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>&nbsp;</td><td>Target Score Api</td><td>Gede Hari Yogananda</td></tr>
 <tr><td>Storage Service</td><td>Setup Container Storage</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Setup Gateway Storage</td><td>M Reza Muktasib, Gede Hari Yogananda</td></tr>
 <tr><td>Game Service</td><td>Setup Game Service Container</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Game Set Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Game HomePage Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Leaderboard Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Game Answer Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Scrambled Word Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Pairing Game Word Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Quiz Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Quiz Game Claim Api</td><td>M Reza Muktasib</td></tr>
 <tr><td>Database Service</td><td>Setup MongoDB Container</td><td>M Reza Muktasib</td></tr>
 <tr><td>&nbsp;</td><td>Setup Collection</td><td>M Reza Muktasib, Gede Hari Yogananda</td></tr>
 <tr><td>Utils</td><td>Data Entry</td><td>Mayada Azizah, Adinda Zahra Q, Adira Calysta</td></tr>
 <tr><td>&nbsp;</td><td>Scraping En_Word</td><td>M Reza Muktasib</td></tr>
</tbody></table>

## Tahapan Pelaksaan

<div align="center">
  <img src="./img/tahapan-pelaksanaan.jpg" alt="" width="100%" />
</div>

## Implementasi

**Tahap 1: Perencanaan & Analisis (Minggu 1-2)**

**Tujuan & Sasaran:** Output dari tahap ini adalah dokumen yang berisi tujuan dan sasaran implementasi E-TOEFL. Dokumen ini harus jelas, terukur, dapat dicapai, relevan, dan berjangka waktu (SMART). <br>
**Mengidentifikasi Target Pengguna:** Output dari tahap ini adalah profil target pengguna E-TOEFL. Profil ini harus mencakup informasi demografis, kebutuhan, dan ekspektasi pengguna. <br>
**Gamifikasi:** Output dari tahap ini adalah desain gamifikasi yang akan diterapkan pada E-TOEFL. Desain ini harus menarik dan memotivasi pengguna untuk menyelesaikan tes. <br>
**Rancangan Database:** Output dari tahap ini adalah rancangan database yang akan digunakan untuk menyimpan data pengguna, hasil tes, dan informasi lainnya. <br>
**Pemilihan Teknologi:** Output dari tahap ini adalah pilihan teknologi yang akan digunakan untuk mengembangkan E-TOEFL. Pilihan teknologi ini harus mempertimbangkan faktor-faktor seperti skalabilitas, keamanan, dan kemudahan penggunaan.

**Tahap 2: Desain & Prototyping (Minggu 3-4)**

**Desain UI/UX:** Output dari tahap ini adalah desain antarmuka pengguna (UI) dan pengalaman pengguna (UX) E-TOEFL. Desain ini harus intuitif, mudah digunakan, dan estetis. <br>
**Pengembangan Konten:** Output dari tahap ini adalah konten tes E-TOEFL. Konten ini harus sesuai dengan standar internasional dan relevan dengan kebutuhan target pengguna.

**Tahap 3: Pengembangan & Implementasi (Minggu 5-6)**

**Pengembangan FE Mobile:** Output dari tahap ini adalah aplikasi mobile E-TOEFL. Aplikasi ini harus memungkinkan pengguna untuk mengikuti tes dari perangkat mobile mereka. <br>
**Pengembangan BE:** Output dari tahap ini adalah backend E-TOEFL. Backend ini harus bertanggung jawab untuk memproses data pengguna, hasil tes, dan informasi lainnya. <br>
**Containerization Docker:** Output dari tahap ini adalah container Docker untuk E-TOEFL. Container ini akan memungkinkan E-TOEFL untuk dijalankan dengan mudah di berbagai lingkungan.

**Tahap 4: Testing & Deployment (Minggu 7-8)**

**Testing Installation:** Output dari tahap ini adalah instalasi E-TOEFL di lingkungan produksi. Instalasi ini harus memastikan bahwa E-TOEFL berjalan dengan lancar dan aman. <br>
**Functional Testing:** Output dari tahap ini adalah pengujian fungsional E-TOEFL. Pengujian ini harus memastikan bahwa semua fitur E-TOEFL berfungsi dengan benar. <br>
**Uji Coba:** Output dari tahap ini adalah hasil uji coba E-TOEFL dengan pengguna nyata. Uji coba ini harus mengidentifikasi masalah dan bug yang masih ada. <br>
**Peluncuran:** Output dari tahap ini adalah peluncuran E-TOEFL ke publik. Peluncuran ini harus dilakukan dengan strategi yang tepat untuk memastikan kelancaran dan kesuksesan.

## Sistem testing

### Fungsional Testing API
![image](https://github.com/gandirayu/Administrasi_Jaringan/assets/123063394/bd1b4ac9-deaf-4d75-83a4-65a3753d5ba9)

link documentation API -> https://docs.google.com/spreadsheets/d/1-Jroqy-IDRazHRMXz3AzIXzvIScPwYVNrdnf1L9PnkQ/edit?usp=sharing

## Kesimpulan

Melalui tahapan pelaksanaan ini, diharapkan aplikasi e-TOEFL dapat membantu mahasiswa PENS dalam mempersiapkan diri menghadapi tes e-TOEFL dengan lebih baik, memberikan pengalaman belajar yang dipersonalisasi, serta membuat tes e-TOEFL lebih mudah diakses. Implementasi teknologi yang tepat serta pengujian yang komprehensif akan memastikan aplikasi berjalan dengan baik dan memenuhi kebutuhan pengguna.

Penerapan teknologi Docker Engine dalam aplikasi E-TOEFL menghadirkan banyak keuntungan. Konsistensi dan efisiensi operasional terjamin, deployment dan skalabilitas menjadi mudah, serta keamanan dan keandalan aplikasi terjaga. Docker Engine mengisolasi aplikasi, membuatnya aman dan terlindungi. Image yang tidak dapat diubah memastikan aplikasi selalu berjalan dalam kondisi yang ideal. Keunggulan ini menjadikan Docker Engine sebagai alat penting dalam memastikan kelancaran dan keandalan E-TOEFL.

Keunggulan utama dari penggunaan Docker dalam proyek ini meliputi:

- **Portabilitas:** Aplikasi dapat berjalan di berbagai lingkungan tanpa perlu mengubah konfigurasi, sehingga memudahkan proses pengembangan dan deployment.
- **Isolasi Lingkungan:** Setiap container berjalan terpisah, yang memastikan tidak ada konflik antara layanan yang berbeda dan meningkatkan keamanan
- **Skalabilitas:** Dengan Docker, menambah atau mengurangi instance container dapat dilakukan dengan mudah sesuai kebutuhan, memungkinkan aplikasi untuk mengelola beban kerja yang dinamis
- **Efisiensi:** Docker memungkinkan pemanfaatan sumber daya yang lebih baik dan meminimalkan overhead yang biasanya terkait dengan virtualisasi tradisional.
