<h1 align="center">
LAPORAN PRAKTIKUM WORKSHOP

**ADMINISTRASI JARINGAN**
</h1>
<p align="center">
“MAIL SERVER DEBIAN 10, BIND9, POSTFIX, DOVECOT, ThunderBird, RoundCube”
</p>

<p align="center">
    <img src="img/covernobg.png" alt="Cover Image" width="480" height="420">
</p>

<h4 align="center">
   
Disusun Oleh:

**Gede Hari Yoga Nanda  					3122500005**

</h4>

<h3 align="center">  
   
2 D3 INFORMATIKA A


DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER JURUSAN TEKNIK INFORMATIKA
POLITEKNIK ELEKTRONIKA NEGERI SURABAYA

2023/2024
</h3> 

<hr>

# WEB EMAIL SYSTEM

## NTP Client
1. Lakukan instalasi layanan sinkronisasi waktu

    ``apt install systemd-timesyncd``

2. Melakukan konfigurasi timezone ke Asia/Jakarta

   ``sudo timedatectl set-timezone Asia/Jakarta`` <br>
   ``sudo timedatectl set-local-rtc false`` <br>
   ``sudo timedatectl set-ntp true``

  <p align="">
        <img src="img/tugas5/6.1 real.png" alt="Cover Image">
  </p>

3. Edit file timesyncd.conf 

    ``sudo nano /etc/systemd/timesyncd.conf`` <br>
    tambahkan konfigurasi : 
    NTP=0.id.pool.ntp.org <br>
     <p align="">
        <img src="img/tugas5/6.2 done.png" alt="Cover Image">
    </p>

4. Restart system-timesyncd

   ``sudo systemctl restart systemd-timesyncd``
   <p align="">
        <img src="img/tugas5/6.3.png" alt="Cover Image">
    </p>

5. Lakukan pengecekan kesesuaian tanggal system dengan perintah 

    ``sudo timedatectl``
   <p align="">
        <img src="img/tugas5/6.4 (last).png" alt="Cover Image">
    </p>


## Apache 2 + PHP-FM
1. Install Apache2

   ``sudo apt -y install apache2``
    <p align="">
        <img src="" alt="Cover Image">
    </p>


2. Mengkonfigurasi Apache2 
    ``sudo nano /etc/apache2/conf-enabled/security.conf`` <br>
    uncoment ServerToken Prod
    ServerTokens Prod <br>
    <p align="">
        <img src="img/tugas5/6.5.png" alt="Cover Image">
    </p>

   ``sudo nano /etc/apache2/mods-enabled/dir.conf`` <br>
    add file agar bisa dibaca
    DirectoryIndex index.html index.htm index.php ... <br>
     <p align="">
        <img src="img/tugas5/6.6.png" alt="Cover Image">
    </p>

   ``sudo nano /etc/apache2/apache2.conf``
    - benahi spesifik ServerName ke nama domain
    ServerName www.kelompok4.local <br>
     <p align="">
        <img src="img/tugas5/6.7.png" alt="Cover Image">
    </p>

    ``sudo nano /etc/apache2/sites-enabled/000-default.conf``
    - rubah webmaster ke nama domain
    ServerAdmin webmaster@kelompok4.local <br>
     <p align="">
        <img src="img/tugas5/6.8.png" alt="Cover Image">
    </p>

    ``sudo systemctl reload apache2``
   reload untuk melakukan reload pada konfigurasi apache

4. Melakukan test apakah sudah berjalan di web browser <br>
    <p align="">
        <img src="img/tugas5/ngkosik iki php.png" alt="Cover Image">
    </p>

### Install PHP 8.2

1.  Install php dengan perintah berikut
    ``apt -y install php8.2 php8.2-mbstring php-pear``
     <p align="">
        <img src="img/tugas5/6.10.png" alt="Cover Image">
    </p>
    berikut isntalasi berhasil : 
      <p align="">
        <img src="img/tugas5/6.11.png" alt="Cover Image">
    </p>
    
