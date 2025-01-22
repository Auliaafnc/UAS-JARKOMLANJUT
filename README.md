## Ujian Akhir Semester Jarkom Lanjut

### Nama: Aulia Fitri Nur Cahyati

### NIM: 20220801148



## Studi Kasus
Buatlah Topologi dan Konfigurasi ruang lab praktikum Universitas Esa Unggul untuk masing masing kampus (CR, KHI, KJ) bagaimana agar mereka bisa terhubung dan terkoneksi dengan memanfaatkan routing statik, routing dinamik (BGP, RIP, OSPF), Kumpulkan semua ke github masing-masing.

## Deskripsi
Proyek ini bertujuan untuk menghubungkan tiga kampus (KJ, CR, dan KHI) menggunakan konfigurasi routing statis dan dinamis melalui jaringan internet dengan dukungan **ISP (Internet Service Provider)**. Untuk menjamin keamanan data selama komunikasi antar kampus, digunakan teknologi **VPN Tunnel** yang menciptakan jalur komunikasi terenkripsi. 
Setiap kampus memerlukan **IP publik** yang disediakan oleh ISP untuk terhubung ke jaringan internet. **ISP** menjadi penghubung utama antar-lokasi, menyediakan koneksi internet untuk ketiga kampus. Mengingat data yang dikirimkan melalui jaringan publik dapat terpapar risiko, digunakan **VPN Tunnel** untuk memastikan keamanan data selama transit. VPN Tunnel akan mengenkripsi data sehingga tetap aman dan privat meskipun melewati jaringan publik yang rentan.

Dengan teknologi ini, komunikasi antar kampus dapat dilakukan dengan aman dan lancar, mendukung berbagai kebutuhan transfer data yang aman.

## Analisis
Konfigurasi jaringan untuk menghubungkan tiga kampus (KJ, CR, dan KHI) menggunakan ISP dan VPN tunnel berhasil menciptakan komunikasi yang aman dan efektif antar lokasi. Setiap router di kampus-kampus tersebut telah dikonfigurasi dengan dua jenis alamat IP, yaitu IP lokal untuk jaringan internal dan IP publik yang diberikan oleh ISP untuk memungkinkan koneksi ke jaringan internet. Penggunaan DHCP dan NAT mempermudah pengelolaan IP lokal secara otomatis, serta memungkinkan perangkat di dalam jaringan lokal untuk mengakses internet dengan aman dan efisien. VPN tunnel berfungsi sebagai saluran aman antara router-router yang terhubung, mengenkripsi data yang melewati jaringan publik untuk melindungi dari potensi ancaman eksternal. Dengan penerapan routing statis, setiap router mengarahkan lalu lintas data ke tujuan yang tepat melalui tunnel yang telah dikonfigurasi, memastikan komunikasi antar kampus berjalan lancar tanpa perlu pengaturan tambahan pada perangkat lain di jaringan lokal. ISP bertindak sebagai penyedia koneksi publik yang menghubungkan kampus-kampus ini, sementara VPN tunnel berperan sebagai lapisan keamanan yang melindungi jalur komunikasi dengan enkripsi data. Secara keseluruhan, konfigurasi ini memberikan solusi yang aman dan efisien untuk menghubungkan kampus-kampus yang terpisah secara fisik, menjaga kelancaran aliran data antara mereka meskipun melalui jaringan publik.





## Implementasi

### 1. **Konfigurasi Dasar pada Setiap Router**
- Setiap router di lokasi KJ, CR, dan KHI dikonfigurasi dengan:
  - **IP lokal** untuk perangkat dalam jaringan internal.
  - **IP publik** dari ISP untuk koneksi antar-lokasi melalui internet.
- Langkah-langkah konfigurasi:
  1. Aktifkan **DHCP server** agar router mendapatkan alamat IP otomatis.
  2. Aktifkan **Network Address Translation (NAT)** untuk menerjemahkan IP lokal ke IP publik, sehingga perangkat internal dapat mengakses internet dengan aman.

Sebagai langkah awal, setiap router yang ditempatkan di lokasi KJ, CR, KHI 
dikonfigurasi dengan pengaturan dasar. Setiap router memiliki 2 jenis alamat IP, yaitu 
IP lokal dan IP publik. IP lokal untuk jaringan internal di masing-masing lokasi, 
digunakan untuk perangkat yang terhubung dalam jaringan lokal dan IP publik 
disediakan oleh ISP, digunakan untuk koneksi internet dan akses antar-lokasi melalui 
tunnel. Setelah itu agar setiap router mendapatkan alamat IP secara otomatis maka 
lakukan DHCP server. Selain itu, Network Address Translation (NAT) diaktifkan untuk 
menerjemahkan IP lokal ke IP publik, memungkinkan perangkat internal mengakses 
internet dengan aman dan efisien. 

