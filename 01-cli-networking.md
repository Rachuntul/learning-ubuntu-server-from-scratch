# 📘 01 - Perintah Dasar Linux & Konfigurasi Jaringan

Dokumentasi pembelajaran hari pertama menggunakan Ubuntu Desktop sebagai server harian berbasis CLI dan konfigurasi jaringan dasar.

---

## 🎯 Tujuan Pembelajaran

- Mengenal perintah dasar Linux
- Menavigasi filesystem
- Mengelola file dan folder
- Mengenal struktur direktori Linux
- Mengecek status jaringan
- Memahami dasar `netplan`

---

## 🧪 Perintah-perintah CLI yang Dipelajari

| Perintah | Fungsi |
|----------|--------|
| `pwd` | Menampilkan direktori saat ini |
| `ls -la` | Menampilkan isi direktori secara lengkap |
| `cd` | Berpindah direktori |
| `mkdir` | Membuat folder |
| `touch` | Membuat file kosong |
| `cp`, `mv`, `rm` | Menyalin, memindah, dan menghapus file/folder |
| `nano` | Editor teks berbasis terminal |
| `man` | Manual/help dari suatu perintah |
| `clear` | Membersihkan layar terminal |
| `history` | Menampilkan riwayat perintah |
| `sudo apt update` | Memperbarui indeks paket |
| `sudo apt install` | Menginstal paket aplikasi |

---

## 🗂️ Struktur Direktori Linux (Dasar)

| Direktori | Keterangan |
|----------|------------|
| `/home` | Direktori user |
| `/etc` | File konfigurasi sistem |
| `/var` | File log, data aplikasi |
| `/usr` | Aplikasi dan library tambahan |
| `/bin`, `/sbin` | Perintah sistem |

---

## 🌐 Pemeriksaan Jaringan

```bash
ip a
	***Menampilkan semua interface jaringan, alamat IP, MAC, dll.

```bash
nmcli device status
	***Menampilkan status NetworkManager (Wi-Fi, Ethernet, dsb)

```bash
ping 8.8.8.8
	***Cek koneksi ke internet (Google DNS)

## ⚙️  Dasar Konfigurasi Jaringan dengan Netplan

	***Lokasi file konfigurasi: /etc/netplan/*.yaml

```bash
cd /etc/netplan/
	***Masuk ke direktori netplan

```bash
ls
	***Menunjukkan daftar folder yang ada di netplan

```bash
sudo nano 01-network-manager-all.yaml
	***Membuka 01-network-manager-all.yaml di notepad(nano)
