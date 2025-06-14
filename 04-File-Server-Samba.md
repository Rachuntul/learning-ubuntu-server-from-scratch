🎯 Tujuan Hari Ke-4:
~~Membuat file server lokal menggunakan Samba
~~Bisa share folder ke jaringan lokal, agar bisa diakses dari Windows/Linux lain
~~Mengatur izin akses (permission) agar aman

🧰 Langkah 1: Instal Samba
sudo apt update
sudo apt install samba -y

🗂️ Langkah 2: Buat Folder untuk Dibagikan
#Misalnya kita buat folder bernama share-ubuntu di dalam /srv/share:
sudo mkdir -p /srv/share/ubuntu-share
sudo chown nobody:nogroup /srv/share/ubuntu-share
sudo chmod 0775 /srv/share/ubuntu-share

⚙️ Langkah 3 (edit konfigurasi Samba)
sudo nano /etc/samba/smb.conf
#Tambahkan IP
[global]
   interfaces = 192.168.2.25 lo
   bind interfaces only = yes
#Tambahkan di paling bawah:
[UbuntuShare]
   path = /srv/share/ubuntu-share
   browseable = yes
   read only = no
   guest ok = yes

#Lalu restrat samba
sudo systemctl restart smbd

#Tes mengakses file melalui perangkat lain (contoh melalui android) dengan aplikasi X-Plorer File Manager (Download di PlayStore)
