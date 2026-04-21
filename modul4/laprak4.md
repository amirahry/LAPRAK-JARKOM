# LAPORAN PRAKTIKUM MODUL 4 : DNS

## Tujuan Praktikum
1. Mengetahui cara kerja DNS menggunakan Wireshark.
2. Memahami proses query dan response DNS.
3. Mengamati penggunaan tools nslookup dan ipconfig.

## Alat dan Bahan
- Wireshark
- Command Prompt / Terminal
- Browser
- Koneksi internet

## Hasil dan Pembahasan
## 1. Nslookup

Pada praktikum ini digunakan perintah `nslookup` untuk mengetahui informasi DNS seperti alamat IP, DNS server otoritatif, dan mail server suatu domain.

---

### a. Mencari Alamat IP Domain

Perintah:

nslookup www.mit.edu


#### Hasil
![nslookup mit](../assets/image/nslookup_mit.png)

#### Pembahasan
Perintah ini digunakan untuk mengetahui alamat IP dari domain **www.mit.edu**.

Alamat IP yang diperoleh:
- 23.217.163.122
- 2001:4488:f931:1a3::255e
- 2001:4488:f931:19e::255e

Hal ini menunjukkan satu domain dapat memiliki beberapa alamat IP karena adanya **load balancing** dan penggunaan **Content Delivery Network (CDN)**.

---

### b. Mengetahui DNS Server Otoritatif

Perintah:

nslookup -type=NS ox.ac.uk


#### Hasil
![nslookup ns](../assets/image/nslookup_ns.png)

#### Pembahasan
Perintah ini digunakan untuk mengetahui DNS server otoritatif dari domain **ox.ac.uk**.

Server DNS:
- oxforduni.in.tmes.trendmicro.eu

DNS server otoritatif merupakan server yang memiliki informasi resmi mengenai suatu domain.

---

### c. Mengetahui Mail Server (MX Record)

Perintah:

nslookup -type=MX ox.ac.uk


#### Hasil
![nslookup mx](../assets/image/nslookup_mx.png)

#### Pembahasan
Perintah ini digunakan untuk mengetahui mail server dari suatu domain.

Mail server:
- oxforduni.in.tmes.trendmicro.eu

Alamat IP:
- 34.147.168.147
- 35.242.183.249
- 35.242.142.110
- 35.189.126.202

Record MX digunakan untuk menentukan server yang menangani layanan email pada suatu domain.

---

### d. Nslookup Domain Lain

Perintah:

nslookup lms.telkomuniversity.ac.id


#### Hasil
![nslookup telkom](../assets/image/nslookup_telkom.png)

#### Pembahasan
Perintah ini digunakan untuk mengetahui alamat IP domain lain sebagai perbandingan.

Hasil menunjukkan bahwa domain tersebut memiliki beberapa alamat IP (IPv4 dan IPv6), yang menandakan adanya distribusi server untuk meningkatkan performa dan keandalan akses.

---