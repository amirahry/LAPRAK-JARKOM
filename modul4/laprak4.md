## LAPORAN PRAKTIKUM MODUL 4 : DNS

## Tujuan Praktikum
1. Mengetahui cara kerja DNS menggunakan Wireshark.
2. Memahami proses query dan response DNS.
3. Mengamati penggunaan tools nslookup dan ipconfig.

## Alat dan Bahan
- Wireshark
- Command Prompt / Terminal
- Browser
- Koneksi internet

---
## Hasil dan Pembahasan

## 1. Nslookup

Pada praktikum ini digunakan perintah `nslookup` untuk mengetahui informasi DNS seperti alamat IP, DNS server otoritatif, dan mail server suatu domain.

---

### a. Mendapatkan Alamat IP Server Web di Asia

Perintah:

nslookup www.mit.edu


#### Hasil
![nslookup mit](../assets/image/nslookup_mit.png)

#### Pembahasan dan Jawaban
Berdasarkan hasil pada gambar, domain **www.mit.edu** memiliki beberapa alamat IP, yaitu:

- 23.217.163.122  
- 2001:4488:f931:1a3::255e  
- 2001:4488:f931:19e::255e  

Selain itu, terlihat bahwa hasil yang ditampilkan merupakan **Non-authoritative answer**, yang berarti jawaban diperoleh dari cache DNS, bukan langsung dari server otoritatif.

Hal ini menunjukkan bahwa satu domain dapat memiliki lebih dari satu alamat IP untuk meningkatkan performa dan keandalan akses.

---

### b. Mengetahui DNS Server Otoritatif Universitas di Eropa

Perintah:

nslookup -type=NS ox.ac.uk


#### Hasil
![nslookup ns](../assets/image/nslookup_nx.png)

#### Pembahasan dan Jawaban
Berdasarkan hasil pada gambar, query dilakukan ke server DNS:
- tusbind.ac.id (10.217.7.77)

Hasil menunjukkan bahwa domain **ox.ac.uk** memiliki server DNS:

- oxforduni.in.tmes.trendmicro.eu  

Jawaban yang diberikan juga merupakan **Non-authoritative answer**, yang berarti informasi diperoleh dari cache DNS server lokal.

---

### c. Mengetahui Mail Server Yahoo dan Alamat IP

Perintah:

nslookup -type=MX yahoo.com


#### Hasil
![nslookup mx](../assets/image/nslookup_mx.png)

#### Pembahasan dan Jawaban
Berdasarkan hasil pada gambar, domain memiliki mail server:

- oxforduni.in.tmes.trendmicro.eu  

Dengan alamat IP:
- 34.147.168.147  
- 35.242.183.249  
- 35.242.142.110  
- 35.189.126.202  

Hasil juga menunjukkan **Non-authoritative answer**, yang berarti jawaban diperoleh dari cache DNS.

Mail server digunakan untuk menangani pengiriman dan penerimaan email, dan adanya beberapa IP menunjukkan adanya sistem redundansi.

---

### d. Nslookup Domain Lain (Telkom University)

Perintah:

nslookup lms.telkomuniversity.ac.id


#### Hasil
![nslookup telkom](../assets/image/nslookup_telkom.png)

#### Pembahasan
Berdasarkan hasil pada gambar, domain **lms.telkomuniversity.ac.id** memiliki beberapa alamat IP, baik IPv4 maupun IPv6.

Selain itu, terdapat bagian:
- Name: proxy-fallback.celoe.in  
- Aliases: lms.telkomuniversity.ac.id  

Hal ini menunjukkan bahwa domain menggunakan sistem alias (CNAME) dan didistribusikan melalui beberapa server untuk meningkatkan performa dan ketersediaan layanan.

---