2. Mengkonfigurasi PHP-FM pada file konfigurasi Apache
    ``nano /etc/apache2/sites-available/default-ssl.conf`` <br>
   tambahkan konfigurasi :<br>
    <FilesMatch \.php$> <br>
        SetHandler "proxy:unix:/var/run/php/php8.2-fpm.sock|fcgi://localhost/" <br>
   </FilesMatch> <br>
   <p align="">
        <img src="img/tugas5/6.12.png" alt="Cover Image">
    </p>

    `` a2enmod proxy_fcgi setenvif `` <br>
    <p align="">
        <img src="img/tugas5/6.13.png" alt="Cover Image">
    </p>

    `` a2enconf php8.2-fpm`` <br>
     <p align="">
        <img src="img/tugas5/8.14.png" alt="Cover Image">
    </p>

    ``systemctl restart php8.2-fpm apache2`` <br>
    untuk merestart kofigur yang barusan di setup

3. Melakukan test validasi dengan phpinfo()

    ``echo '<?php phpinfo(); ?>' > /var/www/html/info.php`` <br>
     <p align="">
        <img src="img/tugas5/7.15.png" alt="Cover Image">
    </p>

4. Lakukan pemgecekan di broser apakah sudah tersambung
   <p align="">
        <img src="img/tugas5/6.16.png" alt="Cover Image">
    </p>

## Database System MariaDB

1. Lakukan instalasi Maria DB 10.11 <br>
   ``apt -y install mariadb-server`` <br>
    <p align="">
        <img src="img/tugas5/6.17.png" alt="Cover Image">
    </p>

2. Lakukan config di file berikut : <br>
   ``nano /etc/mysql/mariadb.conf.d/50-server.cnf`` <br>
    character-set-server = utf8mb4 <br>
    collation-server = utf8mb4_general_ci <br>
     <p align="">
        <img src="img/tugas5/6.18.png" alt="Cover Image">
    </p>
3. restart mariadb konfig <br>
    ``systemctl restart mariadb``

4. Inisial Konfigurasi dan testing database MariaDB Server

    ``mysql_secure_installation``
    <p align="">
        <img src="img/tugas5/6.19.png" alt="Cover Image">
    </p>
    <br>

    jalankan: <br>
    ``mysql'' <br>
    ``show grandts fot root@localhost;  ``<br>
    <p align="">
        <img src="img/tugas5/6.20.png" alt="Cover Image">
    </p>
    <br>
    ``select user,host,password from mysql.user;`` <br>
    ``show database`` <br>
     <p align="">
        <img src="img/tugas5/6.21.png" alt="Cover Image">
    </p>
    ``create database test; ``<br>
    ``use test (lalu insert coba data dumy)     `` <br>
    ``select * from test`` <br>
    <p align="">
        <img src="img/tugas5/6.22.png" alt="Cover Image">
    </p>

## Install PHPMYADMIN
1. pertama2 dengan perintah apt install phpmyadmin
   ``sudo apt -y install phpmyadmin``
   pilih apache untuk webserver
    <p align="">
        <img src="img/tugas5/php 6.23.png" alt="Cover Image">
    </p> <br>

2. Tunggu proses instalasi <br>
    <p align="">
        <img src="img/tugas5/6.24.png" alt="Cover Image">
    </p> <br>
3. akan ada konfigurasi untuk password <br>
        <p align="">
        <img src="img/tugas5/6.25 ikisik.png.png" alt="Cover Image">
    </p> <br>
3. lalu selesai instalasi
   <p align="">
        <img src="img/tugas5/6.25.png" alt="Cover Image">
    </p> <br>
4. Melakukan konfigurasi pada apache2.conf <br>
    ``sudo nano /etc/apache2/apache2.conf`` <br>
    <p align="">
        <img src="img/tugas5/6.26.png" alt="Cover Image">
    </p> <br>
    
5. Lalu restart untuk merefresh dari konfigurasi <br>
    ``sudo systemctl restart apache2`` <br>
    <p align="">
        <img src="img/tugas5/6.27.png" alt="Cover Image">
    </p> <br>
