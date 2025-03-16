## 1. Perbedaan Multi Programming dan Multi Tasking

### A. Multi Programming

Multi Programming adalah teknik yang memungkinkan beberapa program dimuat ke dalam memori utama secara bersamaan dan CPU dieksekusi satu per satu. Multi programming memiliki cara kerja ketika satu program menunggu operasi I/O (misalnya membaca dari disk), CPU beralih ke program lain yang siap dieksekusi. Tujuan dari Multi Programming ini meningkatkan pemanfaatan CPU dengan mengurangi waktu idle (menganggur).

**Contoh**: Dalam sistem batch processing, OS memuat beberapa pekerjaan ke memori dan menjalankannya satu per satu.

### B. Multi Tasking

Multi Tasking adalah teknik yang memungkinkan beberapa tugas atau proses dijalankan secara bersamaan dengan berbagi waktu CPU melalui teknik time-sharing. Kemudian untuk cara kerja multi tasking CPU beralih cepat antara proses yang berbeda dalam interval waktu kecil (time slice), memberikan ilusi bahwa semua proses berjalan bersamaan dengan tujuan memberikan pengalaman responsif bagi pengguna dengan menjalankan banyak program secara bersamaan.

**Contoh**: Dalam sistem operasi modern seperti Windows atau Linux, pengguna bisa menjalankan browser, pemutar musik, dan aplikasi lainnya secara bersamaan.

### C. Perbedaan Utama

| Aspek      | Multi Programming                          | Multi Tasking                              |
|------------|--------------------------------------------|--------------------------------------------|
| Pendekatan | Beberapa program dalam memori, CPU memilih satu per satu | CPU bergantian menangani beberapa tugas dalam waktu yang singkat |
| Tujuan     | Meningkatkan pemanfaatan CPU               | Memberikan pengalaman pengguna yang lebih interaktif |
| Metode     | Bergantung pada operasi I/O                | Menggunakan time-sharing                   |
| Contoh OS  | Batch Systems, OS lama                    | Windows, Linux, macOS                      |

Jadi, multiprogramming lebih berfokus pada efisiensi CPU, sedangkan multitasking lebih berfokus pada pengalaman pengguna dan eksekusi simultan beberapa tugas.

---

## 2. Fungsi OS

Sistem operasi memiliki beberapa fungsi utama dalam mengelola sumber daya komputer agar dapat berjalan dengan efisien. Salah satu fungsinya adalah manajemen proses, yang bertugas mengelola eksekusi program yang sedang berjalan. Sistem operasi juga menjadwalkan proses menggunakan berbagai algoritma seperti FCFS, Round Robin, dan Priority Scheduling, serta menangani multitasking, multithreading, dan multiprocessing untuk memastikan pemanfaatan CPU yang optimal.

Selain itu, sistem operasi berperan dalam manajemen memori dengan mengalokasikan dan membebaskan ruang memori untuk proses yang berjalan. Pengelolaan RAM dilakukan dengan teknik seperti paging dan segmentation, serta mendukung memori virtual yang memungkinkan program dengan ukuran lebih besar dari kapasitas RAM tetap dapat dijalankan.

Dalam manajemen perangkat input dan output, sistem operasi mengontrol perangkat seperti keyboard, mouse, dan printer. Komunikasi antara perangkat keras dan perangkat lunak dilakukan melalui driver, sementara buffer dan caching digunakan untuk meningkatkan performa operasi input dan output.

Sistem operasi juga bertanggung jawab dalam manajemen file dengan menyediakan struktur direktori untuk menyimpan dan mengelola file. OS mengontrol akses ke file menggunakan sistem izin seperti read, write, dan execute serta mendukung berbagai sistem file seperti NTFS, FAT32, dan ext4.

Keamanan dan proteksi menjadi aspek penting lainnya yang dikelola oleh sistem operasi. OS melindungi sistem dari akses yang tidak sah melalui mekanisme autentikasi seperti login, password, dan biometrik. Selain itu, izin akses pengguna dan proses dikelola dengan ketat, sementara fitur keamanan seperti firewall dan enkripsi data digunakan untuk mencegah ancaman eksternal.

Dalam manajemen jaringan, sistem operasi memungkinkan komunikasi antar komputer dalam jaringan dengan mengatur protokol seperti TCP/IP, UDP, dan HTTP. Fungsi ini juga mendukung file sharing, remote access, serta koneksi internet yang stabil dan aman.

