
# Tugas 6 Sistem Operasi  
**Compile thread 3, Mencoba Forking, Soal No. 3 & 4 (Referensi Indonesia)**

**Nama:** Ahnaf Hafizh Putra Efendi  
**NRP:** 3124500033  
**Dosen Pengajar:** Dr Ferry Astika Saputra ST, M.Sc  

**PROGRAM STUDI D3 TEKNIK INFORMATIKA**  
**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)**  
**TAHUN 2024**

---

## 1. Compile Thread 3

### Code dan cara menjalankan

```c
#include <stdio.h>
#include <pthread.h>

pthread_cond_t cond1 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond2 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond3 = PTHREAD_COND_INITIALIZER;
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
int done = 1;

void *foo(void *arg) {
    int thread_num = *(int *)arg;
    while (1) {
        pthread_mutex_lock(&lock);
        while (done != thread_num) {
            if (thread_num == 1) {
                pthread_cond_wait(&cond1, &lock);
            } else if (thread_num == 2) {
                pthread_cond_wait(&cond2, &lock);
            } else {
                pthread_cond_wait(&cond3, &lock);
            }
        }
        printf("%d ", thread_num);
        fflush(stdout);

        if (done == 3) {
            done = 1;
            pthread_cond_signal(&cond1);
        } else if (done == 1) {
            done = 2;
            pthread_cond_signal(&cond2);
        } else if (done == 2) {
            done = 3;
            pthread_cond_signal(&cond3);
        }
        pthread_mutex_unlock(&lock);
    }
    return NULL;
}

int main() {
    pthread_t tid1, tid2, tid3;
    int n1 = 1, n2 = 2, n3 = 3;
    pthread_create(&tid1, NULL, foo, &n1);
    pthread_create(&tid2, NULL, foo, &n2);
    pthread_create(&tid3, NULL, foo, &n3);

    pthread_join(tid1, NULL);
    pthread_join(tid2, NULL);
    pthread_join(tid3, NULL);
    return 0;
}
```

### Langkah Menjalankan Code

1. Buka terminal Linux  
2. Ketik `nano print_123.c`  
3. Tempelkan kode di atas ke dalam file  
4. Simpan file (`CTRL + O`, Enter, `CTRL + X`)  
5. Compile dengan: `gcc -pthread print_123.c -o print_123`  
6. Jalankan dengan: `./print_123`

### Output

```
1 2 3 1 2 3 ...
```

(akan terus berjalan sampai ditekan `CTRL + C` maka program akan selesai)

### Analisa Kode


```c
pthread_cond_t cond1 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond2 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond3 = PTHREAD_COND_INITIALIZER;
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
int done = 1;
```

- `done` menyimpan giliran thread mana yang boleh mencetak.
- `cond1`, `cond2`, `cond3` digunakan agar masing-masing thread hanya aktif di gilirannya.
- `lock`: Mutex digunakan untuk memastikan bahwa hanya satu thread yang bisa memeriksa/mengubah `done` pada satu waktu.

```c
void *foo(void *arg)
```

- Fungsi ini dijalankan oleh semua thread.
- `arg` berisi angka 1, 2, atau 3.
- Setiap thread akan menunggu sampai `done == thread_num`, baru mencetak angkanya.

```c
if (done == 3) {
    done = 1;
    pthread_cond_signal(&cond1);
} else if (done == 1) {
    done = 2;
    pthread_cond_signal(&cond2);
} else if (done == 2) {
    done = 3;
    pthread_cond_signal(&cond3);
```

- Setelah mencetak angka, thread mengatur siapa selanjutnya dan mengirim sinyal untuk membangunkan thread berikutnya.


---

## 2. Mencoba Forking

### Pengertian Forking

Forking adalah proses di mana sebuah *parent process* membuat salinan dirinya sendiri (*child process*), menggunakan sistem call `fork()`. Setelah `fork()`, dua proses akan berjalan independen.

### Kode

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();

    if (pid < 0) {
        perror("Fork gagal");
        return 1;
    } else if (pid == 0) {
        printf("Ini adalah proses anak dengan PID %d
", getpid());
    } else {
        printf("Ini adalah proses induk dengan PID %d dan anak dengan PID %d
", getpid(), pid);
    }

    return 0;
}
```

### Penjelasan Kode

1. `pid_t pid = fork();` → menduplikasi proses.
2. `pid < 0` → fork gagal.
3. `pid == 0` → proses anak.
4. `pid > 0` → proses induk.

---

## Soal Nomor 3

**Apakah keuntungan menggunakan time quantum size di level yang berbeda dari sebuah antrian sistem multilevel?**

### Jawaban:

1. **Penyesuaian dengan Karakteristik Proses**
   - Proses interaktif/I/O-bound → time quantum kecil → respon cepat.
   - Proses CPU-bound → time quantum besar → kurangi context switching.

2. **Meningkatkan Efisiensi Sistem**
   - Minimalkan waktu CPU yang terbuang karena switching berlebihan.

3. **Maksimalkan Throughput dan Respons Time**
   - Proses kecil selesai lebih cepat.
   - Proses besar tetap efisien tanpa hambat proses ringan.

4. **Fairness dan Prioritas Dinamis (Multilevel Feedback Queue)**
   - Proses berat bisa "turun level".
   - Proses ringan bisa "naik level" → dapat CPU lebih cepat.

---

## Soal Nomor 4

### Tabel Proses

| Proses | Burst Time | Prioritas |
|--------|------------|-----------|
| P1     | 10         | 3         |
| P2     | 1          | 1         |
| P3     | 2          | 3         |
| P4     | 1          | 4         |
| P5     | 5          | 2         |

---

### FCFS (First Come First Serve)

Asumsi urutan masuk: P1 → P2 → P3 → P4 → P5

**Gantt Chart:**

```
P1 | P2 | P3 | P4 | P5
0   10  11  13  14  19
```

---

### SJF (Shortest Job First – Nonpreemptive)

Urut berdasarkan Burst Time: P2 (1), P4 (1), P3 (2), P5 (5), P1 (10)

**Gantt Chart:**

```
P2 | P4 | P3 | P5 | P1
0    1   2    4    9   19
```

---

### Prioritas Nonpreemptive

Urut berdasarkan prioritas (kecil = lebih tinggi): P2 (1), P5 (2), P1 & P3 (3), P4 (4)  
P1 duluan karena datang lebih awal.

**Gantt Chart:**

```
P2 | P5 | P1 | P3 | P4
0    1    6   16   18  19
```

---

### Round Robin (Quantum = 2)

Awal: P1(10), P2(1), P3(2), P4(1), P5(5)

**Gantt Chart:**

```
P1 | P2 | P3 | P4 | P5 | P1 | P5 | P1 | P5 | P1 | P1
0    2    3    5    6    8   10  12  13  15  17  19
```