6. cek apakah bisa diakses di web server phpmyadmin <br>
       <p align="">
        <img src="img/tugas5/6.28(30gaonoke).png" alt="Cover Image">
    </p> <br>
      <p align="">
        <img src="img/tugas5/ss phpmyadmin.png" alt="Cover Image">
    </p> <br>
7. Menambahkan privilage ke user phpmyadmin
   ``mysql -u root -p`` <br>
   ``GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
FLUSH PRIVILEGES;`` <br>
     <p align="">
        <img src="img/tugas5/6.29.png" alt="Cover Image">
    </p> <br>
   
    
## Install Email System POSTFIX SMTP Server 

1. install dengan perintah berikut <br>
    ``apt -y install postfix sasl2-bin`` <br>
   <p align="">
        <img src="img/tugas5/6.32.png" alt="Cover Image">
    </p> <br>
    - pilih no konfigur
     <p align="">
        <img src="img/tugas5/6.33.png" alt="Cover Image">
    </p> <br>
   
2. copy main.cf.dist ke posfix
   ``cp /usr/share/postfix/main.cf.dist /etc/postfix/main.cf`` <br>
     <p align="">
        <img src="img/tugas5/6.34.png" alt="Cover Image">
    </p>

    ``nano /etc/posfix/main.cf``
    - #line 82 : uncomment <br> mail_owner = postfix <br>
    <p align="">
        <img src="img/tugas5/6.35.png" alt="Cover Image">
    </p>
    
    - #line 98 : uncomment and specify hostname <br> myhostname = mail.kelompok4.local dan mydomain = kelompok4.local<br>
     <p align="">
        <img src="img/tugas5/6.36.png" alt="Cover Image">
    </p>
    
    - #line 127 : uncomment <br>
    ``myorigin = $mydomain`` <br>
    - #line 141 : uncomment <br>
    ``inet_interfaces = all``
     <p align="">
        <img src="img/tugas5/6.37.png" alt="Cover Image">
    </p>
    
    - #line 189 : uncomment <br>
   `` mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain ``
     <p align="">
        <img src="img/tugas5/6.38.png" alt="Cover Image">
    </p>
    
    - #line 277 : uncomment <br>
   `` mynetworks_style = subnet `` <br>
   `` mynetworks = 127.0.0.0/8, 10.0.0.0/24, 192.168.0.0/16`` <br>
     <p align="">
        <img src="img/tugas5/6.39.png" alt="Cover Image">
    </p> <br>
    ``alias_maps = hash:/etc/aliases`` <br>
    ``alias_database = hash:/etc/aliases``
     <p align="">
        <img src="img/tugas5/6.40.png" alt="Cover Image">
    </p> <br>
    ``home_mailbox = Maildir/ ``
     <p align="">
        <img src="img/tugas5/6.41.png" alt="Cover Image">
    </p> <br>
    
    - #line 585: comment out and add <br>
    #smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU) <br>
    menjadi : 
    ``smtpd_banner = $myhostname ESMTP``
     <p align="">
        <img src="img/tugas5/6.42.png" alt="Cover Image">
    </p>
    
    - #line 659 : add <br>
    ``sendmail_path = /usr/sbin/postfix`` <br>
    ``newaliases_path = /usr/bin/newaliases`` <br>
    ``mailq_path = /usr/bin/mailq`` <br>
    ``setgid_group = postdrop`` <br>
      <p align="">
        <img src="img/tugas5/6.43.png" alt="Cover Image">
    </p> <br>
    
    - #line 688 : comment out <br>
    #sample_directory = ``<br>
    ``readme_directory = ``<br>
    ``inet_protocols = ipv4`` <br>
    ``disable_vrfy_command = yes `` <br>
    ``smtpd_helo_required = yes `` <br>
    ``message_size_limit = 10240000`` <br>
    ``smtpd_sasl_type = dovecot`` <br>
    ``smtpd_sasl_path = private/auth`` <br>
    ``smtpd_sasl_auth_enable = yes`` <br>
    ``smtpd_sasl_security_options = noanonymous`` <br> 
    ``smtpd_sasl_local_domain = $myhostname`` <br>
    ``smtpd_recipient_restrictions = permit_mynetworks, permit_auth_destination,permit_sasl_authenticated, reject`` <br>
    <p align="">
        <img src="img/tugas5/6.45.png" alt="Cover Image">
    </p> <br>
    
