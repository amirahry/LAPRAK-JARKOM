# LAPORAN PRAKTIKUM MODUL 3 : HTTP

## Tujuan Praktikum
1. Mengetahui cara kerja protokol HTTP menggunakan Wireshark.
2. Mengamati proses request dan response antara client dan server.
3. Memahami bagaimana browser mengambil halaman web beserta objek yang ada di dalamnya.

## Alat dan Bahan
- Wireshark
- Browser
- Koneksi internet

---

# Langkah Percobaan

### 1. Basic HTTP GET / Response
1. Membuka aplikasi Wireshark.
2. Menjalankan capture paket pada interface jaringan yang digunakan.
3. Pada kolom filter mengetik `http`.
4. Membuka browser dan mengakses:

```
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
```

5. Setelah halaman terbuka, menghentikan proses capture pada Wireshark.

---

### 2. HTTP Conditional GET
1. Membersihkan cache dan history pada browser.
2. Menjalankan Wireshark dan mulai capture paket.
3. Mengakses halaman berikut:

```
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file2.html
```

4. Melakukan refresh halaman tersebut beberapa kali.
5. Menghentikan capture paket dan menerapkan filter `http`.

---

### 3. Retrieving Long Documents
1. Membersihkan cache browser.
2. Menjalankan Wireshark dan mulai capture paket.
3. Mengakses halaman berikut:

```
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
```

4. Setelah halaman terbuka, menghentikan capture paket.

---

### 4. HTML dengan Embedded Objects
1. Menjalankan Wireshark dan mulai capture paket.
2. Membuka halaman berikut pada browser:

```
http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
```

3. Halaman tersebut menampilkan HTML dengan beberapa gambar.
4. Menghentikan proses capture pada Wireshark.

---

### 5. HTTP Authentication
1. Menjalankan Wireshark dan mulai capture paket.
2. Mengakses halaman berikut:

```
http://gaia.cs.umass.edu/wireshark-labs/protected_pages/HTTP-wireshark-file5.html
```

3. Ketika diminta login, masukkan:

Username : wireshark-students  
Password : network  

4. Setelah halaman berhasil dibuka, hentikan capture paket.

---

# Hasil dan Pembahasan

## 1. Basic HTTP GET

### Tampilan Halaman Web
![Halaman file1](file1.png)

Halaman di atas merupakan file HTML sederhana yang berhasil diakses melalui browser.

### Hasil Capture Wireshark
![Wireshark HTTP 200 OK](http.png)

Pada hasil capture Wireshark terlihat bahwa browser mengirimkan request **HTTP GET** ke server gaia.cs.umass.edu. Server kemudian memberikan respon **HTTP 200 OK** yang menandakan bahwa permintaan berhasil diproses.

---

## 2. Conditional GET

### Tampilan Halaman Web
![Halaman file2](file2.png)

Halaman ini diakses setelah cache browser dibersihkan.

### Hasil Capture Wireshark
![Wireshark Conditional GET](conditional get.png)

Pada Wireshark terlihat bahwa browser mengirim request HTTP kembali ke server. Server kemudian memberikan respon **304 Not Modified** yang berarti file tidak berubah sehingga browser dapat menggunakan file dari cache.

---

## 3. Retrieving Long Documents

### Tampilan Halaman Web
![Halaman file3](file3.png)

Halaman ini berisi dokumen HTML yang cukup panjang yaitu teks mengenai **Bill of Rights**.

### Hasil Capture Wireshark
![Wireshark Retrieving Long](retrieving.png)

Pada Wireshark terlihat bahwa respon HTTP dari server dikirim dalam beberapa paket TCP karena ukuran file yang cukup besar.

---

## 4. HTML dengan Embedded Objects

### Tampilan Halaman Web
![Halaman file4](file4.png)

Halaman ini merupakan file HTML yang memiliki objek tambahan berupa gambar.

### Hasil Capture Wireshark
![Wireshark Embedded Objects](html.png)

Pada Wireshark terlihat beberapa request **HTTP GET** yang dikirim browser untuk mengambil file HTML serta gambar yang terdapat pada halaman tersebut.

---

## 5. HTTP Authentication

### Tampilan Login
![Login Page](file5.png)

Halaman ini meminta username dan password sebelum halaman dapat diakses.

### Hasil Capture Wireshark
![Wireshark Authentication](conditionalget.png)

Pada hasil capture Wireshark terlihat proses autentikasi HTTP dimana browser mengirimkan header **Authorization** yang berisi username dan password yang telah dikodekan menggunakan Base64.

---

# Kesimpulan

Berdasarkan praktikum yang telah dilakukan dapat diketahui bahwa protokol HTTP digunakan untuk komunikasi antara client dan server dalam mengakses halaman web. Dengan menggunakan Wireshark kita dapat melihat secara langsung proses pertukaran paket HTTP seperti request GET, respon dari server, conditional GET, pengambilan dokumen HTML berukuran besar, pengambilan objek tambahan pada halaman web, serta proses autentikasi HTTP.