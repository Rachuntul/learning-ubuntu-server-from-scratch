# 🌐 02 - Konfigurasi Static IP dengan Netplan (Wi-Fi)

Dokumentasi hari kedua: Mengatur IP statis untuk koneksi Wi-Fi menggunakan Netplan di Ubuntu Desktop sebagai server lokal.

---

## 🎯 Tujuan Pembelajaran

- Memahami cara kerja Netplan
- Mengatur IP statis untuk Wi-Fi
- Menyimpan dan menerapkan konfigurasi jaringan
- Mengecek hasil konfigurasi

---

## 📁 Lokasi File Konfigurasi

Netplan menyimpan konfigurasi di:

```bash
cd /etc/netplan/

---File yang biasanya digunakan:
01-network-manager-all.yaml



## 🧾 Contoh Konfigurasi Static IP (Wi-Fi)
1. Buka file konfigurasi:
	sudo nano /etc/netplan/01-network-manager-all.yaml

2. Edit isi file seperti contoh di bawah:

network:
  version: 2
  renderer: NetworkManager
  wifis:
    wlan0:
      dhcp4: no
      addresses: [192.168.1.100/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
      access-points:
        "Nama-WiFi":
          password: "PasswordWiFi"

## 🔎 Keterangan:
    -wlan0: Nama interface Wi-Fi kamu (cek dengan ip a)
    -addresses: IP statis yang ingin digunakan
    -gateway4: Gateway router (biasanya IP router)
    -nameservers: DNS resolver
    -access-points: Nama Wi-Fi dan password-nya

3. Simpan dan keluar (Ctrl+O, Enter, lalu Ctrl+X)


## 💾 Menerapkan Konfigurasi
sudo netplan apply

-- Jika gagal, gunakan:
sudo netplan --debug apply

## ✅ Verifikasi Konfigurasi
1. Cek IP address:
ip a

2.Cek koneksi internet:
ping google.com

3.Cek routing:
ip route