3. ``newaliases `` <br>
    ``systemctl restart postfix `` <br>
     <p align="">
        <img src="img/tugas5/6.46.png" alt="Cover Image">
    </p> <br>

    
4. Menambahkan konfigurasi anti spam
    ``nano /etc/postfix/main.cf ``
    #add to the end <br>
    #reject unknown clients that forward lookup and reverse lookup of their hostnames on DNS do
    not match <br>
    ``smtpd_client_restrictions = permit_mynetworks, reject_unknown_client_hostname, permit 
    smtpd_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_non_fqdn_sender
    smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, reject_non_fqdn_hostname, reject_invalid_hostname, permit`` 
      <p align="">
        <img src="img/tugas5/6.47.png" alt="Cover Image">
    </p> <br>

5. jangan lupa untuk restart <br>
   ``systemctl restart postfix`` <br>

## DOVECOT : IMAP4 (TCP 143) and POP3 (TCP110) Server

1. Instalasi Dovecot Server
    ``apt -y install dovecot-core dovecot-pop3d dovecot-imapd`` <br>
   <p align="">
        <img src="img/tugas5/6.48.png" alt="Cover Image">
    </p> <br>
    
   ``nano /etc/dovecot/dovecot.conf`` <br>
    benahi seperti : <br>
   ``listen = *, :: `` <br>
       <p align="">
        <img src="img/tugas5/6.49.png" alt="Cover Image">
    </p> <br>

    
    ``nano /etc/dovecot/conf.d/10-auth.conf`` <br>
    ``disable_plaintext_auth = no`` <br>
    <p align="">
        <img src="img/tugas5/6.50.png" alt="Cover Image">
    </p> <br>
    
    ``auth_mechanisms = plain login`` <br>
     <p align="">
        <img src="img/tugas5/6.51.png" alt="Cover Image">
    </p> <br>

    ``nano /etc/dovecot/conf.d/10-mail.conf`` <br>
    ``mail_location = maildir:~/Maildir`` <br>
    ``nano /etc/dovecot/conf.d/10-master.conf`` <br>
    ``unix_listener /var/spool/postfix/private/auth {
    mode = 0666 <br>
    user = postfix <br>
    group = postfix <br>
    } ``
    <br>
   <p align="">
        <img src="img/tugas5/mbenahi .png" alt="Cover Image">
    </p> <br>
2. Jangan lupa untuk restart dovecot dengan configurasi diatas : <br>
    ``systemctl restart dovecot`` <br>

3. CHECK untuk semua SERVICES :
    ``netstat -a| grep LISTEN`` <br>
       <p align="">
        <img src="img/tugas5/perintahjalan 6.53.png" alt="Cover Image">
    </p> <br>
    
### Melakukan Cek terhadap Layanan Posfix
`` telnet mail.kelompok4.local 25
`` 
   <p align="">
        <img src="img/tugas5/telnet.png" alt="Cover Image">
    </p> <br>
<br>

## Test Email Menggunakan Thunderbird

1. Install Thunderbird <br>
    ``apt-get install thunderbird ``
     <p align="">
        <img src="img/tugas5/6.55.png" alt="Cover Image">
    </p> <br>

    berikut tampilan dari thunderbird
      <p align="">
        <img src="img/tugas5/6.56.png" alt="Cover Image">
    </p> <br>

3. Testing kirim email dari user pertama ke user kedua
    pesan berhasil terkirim ke user ary@mail.kelompok4.local <br>

5. Testing kirim email dari user kedua ke user pertama
    Berhasil saling mengirim pesan, yang mana artinya email sistem telah berjalan dengan benar.