### 2. **Pengaturan Tunnel Antar-Lokasi**
- Setiap router membangun tunnel menuju IP publik dari router di lokasi lain:
  - **Kampus KJ** membangun tunnel ke CR dan KHI.
  - **Kampus CR** membangun tunnel ke KJ dan KHI.
  - **Kampus KHI** membangun tunnel ke KJ dan CR.
- Tunnel ini memungkinkan komunikasi langsung antar-kampus melalui ISP dengan perlindungan tambahan berupa enkripsi data.

Selanjutnya adalah melakukann setting tunnel di antara router di ketiga lokasi (KJ, CR, 
KHI) melalui jaringan ISP. Setiap router membuat tunnel yang diarahkan ke IP publik 
yang disediakan ISP di lokasi tujuan. Jadi, router lokasi KJ membangun tunnel menuju 
IP publik yang dimiliki router di lokasi CR dan KHI. Begitu juga sebaliknya, masing
masing router di CR dan KHI membangun tunnel ke router di lokasi lainnya. Dengan 
melakukan konfigurasi tersebut jalur komunikasi langsung dibuat antar-lokasi 
menggunakan ISP sebagai media transportasi, sementara tunnel tersebut memberikan 
keamanan tambahan dengan enkripsi data selama transit. 

### 3. **Routing Statis untuk Pengaturan Lalu Lintas Data**
- Routing statis diterapkan untuk menentukan jalur paket data:
  - Router di KJ mengarahkan data ke CR melalui tunnel menuju IP publik router di CR, begitu pula untuk koneksi ke KHI.
  - Prinsip yang sama diterapkan untuk router di CR dan KHI.
- Dengan konfigurasi ini, perangkat di ketiga kampus dapat saling terhubung tanpa perlu konfigurasi tambahan pada perangkat lokal.

Routing statis ini menentukan jalur yang harus diambil oleh paket data untuk mencapai 
lokasi tujuan. Untuk mengarahkan data dari KJ ke CR, router lokasi KJ akan 
menggunakan rute yang mengarah ke tunnel menuju IP publik router di CR. Begitu pula 
untuk rute ke KHI. Dengan melakukan konfigurasi tersebut, perangkat di lokasi KJ, 
CR, dan KHI dapat berkomunikasi secara langsung tanpa memerlukan konfigurasi 
tambahan di perangkat lain dalam jaringan lokal. 

## Kesimpulan
- **ISP** menyediakan IP publik yang menjadi penghubung utama antar-kampus melalui jaringan publik.
- **VPN Tunnel** berperan penting dalam menciptakan jalur komunikasi yang aman dan terenkripsi meskipun data melewati jaringan publik.

Dalam proyek ini, konfigurasi jaringan untuk menghubungkan tiga kampus (KJ, CR, dan KHI) telah berhasil diterapkan dengan menggunakan teknologi ISP, VPN Tunnel, dan routing statis. ISP bertindak sebagai penyedia IP publik yang menghubungkan ketiga kampus melalui jaringan internet. Penggunaan VPN Tunnel memberikan lapisan keamanan ekstra dengan mengenkripsi data yang dikirimkan antar kampus, melindunginya dari potensi ancaman yang dapat terjadi di jaringan publik. Routing statis digunakan untuk menentukan jalur lalu lintas data, memastikan komunikasi antar kampus berjalan lancar dan efisien tanpa konfigurasi tambahan pada perangkat lokal. Secara keseluruhan, konfigurasi ini memberikan solusi yang aman, efisien, dan handal untuk menghubungkan kampus-kampus yang terpisah secara fisik, menjaga kelancaran aliran data antar kampus meskipun melalui jaringan yang terbuka dan publik.

## Panduan Penggunaan
1. Pastikan setiap router telah dihubungkan ke ISP.
2. Lakukan konfigurasi dasar pada router sesuai panduan di atas.
3. Bangun tunnel antar-lokasi dengan menentukan IP publik tujuan.
4. Atur routing statis untuk memastikan lalu lintas data berjalan sesuai dengan jalur yang ditentukan.

## Teknologi yang Digunakan
- **Router** untuk setiap lokasi (KJ, CR, KHI).
- **ISP** untuk koneksi internet.
- **VPN Tunnel** untuk keamanan data.
- **Routing Statis** untuk pengaturan jalur data.

---
**Catatan:** Pastikan konfigurasi dilakukan dengan cermat untuk menghindari kesalahan koneksi atau kebocoran data.
