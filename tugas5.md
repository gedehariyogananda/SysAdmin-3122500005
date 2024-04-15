<h1 align="center">
LAPORAN PRAKTIKUM WORKSHOP

**ADMINISTRASI JARINGAN**
</h1>
<p align="center">
“Setting DNS dan Ekosistem Internet”
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

---
# WEB EMAIL SYSTEM

## NTP Client
1. Lakukan instalasi layanan sinkronisasi waktu

    > apt install systemd-timesyncd <br>
    ![alt text](<img/1.png>)


2. Pastikan konfigurasi timezone ke Asia/Jakarta

    > sudo timedatectl set-timezone Asia/Jakarta

    Melakukan konfigurasi Real Time Clock (RTC) untuk merefer ke UTC (Coordinated Universal Time)

    > sudo timedatectl set-local-rtc false
    
    Mengaktifkan NTP Client untuk sinkronisasi waktu

    > sudo timedatectl set-ntp true <br>

    ![alt text](<img/2.png>)


3. Menyunting file timesyncd.conf untuk mengarah ke NTP server terdekat untuk mendapatkan waktu delay terpendek. Biasanya setiap organisasi atau negara mempunyai NTP Server sendiri

    > sudo nano /etc/systemd/timesyncd.conf <br>
    #Ubahlah line 16 <br>
    [Time] <br>
    NTP=0.id.pool.ntp.org <br>
    ![alt text](<img/3.png>)


4. Restart layanan sinkronisasi waktu dan pastikan layanan berjalan dengan benar

    > sudo systemctl restart systemd-timesyncd <br>
    sudo systemctl status systemd-timesyncd <br>
    ![alt text](<img/4.png>)


5. Lakukan pengecekan kesesuaian tanggal system dengan perintah 

    > sudo timedatectl <br>
    ![alt text](<img/5.png>)

    done


## Apache 2 + PHP-FM
1. Install Apache2

    > sudo apt -y install apache2 <br>
    ![alt text](<img/6.png>)


2. Mengkonfigurasi Apache2 

    > sudo nano /etc/apache2/conf-enabled/security.conf <br>
    #line 12 : change <br>
    ServerTokens Prod <br>
    ![alt text](<img/7.png>)

    > sudo nano /etc/apache2/mods-enabled/dir.conf <br>
    #add file name that it can access only with directory's name <br>
    DirectoryIndex index.html index.htm index.php(untuk membuka file index roundcube) <br>
    ![alt text](<img/8.png>)

    > sudo nano /etc/apache2/apache2.conf <br>
    #line 70 : add to specify server name <br>
    ServerName www.kelompok10.local <br>
    ![alt text](<img/9.png>)

    > sudo nano /etc/apache2/sites-enabled/000-default.conf <br>
    #line 11 : change to webmaster's email <br>
    ServerAdmin webmaster@kelompok10.local <br>
    ![alt text](<img/10.png>)

    > sudo systemctl reload apache2

3. Melakukan test ke web browser <br>

    ![alt text](<img/11.png>)

### Install PHP 8.2

1.  Install dengan perintah berikut
    > apt -y install php8.2 php8.2-mbstring php-pear <br>
    ![alt text](<img/12.png>)

2.  Lakukan pengecekan dan testing apakah sudah berhasil terinstall
    > php -v <br>
    echo '<?php echo `php -i`."\n"; ?>' > php_test.php <br>
    php php_test.php | head <br>
    ![alt text](<img/13.png>)

### Install PHP-FM
1. Install dengan perintah berikut
    > apt -y install php-fpm <br>
    ![alt text](<img/14.png>)

2. Mengkonfigurasi PHP-FM pada file konfigurasi Apache
    > nano /etc/apache2/sites-available/default-ssl.conf <br>
    #add this :<br>
    > <FilesMatch \.php$> <br>
    SetHandler "proxy:unix:/var/run/php/php8.2-fpm.sock|fcgi://localhost/" </FilesMatch> <br>
    ![alt text](<img/15.png>)

    > a2enmod proxy_fcgi setenvif <br>
    ![alt text](<img/16.png>)

    > a2enconf php8.2-fpm <br>
    ![alt text](<img/17.png>)

    > systemctl restart php8.2-fpm apache2

3. Melakukan test validasi terhadap PHP-FM dengan membuat file info.php di root document 

    > echo '<?php phpinfo(); ?>' > /var/www/html/info.php <br>
    ![alt text](<img/18.png>)

4. Lalu lakukan test di browser <br>
    ![alt text](<img/19.png>)

## Database System : MariaDB

1. Lakukan instalasi Maria DB 10.11
    > apt -y install mariadb-server <br>
    ![alt text](<img/20.png>)

    > nano /etc/mysql/mariadb.conf.d/50-server.cnf <br>
    #line 95 : confirm default charset <br>
    #if use 4 bytes UTF-8, specify [utf8mb4] <br>
    character-set-server = utf8mb4 <br>
    collation-server = utf8mb4_general_ci <br>
    ![alt text](<img/21.png>)

    > systemctl restart mariadb