## Email Client Menggunakan Web (ROUNDCUBE)

1. Install Roundcube terlebih dahulu <br>
    <p align="">
        <img src="img/tugas5/sik.png" alt="Cover Image">
    </p> <br>

2. Lakukan config  <br>
    ``nano /etc/roundcube/config.inc.php`` <br>
    <p align="">
        <img src="img/tugas5/6.61.png" alt="Cover Image">
    </p> <br>

3. Lakukan config file apache pada roundcube, uncomment line 3 dan hapus public_html path. <br>
   ``nano /etc/roundcube/apache.conf`` <br>
      <p align="">
        <img src="img/tugas5/6.62.png" alt="Cover Image">
    </p> <br>

4. Lakukan symlink pada folder roundcube
      <p align="">
        <img src="img/tugas5/6.63.png" alt="Cover Image">
    </p> <br>

5. Tambahkan Servername dan DocumentRoot pada file <br>
   ``nano /etc/apache2/sites-available/000-default.conf`` <br>
   <p align="">
        <img src="img/tugas5/6.64.png" alt="Cover Image">
    </p> <br>
    
6. Lakukan rekonfigurasi
    ``sudo dpkg-reconfigure roundcube-core``
   tulis mail.kelompok4.local sesuai nama domain <br>
    >klik ok <br>
      <p align="">
        <img src="img/tugas5/6.65.png" alt="Cover Image">
    </p> <br>

    pilih language <br>
      <p align="">
        <img src="img/tugas5/6.66.png" alt="Cover Image">
    </p> <br>

    pilih reinstall <br>

   <p align="">
        <img src="img/tugas5/6.67.png" alt="Cover Image">
    </p> <br>

    pilih TCP IP <br>
     <p align="">
        <img src="img/tugas5/6.68.png" alt="Cover Image">
    </p> <br>

    pilih localhost <br>
    <p align="">
        <img src="img/tugas5/6.69.png" alt="Cover Image">
    </p> <br>

    port 3306, klik ok <br>
     <p align="">
        <img src="img/tugas5/6.70.png" alt="Cover Image">
    </p> <br>

    pilih mysql_native_password <br>
     <p align="">
        <img src="img/tugas5/6.71.png" alt="Cover Image">
    </p> <br>

    database name default yaitu roundcube@localhost <br>
      <p align="">
        <img src="img/tugas5/6.72.png" alt="Cover Image">
    </p> <br>

    password 123 <br>
   <p align="">
        <img src="img/tugas5/6.73.png" alt="Cover Image">
    </p> <br>

    admin root <br>
      <p align="">
        <img src="img/tugas5/6.74.png" alt="Cover Image">
    </p> <br>

    klik ya untuk restart <br>
   <p align="">
        <img src="img/tugas5/6.75.png" alt="Cover Image">
    </p> <br>

    success restart <br>
       <p align="">
        <img src="img/tugas5/6.76.png" alt="Cover Image">
    </p> <br>

7. Lakukan percobaan untuk mengirim pesan ke user lain.
       <p align="">
        <img src="img/tugas5/reduy.png" alt="Cover Image">
    </p> <br>

    *berhasil terkirim ke user tujuan <br>
        <p align="">
        <img src="img/tugas5/akhir.png" alt="Cover Image">
    </p> <br>


# PRAKTIKUM MENGUNAKAN WEBMAIL DALAM 1 JARINGAN

## SETUP AWAL

Pertama-tama sambungkan komputer dengan kabel ethernet lokal yang tersedia. Setelah tersambung dengan jaringan lokal pastikan IP sesuai dengan kelompok/meja gunakan command `ipconfig/all` pada kasus ini saya mendapatkan IP `192.168.4.1` karena saya merupakan kelompok 4
  <p align="">
        <img src="img/tugas5/awalsetup1.png" alt="Cover Image">
    </p> <br>

