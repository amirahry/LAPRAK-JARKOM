# LAPORAN TUGAS PRAKTIKUM  
## MODUL 14: 802.11 WiFi (Wireless LAN Analysis)  

---

## 1. Tujuan Praktikum  
1. Mempelajari konsep kerja jaringan WiFi 802.11.  
2. Mengamati beacon frame menggunakan Wireshark.  
3. Memahami struktur SSID dan BSSID.  
4. Menganalisis management frame dan data frame.  
5. Memahami mekanisme komunikasi wireless hingga data transfer.  

---

## 2. Alat dan Bahan  
- Wireshark  
- File capture `Wireshark_802_11.pcap`  
- Laptop / PC  
- Koneksi internet  

---

## 3. Langkah Percobaan  

### 3.1 Membuka File Capture  
File diunduh dari:  
```text
http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
```

File yang digunakan:  
```text
Wireshark_802_11.pcap
```

---

---

### 3.2 Beacon Frame  
Beacon frame adalah frame dari Access Point untuk mengumumkan jaringan WiFi.

---

### Gambar 1 : Beacon Frame  
![Beacon Frame](assets/2.png)

---

### 3.3 SSID dan BSSID  
SSID adalah nama jaringan, BSSID adalah MAC address Access Point.

---

### Gambar 2 : SSID dan BSSID  
![SSID BSSID](assets/3.png)

---

### 3.4 Wireless Management (Fixed Parameters)  
Berisi:  
- Timestamp  
- Beacon Interval  
- Capabilities Info  

---

### Gambar 3 : Wireless Management  
![Wireless Management](assets/4.png)

---

## 4. Tagged Parameters  

### 4.1 SSID & Supported Rates  
SSID dan kecepatan dasar jaringan WiFi.

---

### Gambar 4  
![SSID Rates](assets/5.png)

---

### 4.2 DS, TIM, Country, EDCA  
Channel, QoS, dan informasi power negara.

---

### Gambar 5  
![QoS EDCA](assets/6.png)

---

### 4.3 ERP & Extended Rates  
Dukungan perangkat lama dan kecepatan tambahan.

---

### Gambar 6  
![ERP Extended](assets/7.png)

---

### 4.4 Vendor Specific  
MIMO dan WMM/QoS tambahan.

---

### Gambar 7  
![Vendor](assets/8.png)

---

## 5. Data Frame Analysis  

### 5.1 Filter Data Frame  
```text
ip.addr == 128.119.245.12 && wlan.fc.type == 2
```

---

### Gambar 8  
![Filter](assets/9.png)

---

### 5.2 Packet 466  
QoS Data Frame dengan sequence number 47.

---

### Gambar 9
![Packet 466](assets/10.png)

---

## 6. Association Process  

Tahapan koneksi WiFi:  
Beacon → Probe → Authentication → Association → Data Frame  

---

### Gambar 10  
![Association](assets/11.png)

---

## 7. Kesimpulan  

WiFi 802.11 bekerja melalui beacon frame, authentication, association, hingga data frame. Wireshark digunakan untuk menganalisis seluruh proses komunikasi wireless secara detail.