2. Inisial Konfigurasi dan testing database MariaDB Server

    > mysql_secure_installation <br>
    ![alt text](<img/22.png>)
    ![alt text](<img/23.png>)
    ![alt text](<img/24.png>)

    > mysql <br>
    ![alt text](<img/25.png>)
    ![alt text](<img/26.png>)
    ![alt text](<img/27.png>)


## Install Email System POSTFIX : SMTP Server (TCP 25)

1. install dengan perintah berikut
    > apt -y install postfix sasl2-bin <br>
    cp /usr/share/postfix/main.cf.dist /etc/postfix/main.cf <br>
    ![alt text](<img/29.png>)

    > nano /etc/posfix/main.cf <br>
    - #line 82 : uncomment <br> mail_owner = postfix <br>
    ![alt text](<img/30.png>)
    - #line 98 : uncomment and specify hostname <br> myhostname = mail.kelompok10.local <br>
    ![alt text](<img/31.png>)
    - #line 106 : uncomment and specify domainname <br> mydomain = kelompok10.local <br>
    ![alt text](<img/32.png>)
    - #line 127 : uncomment <br>
    myorigin = $mydomain <br>
    ![alt text](<img/33.png>)
    - #line 141 : uncomment <br>
    inet_interfaces = all <br>
    ![alt text](<img/34.png>)
    - #line 189 : uncomment <br>
    mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain <br>
    ![alt text](<img/35.png>)
    - #line 232 : uncomment <br>
    local_recipient_maps = unix:passwd.byname $alias_maps <br>
    ![alt text](<img/36.png>)
    - #line 277 : uncomment <br>
    mynetworks_style = subnet <br>
    - #line 294 : add your local network <br>
    mynetworks = 127.0.0.0/8, 10.0.0.0/24, 192.168.0.0/16 <br>
    ![alt text](<img/37.png>)
    - #line 416 : uncomment <br>
    alias_maps = hash:/etc/aliases
    - #line 427 : uncomment <br>
    alias_database = hash:/etc/aliases <br>
    ![alt text](<img/38.png>)
    - #line 449 : uncomment <br>
    home_mailbox = Maildir/ <br>
    ![alt text](<img/39.png>)
    - #line 585: comment out and add <br>
    #smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU) <br>
    smtpd_banner = $myhostname ESMTP <br>
    ![alt text](<img/40.png>)
    - #line 659 : add <br>
    sendmail_path = /usr/sbin/postfix
    - #line 664 : add <br>
    newaliases_path = /usr/bin/newaliases
    - #line 669 : add <br>
    mailq_path = /usr/bin/mailq
    - #line 675 : add <br>
    setgid_group = postdrop
    - #line 679 : comment out <br>
    #html_directory =
    - #line 683 : comment out<br>
    #manpage_directory = <br>
    ![alt text](<img/41.png>)
    - #line 688 : comment out <br>
    #sample_directory =
    - #line 692 : comment out <br>
    #readme_directory =
    - #line 692 : if also listen IPv6, change to [all] <br>
    inet_protocols = ipv4
    - #add follows to the end <br>
    #disable SMTP VRFY command <br>
    disable_vrfy_command = yes <br>
    #require HELO command to sender hosts <br>
    smtpd_helo_required = yes <br>
    #limit an email size <br>
    #example below means 10M bytes limit <br>
    message_size_limit = 10240000 <br>
    #SMTP-Auth settings <br>
    smtpd_sasl_type = dovecot <br>
    smtpd_sasl_path = private/auth <br>
    smtpd_sasl_auth_enable = yes <br>
    smtpd_sasl_security_options = noanonymous <br>
    smtpd_sasl_local_domain = $myhostname <br>
    smtpd_recipient_restrictions = permit_mynetworks, permit_auth_destination,permit_sasl_authenticated, reject <br>
    ![alt text](<img/42.png>)
    ![alt text](<img/43.png>)
    > newaliases <br>
    systemctl restart postfix <br>
    ![alt text](<img/44.png>)

2. Menambahkan konfigurasi anti spam
    > nano /etc/postfix/main.cf <br>
    #add to the end <br>
    #reject unknown clients that forward lookup and reverse lookup of their hostnames on DNS do
    not match <br>
    smtpd_client_restrictions = permit_mynetworks, reject_unknown_client_hostname, permit <br><br>
    #rejects senders that domain name set in FROM are not registered in DNS or not registered with FQDN <br>
    smtpd_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_non_fqdn_sender <br> <br>
    #reject hosts that domain name set in FROM are not registered in DNS or not registered with FQDN when your SMTP server receives HELO command <br>
    smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, reject_non_fqdn_hostname, reject_invalid_hostname, permit <br>
    ![alt text](<img/45.png>)

    > systemctl restart postfix

## DOVECOT : IMAP4 (TCP 143) and POP3 (TCP110) Server

