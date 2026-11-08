# PENJELASAN KODE PYTHON
## Penyelesaian Sistem Persamaan Linear 3 Variabel dengan Metode Eliminasi Gauss

**Nama:** Hildegardis Amaral

**NIM:** 202511420091

**Program Studi:** Teknik Informatika

---

## 1. Penjelasan Cell 1 – Import Library

Kode:

```python
import numpy as np

print("PROGRAM PENYELESAIAN SPL 3 VARIABEL")
print("METODE ELIMINASI GAUSS")
print("-----------------------------------")
```

Penjelasan:

- `import numpy as np` digunakan untuk memanggil library NumPy. Library ini membantu melakukan operasi matematika dan pengolahan matriks.
- `print()` digunakan untuk menampilkan judul program.
- Tanda garis digunakan sebagai pemisah agar tampilan program lebih rapi.

## 2. Penjelasan Cell 2 – Memasukkan Matriks

Kode:

```python
A = np.array([
    [4,  2, -2],
    [2,  6,  4],
    [3, -1,  2]
], dtype=float)

B = np.array([5, 35, 10], dtype=float)

matriks_augmented = np.column_stack((A, B))

print("Matriks Augmented:")
print(matriks_augmented)
```

Penjelasan:

- `A` merupakan matriks yang berisi koefisien dari variabel x, y, dan z.
- `B` merupakan matriks konstanta dari setiap persamaan.
- `dtype=float` digunakan agar angka dapat diproses dalam bentuk desimal.
- `np.column_stack((A, B))` menggabungkan matriks koefisien dengan matriks konstanta.
- `print()` menampilkan matriks augmented sebagai bentuk awal perhitungan.

Sistem persamaan yang digunakan adalah:

1. 4x + 2y - 2z = 5
2. 2x + 6y + 4z = 35
3. 3x - y + 2z = 10

## 3. Penjelasan Cell 3 – Proses Eliminasi Gauss

Penjelasan:

- `M = np.column_stack((A.copy(), B.copy()))` membuat matriks augmented untuk proses eliminasi tanpa mengubah matriks awal.
- `n = len(B)` digunakan untuk mengetahui jumlah persamaan atau variabel.
- `for k in range(n - 1)` menjalankan proses eliminasi pada setiap kolom sampai sebelum kolom terakhir.
- `np.argmax(np.abs(M[k:, k]))` mencari posisi nilai absolut terbesar pada kolom yang sedang diproses untuk menentukan pivot.
- `baris_pivot` menyimpan posisi baris yang akan dijadikan pivot.
- `if baris_pivot != k` memeriksa apakah pertukaran baris diperlukan.
- `M[[k, baris_pivot]]` digunakan untuk menukar posisi dua baris.
- `for i in range(k + 1, n)` menjalankan eliminasi pada baris yang berada di bawah pivot.
- `faktor = M[i, k] / M[k, k]` menghitung faktor pengali untuk menghilangkan nilai di bawah pivot.
- `for j in range(k, n + 1)` menjalankan operasi pengurangan pada setiap elemen baris.
- `M[i, j] = M[i, j] - faktor * M[k, j]` merupakan operasi baris elementer untuk menghasilkan nilai nol di bawah pivot.
- `print(M)` menampilkan perubahan matriks setelah setiap tahap eliminasi.

Hasil dari proses ini adalah matriks segitiga atas.

## 4. Penjelasan Cell 4 – Substitusi Mundur

Penjelasan:

- `X = np.zeros(n)` membuat tempat penyimpanan untuk hasil variabel x, y, dan z.
- `for i in range(n - 1, -1, -1)` menjalankan perhitungan dari baris paling bawah menuju baris paling atas.
- `jumlah = 0` digunakan untuk menampung hasil perkalian variabel yang sudah diketahui.
- `for j in range(i + 1, n)` mengambil variabel yang telah dihitung sebelumnya.
- `jumlah += M[i, j] * X[j]` menghitung jumlah perkalian koefisien dengan nilai variabel.
- `X[i] = (M[i, n] - jumlah) / M[i, i]` menghitung nilai variabel berdasarkan hasil substitusi mundur.
- `print()` menampilkan hasil akhir dari setiap variabel.

## 5. Penjelasan Cell 5 – Pemeriksaan Hasil

Penjelasan:

- `np.dot(A, X)` melakukan perkalian matriks koefisien dengan hasil variabel.
- `hasil_pemeriksaan` menyimpan hasil perhitungan ulang ruas kiri persamaan.
- `print()` menampilkan hasil pemeriksaan dan membandingkannya dengan nilai konstanta.
- `np.allclose(hasil_pemeriksaan, B)` memeriksa apakah hasil perhitungan mendekati nilai konstanta dengan toleransi numerik.
- `if` digunakan untuk menentukan apakah solusi sudah memenuhi semua persamaan.
- `else` menampilkan pesan jika hasil belum sesuai.

## 6. Penjelasan Cell 6 – Kesimpulan

Bagian kesimpulan menjelaskan hasil akhir dari program yang telah dibuat.

Nilai yang diperoleh:

- x = 1,75
- y = 2,75
- z = 3,75

Hasil tersebut menunjukkan bahwa metode Eliminasi Gauss dapat digunakan untuk menyelesaikan Sistem Persamaan Linear tiga variabel menggunakan bahasa pemrograman Python.

---

## Kesimpulan Umum

Program ini menggunakan library NumPy untuk membantu proses pengolahan matriks. Penyelesaian dilakukan melalui dua proses utama, yaitu eliminasi baris untuk membentuk matriks segitiga atas dan substitusi mundur untuk mendapatkan nilai setiap variabel.

Hasil perhitungan kemudian diperiksa kembali untuk memastikan bahwa solusi memenuhi sistem persamaan yang diberikan.
