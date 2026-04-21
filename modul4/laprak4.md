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
2. Menjalankan perintah berikut:


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

Contoh output:

Server: dns.google
Address: 8.8.8.8

Non-authoritative answer:
Name: www.google.com

Address: 142.250.xxx.xxx


#### Pembahasan
Perintah nslookup digunakan untuk mengetahui alamat IP dari suatu domain.

- `nslookup www.google.com` digunakan untuk mendapatkan IP address domain.
- `nslookup -type=NS google.com` digunakan untuk mengetahui DNS server otoritatif.
- `nslookup www.yahoo.com 8.8.8.8` digunakan untuk query ke DNS tertentu.

Non-authoritative answer berarti jawaban berasal dari cache DNS, bukan langsung dari server utama.

---

### 2. Ipconfig

#### Hasil Percobaan
![ipconfig](../assets/image/ipconfig.png)

#### Pembahasan
Perintah ipconfig digunakan untuk melihat konfigurasi jaringan.

- `ipconfig /all` menampilkan IP address, DNS, dan gateway.
- `ipconfig /displaydns` menampilkan cache DNS.
- `ipconfig /flushdns` menghapus cache DNS.

Cache DNS membantu mempercepat akses website.

---

### 3. DNS di Wireshark

#### Hasil Capture
![dns wireshark](../assets/image/dns.png)

#### Pembahasan
Pada Wireshark terlihat komunikasi DNS antara client dan server.

- Client mengirim DNS Query
- Server membalas DNS Response
- Menggunakan protokol UDP port 53

---

### 4. Analisis DNS Query & Response

#### Hasil Capture Detail
![dns detail](../assets/image/dns_detail.png)

#### Pembahasan
Dari hasil analisis:

- Query berisi nama domain
- Response berisi alamat IP
- Terdapat Transaction ID, Flags, Questions, Answers

Menunjukkan proses translasi domain ke IP berjalan dengan baik.

---

## Kesimpulan

1. DNS menerjemahkan domain menjadi IP address.
2. Nslookup dan ipconfig membantu analisis DNS.
3. Wireshark menampilkan proses query dan response DNS.
4. DNS umumnya menggunakan UDP port 53.