1. Lakukan instalasi Dovecot Server
    >  apt -y install dovecot-core dovecot-pop3d dovecot-imapd <br>
    ![alt text](<img/46.png>)

    > nano /etc/dovecot/dovecot.conf <br>
    #line 30 : uncomment <br>
    listen = *, :: <br>
    ![alt text](<img/47.png>)

    > nano /etc/dovecot/conf.d/10-auth.conf <br>
    #line 10 : uncomment and change (allow plain text auth) <br>
    disable_plaintext_auth = no <br>
    ![alt text](<img/48.png>)
    #line 100 : add <br>
    auth_mechanisms = plain login <br>
    ![alt text](<img/49.png>)

    > nano /etc/dovecot/conf.d/10-mail.conf <br>
    #line 30 : change to Maildir <br>
    mail_location = maildir:~/Maildir <br>
    ![alt text](<img/50.png>)

    > nano /etc/dovecot/conf.d/10-master.conf <br>
    #line 107-109 : uncomment and add <br>
    #Postfix smtp-auth <br>
    unix_listener /var/spool/postfix/private/auth { <br>
    mode = 0666 <br>
    user = postfix <br>
    group = postfix <br>
    } <br>
    ![alt text](<img/51.png>)

    > systemctl restart dovecot

2. FINAL CHECK untuk semua SERVICES :
    > netstat -a| grep LISTEN <br>
    Akan terlihat hasilnya seperti di bawah, dengan status Server (LISTEN) : MariaDB(MySQL), IMAP,POP3, DNS(domain), IMAPS, POP3S, Postfix (SMTP) <br>
    ![alt text](<img/52.png>)

### Melakukan Cek terhadap Layanan Posfix
```
 telnet mail.kelompok10.local 25
```
![alt text](<img/53.png>)

## Install phpmyadmin
![alt text](<img/54.png>) <br>
lakukan pengecekan melalui www.kelompok10.local/phpmyadmin/ <br>
![alt text](<img/55.png>) <br>
Berhasil terhubung, yang mana artinya database sudah bekerja dengan benar.

## Test Email Menggunakan Thunderbird

1. Install Thunderbird terlebih dahulu
    > apt-get install thunderbird <br>
    ![alt text](<img/56.png>)

2. Membuat user pertama
    ![alt text](<img/58.png>)
    ![alt text](<img/59.png>)

3. Membuat user kedua
    ![alt text](<img/60.png>)
    ![alt text](<img/61.png>)

4. Testing kirim email dari user pertama ke user kedua
    ![alt text](<img/62.png>)
    pesan berhasil terkirim ke user azizah@mail.kelompok10.local <br>
    ![alt text](<img/63.png>)

5. Testing kirim email dari user kedua ke user pertama
    ![alt text](<img/64.png>)
    ![alt text](<img/65.png>)
    Berhasil saling mengirim pesan, yang mana artinya email sistem telah berjalan dengan benar.

## Email Client Menggunakan Web (ROUNDCUBE)

1. Install Roundcube terlebih dahulu
    ![alt text](<img/66.png>)

2. Lakukan config 
    > nano /etc/roundcube/config.inc.php <br>
    ![alt text](<img/67.png>)

3. Lakukan config file apache pada roundcube, uncomment line 3 dan hapus public_html path.
    > nano /etc/rouncube/apache.conf <br>
    ![alt text](<img/68.png>)

4. Lakukan symlink pada folder roundcube ke folder dimana aplikasi ini dionline kan
    ![alt text](<img/83.png>)

5. Tambahkan Servername dan DocumentRoot pada file:
    > nano /etc/apache2/sites-available/000-default.conf <br>
    ![alt text](<img/69.png>)

6. Lakukan rekonfigurasi
    > sudo dpkg-reconfigure roundcube-core
    
    >klik ok <br>
    ![alt text](<img/70.png>)

    >pilih language <br>
    ![alt text](<img/71.png>)

    >klik yes <br>
    ![alt text](<img/72.png>)

    >pilih TCP IP <br>
    ![alt text](<img/73.png>)

    >pilih localhost <br>
    ![alt text](<img/74.png>)

    >port 3306, klik ok <br>
    ![alt text](<img/75.png>)

    >pilih mysql_native_password <br>
    ![alt text](<img/76.png>) 

    >database name default <br>
    ![alt text](<img/77.png>)

    >username default <br>
    ![alt text](<img/78.png>)

    >password 12345 <br>
    ![alt text](<img/79.png>)

    >admin root <br>
    ![alt text](<img/80.png>)

    >pilih apache2 <br>
    ![alt text](<img/81.png>)

    >klik ya untuk restart <br>
    ![alt text](<img/82.png>)

7. Lakukan pengecekan roundcube dengan mengetikkan www.kelompok10.local/
    ![alt text](<img/84.png>)
    Roundcube sudah berhasil terinstall

8. Coba untuk login sebagai user yang telah terdaftar sebelumnya. Di sini saya login sebagai user mayada@mail.kelompok10.local
    ![alt text](<img/85.png>)

9. Lakukan percobaan untuk mengirim pesan ke user lain.
    ![alt text](<img/86.png>)

    >berhasil terkirim ke user tujuan <br>
    ![alt text](<img/87.png>)

10. Lakukan pengecekan pesan masuk pada user kedua azizah@mail.kelompok10.local
    ![alt text](<img/88.png>)
    Pesan berhasil masuk dan diterima oleh user kedua. Roundcube berhasil berjalan dengan baik.
