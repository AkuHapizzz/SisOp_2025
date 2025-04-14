
# Tugas 7 Sistem Operasi

**Nama**: Ahnaf Hafizh Putra Efendi  
**NRP**: 3124500033  
**Dosen Pengajar**: Dr Ferry Astika Saputra ST, M.Sc  

## PROGRAM STUDI D3 TEKNIK INFORMATIKA  
**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)**  
**TAHUN 2024**

---

### 1. Jelaskan dalam 2 paragraf disertai dengan gambar tentang konsep single thread dan multithread!

**Single Thread** adalah model eksekusi program di mana hanya ada satu jalur eksekusi (thread) yang berjalan dalam satu waktu. Artinya, CPU hanya memproses satu tugas dalam satu waktu meskipun ada banyak tugas yang menunggu. Model ini sederhana dan lebih mudah diimplementasikan serta di-debug karena tidak ada risiko kondisi balapan (*race conditions*). Namun, kelemahannya adalah tidak dapat memanfaatkan sepenuhnya prosesor multi-core dan kinerjanya bisa rendah saat menangani banyak tugas atau aplikasi interaktif.

**Multithread**, di sisi lain, adalah model di mana sebuah proses dapat memiliki beberapa thread yang berjalan secara bersamaan. Setiap thread dapat menjalankan bagian berbeda dari kode secara paralel. Ini meningkatkan efisiensi, terutama pada sistem multi-core, karena beberapa thread dapat berjalan secara simultan. Multithreading umum digunakan dalam aplikasi modern seperti web browser, game, dan server, di mana responsivitas dan efisiensi sangat penting. Namun, pengelolaan thread yang kompleks dapat menyebabkan masalah seperti *deadlock* dan *race conditions* jika tidak ditangani dengan hati-hati.

