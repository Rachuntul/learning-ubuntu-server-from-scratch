# 🧪 Hari ke-3: Remote Akses via SSH & Manajemen User

## 📅 Tanggal: 13 Juni 2025  
## 🧑 Oleh: Dion Puji Ramdani

---

## 🎯 Tujuan
- Install dan konfigurasi layanan SSH
- Remote akses Ubuntu dari HP
- Buat user baru & manajemen permission
- Atur IP address agar statis
- Ubah port default SSH ke 25

---

### 1 Instalasi SSH Server
sudo apt update
sudo apt install openssh-server

### 2 Aktifkan SSH agar otomatis jalan saat boot:
sudo systemctl enable ssh
sudo systemctl start ssh

### 3 Cek status SSH:
sudo systemctl status ssh

### 4 Cek Interface & IP Address
ip a
<!--Hasilnya menunjukkan interface Wi-Fi saya bernama wlp3s0-->

### 5 Atur IP Address Menjadi Statis (contoh 192.168.2.25)
sudo nano /etc/netplan/01-network-manager-all.yaml

***Isi konfigurasi:
network:
  version: 2
  renderer: NetworkManager
  wifis:
    wlp2s0:
      dhcp4: no
      addresses:
        - 192.168.2.25/24 <!-- ganti dengan ip address -->
      nameservers:
        addresses:
          - 8.8.8.8
          - 1.1.1.1
      access-points:
        "HERO": <!-- ganti dengan nama wifi -->
          password: "superman" <!-- ganti dengan password wifi -->
      routes:
        - to: default
          via: 192.168.2.1 <!-- ganti dengan ip gateaway -->
### 6 Simpan dan terapkan:
sudo netplan apply

### 7 Verifikasi:
ip a
<!--✅ IP sudah berubah jadi 192.168.2.25 dan tidak berubah saat reboot.-->

### 8 Ganti Port SSH (contoh 25)
sudo nano /etc/ssh/sshd_config
**Temukan baris: #Port 22
**Ubah menjadi: Port 25 <!-- contoh 25 -->

## 9 Simpan dan restart SSH:
sudo systemctl restart ssh

## 10 Cek apakah port aktif:
sudo ss -tuln | grep 25

### 11 Tambah User Baru (siswa1)
sudo adduser siswa1
**Tambahkan ke grup sudo (opsional):
sudo usermod -aG sudo siswa1

### 12 Remote SSH dari HP (contoh Termux)
Aplikasi: Termux (Android)
IP: 192.168.2.25
Port: 25
User: siswa1
Password: [yang dibuat saat adduser]
