## **A. Pengujian Flops-Iops**

### **1. Buka terminal Linux dan lakukan clone repository flops-iops**
```bash
git clone https://github.com/ferryastika/flops-iops.git
```
Jika tidak bisa maka masuk ke:
```bash
su -
apt install git
sudo apt update && sudo apt install -y build-essential
exit
```

### **2. Masuk ke direktori flops-iops**
```bash
cd flops-iops
```

### **3. Build Program Benchmark**
```bash
make
```

### **4. Jalankan pengujian flops-iops**
#### **a. Jalankan IOPS 32-bit**
```bash
./iops32 $(nproc)
```
**Hasil:**
```
Benchmarking for 32 Bit Integer operations per second
1 Tr 1: 7466128771 Tr 2: 7466481121 IOPS 14932609892
Maximum CPU Throughput: 14.932611 Gigaiops.
Maximum Single Core Throughput: 7.466481 Gigaiops.
```

#### **b. Jalankan IOPS 64-bit**
```bash
./iops64 $(nproc)
```
**Hasil:**
```
Benchmarking for 64 Bit Integer operations per second
1 Tr 1: 7239078522 Tr 2: 7310366180 IOPS = 14549444702
Maximum CPU Throughput: 14.549444 Gigaiops.
Maximum Single Core Throughput: 7.310366 Gigaiops.
```

#### **c. Jalankan FLOPS 32-bit**
```bash
./flops32 $(nproc)
```
**Hasil:**
```
Benchmarking for 32 Bit Floating point operations per second
1 Tr 1: 4695619711 Tr 2: 4694721658 FLOPS = 9390341369
Maximum CPU Throughput: 9.390341 Gigaflops.
Maximum Single Core Throughput: 4.695620 Gigaflops.
Segmentation fault
```

#### **d. Jalankan FLOPS 64-bit**
```bash
./flops64 $(nproc)
```
**Hasil:**
```
Benchmarking for 64 Bit Floating point operations per second
1 Tr 1: 6248587358 Tr 2: 6229297776 FLOPS = 12477885134
Maximum CPU Throughput: 12.477885 Gigaflops.
Maximum Single Core Throughput: 6.248587 Gigaflops.
```

---

## **B. Merangkum Appendix dan Menambahkan Timeline OS**

## 1. Migrasi Fitur
Fitur dari sistem besar (mainframe) diadaptasi ke sistem lebih kecil (microcomputer). Contoh: MULTICS, yang memperkenalkan proteksi berbasis ring dan sistem file hierarkis, memengaruhi UNIX.

## 2. Sistem Awal
- **Sistem Dedikasi**: Programmer juga bertindak sebagai operator.
- **Sistem Berbagi**: Operator profesional mengelola sistem dan mengelompokkan pekerjaan untuk efisiensi.
- **I/O Tumpang Tindih**: Tape magnetik digunakan untuk meningkatkan efisiensi CPU dalam menangani perangkat I/O.

## 3. Atlas (1950-an)
Atlas, dikembangkan di Universitas Manchester, menjadi salah satu sistem operasi pertama yang menerapkan manajemen memori dengan **paging**. Paging memungkinkan sistem untuk menyimpan dan mengambil data dari memori secara lebih efisien. Selain itu, Atlas memperkenalkan konsep **spooling**, yang memungkinkan pekerjaan dijadwalkan berdasarkan ketersediaan perangkat periferal, meningkatkan efisiensi pemrosesan data.

## 4. XDS-940 (1960-an)
Dikembangkan di UC Berkeley, **XDS-940** adalah salah satu sistem pertama yang mendukung **time-sharing**, memungkinkan beberapa pengguna untuk berbagi sumber daya komputer secara bersamaan. Sistem ini juga menggunakan **paging untuk relokasi**, meskipun belum mendukung **demand paging**. Teknologi ini menjadi dasar bagi banyak sistem operasi multitasking modern.

## 5. THE (1960-an)
Sistem operasi **THE**, yang dikembangkan di **Technische Hogeschool Eindhoven**, memperkenalkan **struktur lapisan**, di mana fungsi OS dipisahkan ke dalam beberapa lapisan untuk meningkatkan modularitas dan efisiensi. THE juga menggunakan **semaphore** untuk sinkronisasi antar proses, serta menerapkan **algoritma banker** untuk mencegah deadlock.

## 6. RC 4000 (1960-an)
**RC 4000**, dikembangkan oleh **Per Brinch-Hansen**, memperkenalkan konsep **kernel** sebagai elemen dasar dari OS. Kernel ini memungkinkan pengembang untuk membangun sistem operasi modular dengan fitur yang dapat diperluas. OS ini juga menggunakan **sistem pesan untuk komunikasi antar proses**, yang menjadi fondasi bagi banyak OS modern yang mengutamakan fleksibilitas dan keamanan.

## 7. CTSS (1961)
**CTSS (Compatible Time-Sharing System)** dikembangkan di MIT sebagai salah satu sistem operasi pertama yang mendukung **time-sharing**. Ini memungkinkan beberapa pengguna untuk mengakses komputer secara bersamaan, membagi waktu CPU untuk meningkatkan efisiensi. CTSS juga memperkenalkan **multilevel feedback queue** untuk penjadwalan tugas dan **swapping** untuk pengelolaan memori.

## 8. MULTICS (1965-1970)
**MULTICS (Multiplexed Information and Computing Service)** adalah proyek ambisius dari MIT, GE, dan Bell Labs yang memperkenalkan banyak konsep OS modern, termasuk:
- **Sistem file hierarkis**, yang memungkinkan pengguna mengatur file dalam struktur direktori.
- **Proteksi berbasis ring**, yang meningkatkan keamanan dengan membatasi akses pengguna terhadap sumber daya sistem.