Sistem operasi menyediakan antarmuka pengguna yang memudahkan interaksi dengan komputer. Beberapa OS menggunakan antarmuka grafis atau GUI seperti Windows, macOS, dan Linux, sedangkan yang lain menyediakan antarmuka berbasis teks atau CLI seperti Linux Terminal dan Command Prompt.

Sebagai kesimpulan, sistem operasi adalah otak dari komputer yang mengatur semua aktivitas perangkat keras dan perangkat lunak agar dapat bekerja dengan efisien dan aman.

---

## 3. Virtualisasi Container

### Pengertian

Virtualisasi container adalah teknologi yang memungkinkan aplikasi dan dependensinya berjalan dalam lingkungan terisolasi yang disebut container. Container berbagi kernel sistem operasi host tetapi tetap memiliki file sistem, pustaka, dan konfigurasi sendiri, sehingga memberikan lingkungan yang konsisten di berbagai sistem tanpa perlu menjalankan OS terpisah seperti dalam virtualisasi berbasis mesin virtual (VM).

Container menggunakan fitur OS seperti cgroups dan namespaces untuk membatasi penggunaan sumber daya serta mengisolasi lingkungan proses agar tidak saling mengganggu. Teknologi ini memberikan keuntungan dalam efisiensi penggunaan sumber daya, kecepatan eksekusi, dan fleksibilitas dalam deployment aplikasi.

### Jenis-Jenis Virtualisasi Container

1. **Container Sistem**
   - Berfungsi seperti mesin virtual ringan dengan lingkungan sistem operasi yang hampir lengkap.
   - Contoh: **LXC (Linux Containers), OpenVZ**

2. **Container Aplikasi**
   - Hanya menjalankan satu aplikasi spesifik dan dependensinya dalam lingkungan yang terisolasi.
   - Contoh: **Docker, Podman**

3. **Container Orkestrasi**
   - Digunakan untuk mengelola banyak container secara otomatis dalam skala besar.
   - Contoh: **Kubernetes, Docker Swarm**

### Perbedaan Virtualisasi Container dengan Virtual Machine

1. **Sistem Operasi** → Container berbagi kernel OS host, sedangkan VM menjalankan OS terpisah di setiap instance.
2. **Konsumsi Sumber Daya** → Container lebih ringan karena tidak memerlukan OS penuh, sementara VM membutuhkan lebih banyak RAM dan CPU.
3. **Kecepatan Eksekusi** → Container berjalan dalam hitungan detik, sedangkan VM memerlukan waktu lebih lama untuk booting.
4. **Isolasi** → VM lebih aman karena setiap instance memiliki OS sendiri, sedangkan container memiliki isolasi terbatas karena berbagi kernel.
5. **Penggunaan** → Container cocok untuk aplikasi berbasis microservices dan deployment cloud, sedangkan VM lebih cocok untuk menjalankan sistem operasi berbeda di satu perangkat keras.

### Keuntungan Virtualisasi Container

1. **Efisiensi Sumber Daya** → Berbagi kernel OS host mengurangi konsumsi RAM dan CPU dibandingkan VM.
2. **Kecepatan Eksekusi** → Container bisa berjalan dalam hitungan detik tanpa proses boot OS.
3. **Portabilitas** → Aplikasi dalam container dapat dijalankan di berbagai lingkungan tanpa masalah dependensi.
4. **Skalabilitas** → Memudahkan pengelolaan dan deployment aplikasi dalam skala besar dengan alat orkestrasi seperti Kubernetes.
5. **Keamanan** → Meskipun berbagi kernel OS, container tetap memiliki isolasi yang cukup kuat untuk membatasi akses antar proses.

### Contoh Penggunaan Virtualisasi Container

1. **Deployment Aplikasi di Cloud** → Banyak platform seperti AWS, Google Cloud, dan Azure mendukung container untuk menjalankan aplikasi berbasis cloud.
2. **CI/CD (Continuous Integration/Continuous Deployment)** → Container memungkinkan pengembangan dan pengujian perangkat lunak lebih cepat dan konsisten di berbagai lingkungan.
3. **Microservices Architecture** → Aplikasi modern sering dikembangkan dengan arsitektur microservices, di mana setiap layanan berjalan dalam container terpisah untuk fleksibilitas dan skalabilitas yang lebih baik.