Lalu ubah pada setting network pada virtual machine ke Bridged Adapter dan ganti adapter sesuai dengan hasil command `ipconfig/all` yaitu `Realtek PCIe GbE Family Controller`
  <p align="">
        <img src="img/tugas5/awalsetup2.png" alt="Cover Image">
    </p> <br>

## SETUP DEBIAN 12

Jalankan VM anda lalu pergi ke `sudo nano /etc/bind/named.conf.options`
  <p align="">
        <img src="img/tugas5/setup1.png" alt="Cover Image">
    </p> <br>

Rubah konfigurasi forwarders dengan `10.10.10.1` dan `192.168.4.10` ganti IP listen on ke `192.168.4.10` terakhir ganti konfigurasi `allow-query` dan `allow-recursion `ke `any`. Konfigurasinya akan menjadi seperti berikut:

  <p align="">
        <img src="img/tugas5/setup2.png" alt="Cover Image">
    </p> <br>
  <p align="">
        <img src="img/tugas5/setup3.png" alt="Cover Image">
    </p> <br>

Rubah juga konfigurasi di `sudo nano /etc/resolv.conf` tambahkan `nameserver 192.168.4.10` seperti dibawah berikut:

  <p align="">
        <img src="img/tugas5/setup4.png" alt="Cover Image">
    </p> <br>

Setelah itu coba tes ping IP kelompok lain yaitu kelompok 2 dengan command `ping 192.168.2.10` jika konfigurasi network benar maka maka hasilnya akan seperti berikut:
  <p align="">
        <img src="img/tugas5/test1.png" alt="Cover Image">
    </p> <br>

Coba juga tes ping ke sebagai contoh `detik.com` dengan command `ping detik.com` jika konfigurasi network benar maka akan seperti dibawah ini:
  <p align="">
        <img src="img/tugas5/test2.png" alt="Cover Image">
    </p> <br>

Buka browser dan coba test apakah bisa mengakses webmail (roundcube) kelompok lain disini saya mencoba mengakses ke webmail kelompok 2 dengan alamat `mail.kelompok2.local` Jika berhasil maka akan tampil seperti berikut:

  <p align="">
        <img src="img/tugas5/test3.png" alt="Cover Image">
    </p> <br>

Buka browser dan coba test apakah bisa mengakses webmail (roundcube) dengan alamat `mail.kelompok4.local/roundcube` Jika berhasil maka akan tampil seperti berikut:
  <p align="">
        <img src="img/tugas5/test4.png" alt="Cover Image">
    </p> <br>

Jika network static tidak bekerja dan tidak bisa tampil seperti diatas maka coba buka `sudo nano /etc/network/interfaces` buat auto network dengan mengcomment konfigurasi static pada seperti dibawah ini:

  <p align="">
        <img src="img/tugas5/setup5.png" alt="Cover Image">
    </p> <br>

Lalu setup manual IPv4 dengan IP addres `192.168.4.10` netmask `255.255.255.0` gateway `192.168.4.1` dan DNS `10.10.10.1`

  <p align="">
        <img src="img/tugas5/setup6.png" alt="Cover Image">
    </p> <br>


## KONFIGURASI WINBOX

Buka winbox di windows lalu pergi ke menu bridge. Setelah itu remove bridge yang ada dan buat baru. langsung next next saja hingga bertemu setting DNS inputkan `10.10.10.1`

  <p align="">
        <img src="img/tugas5/winbox1.png" alt="Cover Image">
    </p> <br>


## HASIL AKHIR

Login ke rouncube dengan user dan password yang sudah disetup. pada kasus ini saya bisa menerima pesan dari user `iqbal@kelompok6.local` seperti pada gambar dibawah ini:

  <p align="">
        <img src="img/tugas5/hasil1.png" alt="Cover Image">
    </p> <br>
  <p align="">
        <img src="img/tugas5/hasil2.png" alt="Cover Image">
    </p> <br>

Disini saya ingin mencoba mengirim pesan email ke `user@kelompok2.local` dan berhasil
  <p align="">
        <img src="img/tugas5/hasil3.png" alt="Cover Image">
    </p> <br>