Meskipun MULTICS gagal secara komersial, konsepnya sangat berpengaruh dalam pengembangan UNIX dan OS modern lainnya.

## 9. IBM OS/360 (1960-an)
**OS/360**, dikembangkan oleh **IBM**, adalah salah satu sistem operasi pertama yang dirancang untuk bekerja di berbagai konfigurasi perangkat keras. Namun, kompleksitasnya menyebabkan tantangan dalam pengembangannya, menjadi pelajaran bagi OS di masa depan mengenai pentingnya **modularitas dalam desain OS**.

## 10. TOPS-20 (1970-an)
**TOPS-20**, dikembangkan oleh **Digital Equipment Corporation (DEC)**, adalah OS yang mendukung **manajemen memori virtual** untuk meningkatkan efisiensi penggunaan memori. Dengan fitur **time-sharing**, OS ini memungkinkan banyak pengguna untuk bekerja pada sistem yang sama secara simultan, mempopulerkan konsep **komputasi berbasis jaringan**.

## 11. CP/M dan MS-DOS (1980-an)
- **CP/M (Control Program for Microcomputers)** adalah OS awal yang digunakan dalam komputer mikro, memberikan antarmuka perintah standar bagi banyak perangkat keras yang berbeda.
- **MS-DOS**, dikembangkan oleh **Microsoft** untuk **IBM PC**, menjadi sistem operasi dominan pada 1980-an. Dibandingkan dengan CP/M, MS-DOS memiliki lebih banyak fitur dan kompatibilitas perangkat yang lebih luas, mempercepat adopsi komputer pribadi di seluruh dunia.

## 12. Macintosh Operating System & Windows (1980-an)
- **Mac OS** (dirilis 1984) memperkenalkan **antarmuka grafis pengguna (GUI)** yang revolusioner, menggantikan sistem berbasis teks dengan ikon dan jendela yang lebih intuitif.
- **Windows** (dirilis 1985) membawa konsep GUI ke komputer berbasis IBM PC, menjadikannya standar industri.

Kedua OS ini **memudahkan penggunaan komputer bagi masyarakat luas** dan mendominasi pasar komputer pribadi hingga saat ini.

## 13. Mach (1980-an)
**Mach**, dikembangkan di **Carnegie Mellon University**, adalah **kernel mikro** yang mendukung **multiprosesor dan komunikasi berbasis pesan**. Mach digunakan sebagai basis bagi banyak sistem operasi modern, termasuk **macOS dan NeXTSTEP**.

## 14. Sistem Berbasis Kemampuan (Capability-based Systems)
- **Hydra** memperkenalkan **sistem proteksi berbasis kemampuan** yang memungkinkan pengguna untuk mendefinisikan hak akses mereka sendiri.
- **CAP** adalah OS yang lebih sederhana dibandingkan Hydra tetapi tetap menawarkan **proteksi berbasis kemampuan**, memberikan dasar bagi pengembangan sistem keamanan modern.

## 15. Sistem Lainnya
Beberapa sistem operasi lain yang berpengaruh termasuk:
- **MCP dan SCOPE**, yang dirancang untuk mendukung **multiprosesor** dan memiliki desain yang baik dalam **koordinasi dan sinkronisasi proses**.

## **C. Timeline OS**

#### **1940-1950-an: Era Komputer Awal**
- **Manchester Mark 1 (1949)** – Komputer pertama dengan konsep *stored-program*.
- **GM-NAA I/O (1956)** – Sistem operasi *batch* pertama untuk IBM 704.

#### **1960-an: Time-Sharing dan Multiprogramming**
- **CTSS (1961)** – Sistem *time-sharing* pertama, memungkinkan banyak pengguna berbagi komputer.
- **MULTICS (1965)** – Memperkenalkan sistem file hierarkis dan proteksi berbasis ring, menjadi dasar UNIX.
- **UNIX (1969)** – Dikembangkan di Bell Labs, menjadi dasar banyak OS modern.

#### **1970-an: Minicomputer dan Mikrokomputer**
- **CP/M (1974)** – Sistem operasi untuk komputer mikro, cikal bakal MS-DOS.
- **IBM OS/360 (1970-an)** – Sistem operasi serbaguna untuk komputer *mainframe*.

#### **1980-an: GUI dan Komputasi Personal**
- **MS-DOS (1981)** – Sistem operasi dominan untuk IBM PC.
- **Mac OS (1984)** – Memperkenalkan antarmuka grafis pengguna (GUI).
- **Windows 1.0 (1985)** – Versi pertama Windows dengan GUI berbasis MS-DOS.

#### **1990-an: OS Modern dan Open Source**
- **Windows 95 (1995)** – Memperkenalkan GUI yang lebih maju dan konsep *plug and play*.
- **Linux (1991)** – Sistem operasi open-source berbasis UNIX.

#### **2000-an – Sekarang: OS Mobile dan Cloud**
- **Windows XP (2001)** – OS Windows yang paling populer dan stabil saat itu.
- **macOS X (2001)** – Berbasis UNIX, lebih stabil dibandingkan Mac OS klasik.
- **Android (2008)** – Sistem operasi open-source untuk perangkat mobile.
- **iOS (2007)** – OS eksklusif Apple untuk iPhone dan iPad.
- **Windows 10 (2015)** – OS dengan dukungan jangka panjang dan integrasi cloud.
- **Windows 11 (2021)** – Desain modern dan optimalisasi untuk perangkat terbaru.
