# LAPORAN PRAKTIKUM MODUL 11 : DHCP

## Tujuan Praktikum
1. Mahasiswa dapat menginvestigasi cara kerja protokol DHCP menggunakan Wireshark.

---

# 11.1 Pengantar

Pada modul ini dilakukan pengamatan terhadap protokol DHCP (*Dynamic Host Configuration Protocol*) menggunakan aplikasi Wireshark.

DHCP digunakan untuk memberikan alamat IP secara otomatis kepada host serta mengkonfigurasi informasi jaringan lainnya seperti subnet mask, gateway, dan DNS.

Melalui praktikum ini dilakukan proses capture paket DHCP untuk melihat proses komunikasi antara client dan server DHCP.

---

# 11.2 Alat dan Bahan

- Laptop / Komputer  
- Wireshark  
- Command Prompt / Terminal  
- Koneksi Internet  
- Modul DHCP  

---

# 11.3 Mengumpulkan Jejak Paket

DHCP bekerja dengan proses pertukaran paket antara client dan server untuk memperoleh alamat IP.

Pada praktikum ini dilakukan proses capture paket DHCP menggunakan Wireshark.

---

## A. Capture DHCP pada Mac

### Perintah Terminal

```bash
sudo ipconfig set en0 none
```

Perintah tersebut digunakan untuk menghapus konfigurasi IP pada interface jaringan.

---

### Request DHCP

```bash
sudo ipconfig set en0 dhcp
```

Perintah tersebut digunakan agar perangkat meminta alamat IP baru dari server DHCP.

---

## B. Capture DHCP pada Linux

### Menghapus IP Address

```bash
sudo ip addr flush en0
sudo dhclient -r
```

Digunakan untuk menghapus alamat IP pada interface jaringan.

---

### Request DHCP Baru

```bash
sudo dhclient en0
```

Digunakan untuk meminta alamat IP baru dari server DHCP.

---

## C. Capture DHCP pada Windows

### Release IP

```bash
ipconfig /release
```

Digunakan untuk melepaskan alamat IP yang sedang digunakan.

---

### Renew IP

```bash
ipconfig /renew
```

Digunakan untuk meminta alamat IP baru dari server DHCP.

---

# 11.4 Capture DHCP pada Wireshark

![DHCP Wireshark](assets/image/dhcp-wireshark.png)

Pada Wireshark dilakukan filter:

```text
dhcp
```

Filter tersebut digunakan untuk menampilkan paket DHCP saja.

---

# 11.5 Analisis Paket DHCP

Pada hasil capture terlihat beberapa proses komunikasi DHCP yaitu:

- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP ACK

Proses tersebut menunjukkan tahapan perangkat client dalam memperoleh alamat IP dari server DHCP.

---

## A. DHCP Discover

Client mengirim broadcast untuk mencari server DHCP yang tersedia pada jaringan.

---

## B. DHCP Offer

Server DHCP memberikan penawaran alamat IP kepada client.

---

## C. DHCP Request

Client meminta alamat IP yang ditawarkan oleh server DHCP.

---

## D. DHCP ACK

Server DHCP mengonfirmasi bahwa alamat IP berhasil diberikan kepada client.

---

# 11.6 Kesimpulan

Berdasarkan hasil praktikum dapat disimpulkan bahwa DHCP merupakan protokol yang digunakan untuk memberikan alamat IP secara otomatis kepada client pada jaringan komputer.

Melalui Wireshark dapat diamati proses komunikasi DHCP mulai dari Discover, Offer, Request, hingga ACK yang terjadi antara client dan server DHCP.