**Gambar tentang konsep single thread dan multithread:** 
![Image](https://github.com/user-attachments/assets/d48ea74f-5372-461d-81aa-68857d7a6bbb)


---

## 2. Kerjakan Programming Exercise

### a. Penerapan thread pada contoh di linux `SumTask.java`

**Langkah-langkah:**

1. Cek versi Java:
    ```bash
    java -version
    ```
2. Jika belum ada:
    ```bash
    sudo apt-get update
    sudo apt-cache search openjdk
    sudo apt-get install openjdk-17-jdk
    ```
3. Cek kembali dengan `java -version`.
4. Buat file `SumTask.java`:
    ```bash
    nano SumTask.java
    ```
5. Salin kode dari GitHub:
    [SumTask.java](https://github.com/ferryastika/osc10e/blob/master/ch4/SumTask.java)
6. Kompilasi:
    ```bash
    javac SumTask.java
    ```
7. Jalankan:
    ```bash
    java SumTask
    ```

*Perbedaan hasil terjadi karena penggunaan data acak dalam program.*

---

### b. Penerapan Thread di Linux (`thrd-posix.c`)

**Langkah-langkah:**

1. Cek `gcc`:
    ```bash
    gcc --version
    ```
2. Buat file:
    ```bash
    nano thrd-posix.c
    ```
3. Salin kode dari:
    [thrd-posix.c](https://github.com/ferryastika/osc10e/blob/master/ch4/thrd-posix.c)
4. Kompilasi:
    ```bash
    gcc -pthread thrd-posix.c -o thrd-posix
    ```
5. Jalankan:
    ```bash
    ./thrd-posix 10
    ```

---

### c. Penerapan thread di Windows (`thrd-win32.c`)

**Langkah-langkah:**

1. Buat file `thrd-win32.c` dan salin kode dari:
    [thrd-win32.c](https://github.com/ferryastika/osc10e/blob/master/ch4/thrd-win32.c)
2. Kompilasi:
    ```bash
    gcc thrd-win32.c -o thrd-win32.exe
    ```
3. Jalankan:
    ```bash
    .\thrd-win32.exe 8
    ```

---

## Penjelasan dalam Bentuk Esai

### a. SumTask.java (Java Multithreading)

Program ini adalah implementasi sederhana multithreading menggunakan bahasa Java. Program melakukan penjumlahan angka dalam array yang dibagi ke dua thread. Ini mempercepat eksekusi dan menunjukkan pembagian kerja serta paralelisme.

Java sangat mendukung multithreading melalui `Thread` dan `Runnable`, dan bisa dijalankan di berbagai sistem operasi.

### b. Thread di Linux (`thrd-posix.c`)

Menggunakan pustaka `pthread`, program membuat dua thread yang menjalankan fungsi sederhana. Kompilasi dilakukan dengan `gcc` dan flag `-pthread`.

Menunjukkan bagaimana thread dikelola secara eksplisit di sistem operasi berbasis Unix.

### c. Thread di Windows (`thrd-win32.c`)

Menggunakan API Windows seperti `CreateThread` dan `WaitForSingleObject`. Konsepnya sama dengan Linux, tapi sintaks dan pendekatannya berbeda.

---

## 3. Membuat PPT: Evolusi Teknologi Prosesor Intel

Referensi video: [Intel Processor Evolution - YouTube](https://www.youtube.com/watch?v=PT787d9odKk)

📂 Link Hasil PPT:  
[Google Slides PPT](https://docs.google.com/presentation/d/11Rw4ymkdiD37XrMSDI0ZHBiG6DflW4FV/edit?usp=drive_link&ouid=100329338476453495410&rtpof=true&sd=true)

---

## 4. Mengerjakan Chapter 4 Exercise

### 1. Three Programming Examples where Multithreading is Beneficial

1.	**Photo Thumbnail Generation:** Sebuah aplikasi yang membuat thumbnail dari koleksi gambar dapat menggunakan thread terpisah untuk setiap gambar, sehingga proses pembuatan thumbnail dapat dilakukan secara paralel.
2.	**Web Browser:** Browser web dapat menggunakan satu thread untuk menampilkan gambar atau teks sementara thread lain mengambil data dari jaringan, meningkatkan responsivitas pengguna.
3.	**Word Processor:** Sebuah pengolah kata dapat menggunakan thread terpisah untuk menampilkan grafis, merespons ketukan tombol, dan memeriksa ejaan serta tata bahasa di latar belakang.


### 2. Amdahl’s Law Speedup Calculation

Rumus:
```
Speedup = 1 / (S + (1 - S)/N)
S = 0.4 (serial part)
```

- **2 Cores**: `Speedup = 1 / (0.4 + 0.6/2) = ~1.43`
- **4 Cores**: `Speedup = 1 / (0.4 + 0.6/4) = ~1.82`

### 3. Task or Data Parallelism?

 *Multithreaded web server menunjukkan task parallelism karena setiap thread menangani tugas yang berbeda (misalnya, melayani permintaan klien yang berbeda) secara bersamaan.*.

### 4. User-level Threads vs Kernel-level Threads

| Aspek | User-level Threads | Kernel-level Threads |
|-------|--------------------|----------------------|
| Manajemen | Oleh library user | Oleh OS |
| Pemblokiran | Satu thread blokir = semua blokir | Thread lain tetap berjalan |

**Kapan lebih baik?**

- **User-level**: efisien untuk operasi ringan.
- **Kernel-level**: cocok untuk paralelisme nyata di multi-core.

### 5. Context Switch oleh Kernel

1.	**Simpan Konteks:** Simpan state thread saat ini (register, PC, stack) ke dalam struktur data thread.
2.	**Pilih Thread Baru:** Jadwalkan thread berikutnya yang akan dijalankan.
3.	**Muat Konteks:** Muat state thread baru dari struktur data thread ke register dan PC.
4.	**Lanjutkan Eksekusi:** Lanjutkan eksekusi thread baru.


---

📎 **Referensi kode:**
https://github.com/ferryastika/osc10e/tree/master/ch4
