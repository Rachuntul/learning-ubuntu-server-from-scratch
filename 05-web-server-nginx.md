Instalasi dan Konfigurasi Web Server (Nginx) di Ubuntu 24.04
🎯 Tujuan

Menjadikan Ubuntu Desktop sebagai web server menggunakan Nginx yang dapat diakses melalui browser secara lokal maupun dari jaringan lain.

🔌 Langkah 1: Update & Upgrade Sistem

sudo apt update && sudo apt upgrade -y

🌐 Langkah 2: Instalasi Nginx

sudo apt install nginx -y

✅ Cek status Nginx

sudo systemctl status nginx

🔎 Langkah 3: Uji Web Server

http://localhost
atau
http://<IP-kamu>

🛠️ Langkah 4: Konfigurasi Folder Website

cd /var/www/html

akan ada file index.html atau index.nginx-debian.html
hapus file tersebut dan buat baru:

sudo rm -rf index.html
atau
sudo rm -rf index.nginx-debian.html
sudo rm -rf (nama file.html)

lalu buat baru:
sudo nano index.html

di dalamnya buat teks:
<h1>HELLO WORLD-(Nama)TES WEB SERVER</h1>
lalu simpan: ctrl+x, y, enter

lalu akses lagi:
http://localhost

🌐 Langkah 6: Cek Akses dari Komputer/HP Lain

1. Cek IP Ubuntu Desktop:
ip a
contoh hasil: 192.168.33.195

2. Akses lewat HP di jaringan yang sama:
http://192.168.1.10

