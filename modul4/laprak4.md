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

## Langkah Percobaan

### 1. Nslookup
1. Membuka Command Prompt.
2. Menjalankan perintah berikut:


nslookup www.google.com

nslookup -type=NS google.com
nslookup www.yahoo.com
 8.8.8.8


---

### 2. Ipconfig
1. Membuka Command Prompt.
2. Menjalankan:


ipconfig /all
ipconfig /displaydns
ipconfig /flushdns


---

### 3. Tracing DNS dengan Wireshark
1. Menghapus cache DNS dengan perintah:


ipconfig /flushdns


2. Menjalankan Wireshark.
3. Menggunakan filter:


dns


4. Membuka browser dan mengakses:


http://www.ietf.org


5. Menghentikan capture.

---

## Hasil dan Pembahasan

### 1. Nslookup

#### Hasil Percobaan
![nslookup](../assets/image/nslookup.png)

#### Pembahasan
Perintah `nslookup` digunakan untuk mengetahui alamat IP dari suatu domain.

- `nslookup www.google.com` menghasilkan alamat IP dari domain tersebut.
- `nslookup -type=NS google.com` digunakan untuk mengetahui DNS server otoritatif.
- Nslookup bekerja dengan mengirim query ke DNS server dan menerima response berupa alamat IP.

---

### 2. Ipconfig

#### Hasil Percobaan
![ipconfig](../assets/image/ipconfig.png)

#### Pembahasan
Perintah `ipconfig` digunakan untuk melihat konfigurasi jaringan.

- `ipconfig /all` menampilkan informasi lengkap seperti IP Address, DNS server, dan gateway.
- `ipconfig /displaydns` menampilkan cache DNS yang tersimpan.
- `ipconfig /flushdns` digunakan untuk menghapus cache DNS.

Cache DNS digunakan agar akses website lebih cepat tanpa query ulang ke server.

---

### 3. DNS di Wireshark

#### Hasil Capture
![dns wireshark](../assets/image/dns.png)

#### Pembahasan
Pada Wireshark terlihat proses komunikasi DNS antara client dan server.

- Client mengirim DNS Query untuk mencari IP dari domain.
- Server membalas DNS Response berisi alamat IP.
- Protokol yang digunakan adalah UDP (port 53).

DNS bekerja dengan sistem client-server:
- Client meminta informasi
- DNS server memberikan jawaban

---

### 4. Analisis DNS Query & Response

#### Hasil Capture Detail
![dns detail](../assets/image/dns_detail.png)

#### Pembahasan
Dari hasil analisis:

- Query berisi nama domain (contoh: www.ietf.org)
- Response berisi alamat IP domain tersebut
- Terdapat informasi seperti:
  - Transaction ID
  - Flags
  - Questions dan Answers

Hal ini menunjukkan proses translasi domain ke IP address berjalan dengan benar.

---

## Kesimpulan

1. DNS berfungsi untuk menerjemahkan domain menjadi alamat IP.
2. Tools seperti nslookup dan ipconfig membantu dalam analisis DNS.
3. Wireshark dapat digunakan untuk melihat proses query dan response DNS secara detail.
4. Proses DNS umumnya menggunakan protokol UDP pada port 53.