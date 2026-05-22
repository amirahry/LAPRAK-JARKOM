# LAPORAN PRAKTIKUM MODUL 9 : WEB SERVER

## Tujuan Praktikum
1. Mahasiswa dapat memahami implementasi web server sederhana menggunakan Python Socket Programming.

---

# 9.1 Pengantar

Pada modul ini dilakukan implementasi web server sederhana menggunakan bahasa pemrograman Python dan socket programming. Web server digunakan untuk menerima request dari client melalui browser kemudian mengirimkan halaman HTML sebagai response.

Selain itu dilakukan juga pengujian terhadap halaman yang tersedia maupun halaman yang tidak tersedia untuk melihat response `200 OK` dan `404 Not Found`.

---

# 9.2 Alat dan Bahan

- Laptop / Komputer  
- Python  
- Visual Studio Code  
- Browser  
- Terminal / Command Prompt  
- Modul Web Server  

---

# 9.3 Skeleton Kode Python untuk Web Server

## A. Web_server.py

### Kode

![Web Server Python](assets/image/web-server-py.png)

Kode diatas merupakan implementasi kode web server sederhana menggunakan Python Socket.

---

### Output yang didapatkan

![Web Server Output](assets/image/web-server-output.png)

Jika muncul pesan:

```text
The server is ready to receive
```

maka server berhasil dijalankan dan siap digunakan.

---

## B. Web_server.html

### Kode

![Web Server HTML](assets/image/web-server-html.png)

Kemudian membuka alamat URL berikut:

```text
http://localhost:6789/web_server.html
```

---

### Output Website

![Web Server Success](assets/image/web-server-success.png)

Saat website berhasil dipanggil maka browser akan menampilkan isi halaman HTML yang telah dibuat.

---

### Output 404 Not Found

![Web Server 404](assets/image/web-server-404.png)

Ketika mencoba membuka halaman yang tidak tersedia menggunakan:

```text
http://localhost:6789/web.html
```

maka server akan menampilkan pesan:

```text
404 Not Found
```

---

# 9.4 Latihan Tambahan

## A. Server.py

### Kode

![Server Python](assets/image/server-py.png)

---

### Output yang didapatkan

![Server Output](assets/image/server-output.png)

Jika muncul pesan:

```text
The server is ready to receive
```

maka server berhasil dijalankan.

---

## B. Client.py

### Kode

![Client Python](assets/image/client-py.png)

Pastikan seluruh file berada dalam folder yang sama agar program dapat berjalan dengan baik.

---

## C. Web.html

### Kode

![Web HTML](assets/image/web-html.png)

---

## D. Output

### Berhasil

![Client Success](assets/image/client-success.png)

Saat website berhasil dipanggil maka akan menampilkan:

```text
200 OK
```

beserta isi halaman HTML yang diminta.

---

### Error

![Client Error](assets/image/client-error.png)

Pada percobaan kedua muncul pesan:

```text
404 Not Found
```

karena halaman website yang dipanggil tidak tersedia pada server.

---

# Kesimpulan

Berdasarkan hasil praktikum dapat disimpulkan bahwa web server sederhana dapat dibuat menggunakan Python Socket Programming.

Server mampu menerima request dari browser kemudian memberikan response berupa halaman HTML. Selain itu server juga dapat memberikan response error `404 Not Found` ketika halaman yang diminta tidak tersedia.