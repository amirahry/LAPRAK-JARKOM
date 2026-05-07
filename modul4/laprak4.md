# LAPORAN PRAKTIKUM MODUL 4 : DNS

## Tujuan Praktikum
1. Mengetahui cara kerja DNS menggunakan Wireshark.
2. Memahami proses translasi nama domain menjadi alamat IP.
3. Menggunakan nslookup dan ipconfig untuk analisis DNS.
4. Mengamati proses DNS request dan DNS response pada jaringan.

---

## Alat dan Bahan
- Wireshark
- Browser
- Command Prompt / PowerShell
- Koneksi internet

---

# Langkah Percobaan

## 1. Nslookup Dasar

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
nslookup www.mit.edu
```

3. Mengamati alamat IP yang diberikan oleh server DNS.

Hasil:

![Nslookup MIT](assets/pengujian-nslookup-mit.png)

Pembahasan:

Pada hasil command prompt terlihat bahwa domain `www.mit.edu` berhasil diterjemahkan menjadi alamat IP oleh DNS server. Hal ini menunjukkan fungsi utama DNS yaitu mengubah nama domain menjadi alamat IP agar dapat dikenali oleh komputer dalam jaringan.

---

## 2. Menampilkan Mail Server Domain

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
nslookup -type=MX ox.ac.uk
```

3. Mengamati mail exchanger yang digunakan domain.

Hasil:

![Pengujian MX Record](assets/nslookup_mx.png)

Pembahasan:

Pada hasil command prompt terlihat mail exchanger dari domain `ox.ac.uk`. Record MX digunakan untuk mengetahui server email yang menangani proses pengiriman dan penerimaan email pada suatu domain.

---

## 3. Pengujian Query Type Tidak Valid

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
nslookup -type=NX ox.ac.uk
```

3. Mengamati hasil query.

Hasil:

![Pengujian query type tidak valid](assets/nslookup_nx.png)

Pembahasan:

Pada percobaan ini digunakan query type `NX` yang sebenarnya tidak valid pada `nslookup`. Sistem menampilkan pesan `unknown query type: NX`, sehingga dapat diketahui bahwa query DNS harus menggunakan tipe yang valid seperti A, MX, NS, atau CNAME.

---

## 4. Menampilkan Konfigurasi IP Dasar

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
ipconfig
```

3. Mengamati konfigurasi jaringan dasar.

Hasil:

![Hasil ipconfig](assets/ipconfig-basic.jpeg)

Pembahasan:

Perintah `ipconfig` digunakan untuk menampilkan konfigurasi IP dasar dari adapter jaringan yang aktif. Informasi yang ditampilkan meliputi IPv4 Address, Subnet Mask, dan Default Gateway.

---

## 5. Menampilkan Seluruh Konfigurasi Jaringan

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
ipconfig /all
```

3. Mengamati informasi jaringan lengkap.

Hasil:

![Hasil ipconfig all](assets/ipconfig-all.jpeg)

Pembahasan:

Perintah `ipconfig /all` digunakan untuk menampilkan seluruh konfigurasi jaringan secara lengkap seperti hostname, MAC Address, DHCP status, IPv4 Address, IPv6 Address, dan konfigurasi adapter jaringan lainnya.

---

## 6. Menghapus DNS Cache

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
ipconfig /flushdns
```

3. Mengamati hasil penghapusan DNS cache.

Hasil:

![Flush DNS](assets/ipconfig-flushdns.jpeg)

Pembahasan:

Perintah `ipconfig /flushdns` digunakan untuk membersihkan DNS Resolver Cache yang tersimpan pada sistem operasi Windows sehingga sistem akan meminta informasi DNS terbaru dari DNS server.

---

## 7. Menampilkan DNS Cache

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
ipconfig /displaydns
```

3. Mengamati daftar DNS cache.

Hasil:

![Display DNS](assets/ipconfig-displaydns.jpeg)

Pembahasan:

Perintah `ipconfig /displaydns` digunakan untuk menampilkan daftar cache DNS yang tersimpan pada komputer. Pada hasil terlihat beberapa domain beserta record DNS yang pernah diakses sebelumnya.

---

## 8. Pengujian Nslookup Domain Telkom University

Langkah percobaan:
1. Membuka Command Prompt / PowerShell.
2. Menjalankan perintah berikut:

```bash
nslookup lms.telkomuniversity.ac.id
```

3. Mengamati alamat IP domain.

Hasil:

![Nslookup Telkom University](assets/nslookup_telkom.png)

Pembahasan:

Pada percobaan ini digunakan perintah `nslookup` untuk mencari alamat IP domain `lms.telkomuniversity.ac.id`. Hasil menunjukkan alamat IPv4 dan IPv6 beserta alias domain yang digunakan.

---

## 9. Tracing DNS Menggunakan Wireshark

Langkah percobaan:
1. Membuka aplikasi Wireshark.
2. Menjalankan capture paket pada interface jaringan yang aktif.
3. Membuka browser dan mengakses website berikut:

```text
http://www.ietf.org
```

4. Menghentikan proses capture.
5. Menggunakan filter:

```bash
dns
```

6. Mengamati paket DNS request dan DNS response.

Hasil:

![DNS Wireshark](assets/dnswireshark.png)

Pembahasan:

Pada hasil capture Wireshark terlihat paket DNS request dan DNS response ketika browser mengakses website `www.ietf.org`.

DNS request dikirim menggunakan protokol UDP menuju port 53 pada DNS server. Setelah itu server memberikan DNS response berupa alamat IP domain tujuan.

---

# Jawaban Pertanyaan

## 1. Apakah DNS menggunakan UDP atau TCP?

DNS umumnya menggunakan protokol UDP karena lebih cepat dan ringan. Namun dalam kondisi tertentu DNS juga dapat menggunakan TCP.

---

## 2. Berapa port tujuan DNS request?

Port tujuan DNS request adalah port 53.

---

## 3. Berapa port sumber DNS response?

Port sumber DNS response adalah port 53.

---

## 4. Apa type DNS request?

Type DNS request yang umum digunakan adalah type A untuk mencari alamat IPv4.

---

## 5. Apakah DNS request memiliki answer?

Tidak. DNS request hanya berisi permintaan informasi domain kepada DNS server.

---

## 6. Apa isi DNS response?

DNS response berisi jawaban dari DNS server berupa alamat IP domain tujuan atau informasi DNS lainnya.

---

## 7. Apakah alamat IP pada TCP SYN sesuai dengan DNS response?

Ya. Alamat IP pada TCP SYN sesuai dengan hasil DNS response karena browser menggunakan alamat IP hasil translasi DNS untuk melakukan koneksi.

---

## 8. Apakah browser selalu mengirim DNS request baru untuk setiap gambar?

Tidak selalu. Browser dapat menggunakan DNS cache yang sudah tersimpan sebelumnya sehingga tidak perlu melakukan DNS request ulang.

---

# Kesimpulan

Berdasarkan praktikum yang telah dilakukan dapat diketahui bahwa DNS berfungsi untuk menerjemahkan nama domain menjadi alamat IP. Dengan menggunakan Wireshark, proses DNS request dan DNS response dapat diamati secara langsung. Selain itu, perintah `nslookup` dan `ipconfig` membantu dalam analisis jaringan dan konfigurasi DNS pada komputer.