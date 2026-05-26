## Judul Program

# Simulasi Sistem Harga Produk Online menggunakan Binary Search Tree

# Deskripsi Singkat

Program ini digunakan untuk  sistem penyimpanan harga produk pada toko online menggunakan struktur data Binary Search Tree (BST). Binary Search Tree adalah struktur data berbentuk pohon biner yang menyimpan data secara terurut berdasarkan aturan tertentu.

Pada program ini, setiap harga produk disimpan sebagai sebuah node. Jika harga produk lebih kecil dari node utama, maka harga tersebut akan masuk ke bagian kiri. Jika harga produk lebih besar, maka harga tersebut akan masuk ke bagian kanan. Dengan aturan ini, data harga produk dapat dicari, ditampilkan, dihitung, serta diurutkan dengan lebih mudah.

Program ini memungkinkan pengguna untuk menambahkan harga produk, mencari harga produk tertentu, menampilkan harga dari murah ke mahal, menampilkan traversal preorder dan postorder, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, serta menghitung total semua harga produk yang tersimpan.

Pada Binary Search Tree, operasi pencarian dan penambahan data memiliki kompleksitas waktu rata-rata O(log n) jika bentuk tree seimbang. Namun, pada kondisi terburuk, kompleksitasnya dapat menjadi O(n) apabila tree tidak seimbang.

## Sumber Kode

<img width="586" height="908" alt="Cuplikan layar 2026-05-26 212751" src="https://github.com/user-attachments/assets/76cc83c3-24eb-4ce8-8adb-4e8d2381ad5f" />
<img width="515" height="878" alt="Cuplikan layar 2026-05-26 212807" src="https://github.com/user-attachments/assets/b3139a75-a14e-402d-84af-38cab5b4e74f" />
<img width="515" height="878" alt="Cuplikan layar 2026-05-26 212807" src="https://github.com/user-attachments/assets/60dd2993-c74a-428d-8a14-aebfcc3c9bfd" />
<img width="761" height="860" alt="Cuplikan layar 2026-05-26 212832" src="https://github.com/user-attachments/assets/4c5cafb8-d3e8-45ab-9d07-53f35fd941db" />
<img width="665" height="204" alt="Cuplikan layar 2026-05-26 212839" src="https://github.com/user-attachments/assets/9a336c74-b301-4258-a57f-31b9dabe5502" />



# Penjelasan Logika Perbaris

**class Node:**



## OUTPUT

Image

--

Image

--

Image

--

## Penjelasan Output

Pada awalnya program menampilkan menu utama:

**SISTEM HARGA PRODUK ONLINE**

1. Tambah harga produk
2. Cari harga produk
3. Tampilkan harga dari murah ke mahal
4. Preorder harga produk
5. Postorder harga produk
6. Cari harga termurah
7. Cari harga termahal
8. Hitung jumlah produk
9. Hitung total semua harga produk
10. Keluar

Bagian ini berarti program meminta pengguna memilih salah satu menu. Pengguna dapat menambahkan harga produk, mencari harga tertentu, menampilkan daftar harga, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, menghitung total harga, atau keluar dari program.

Saat pengguna memilih menu:

**Pilih menu: 1**
**Masukkan harga produk: 50000**

Artinya pengguna memilih menu tambah harga produk. Program lalu memasukkan harga `50000` ke dalam Binary Search Tree. Karena ini adalah data pertama, maka harga `50000` menjadi root atau akar dari tree.

Setelah itu pengguna beberapa kali memilih menu nomor 1 lagi dan memasukkan harga produk:

**25000**
**75000**
**10000**
**30000**
**60000**
**90000**

Artinya ada 7 harga produk yang berhasil dimasukkan ke dalam BST. Susunan tree yang terbentuk adalah:

```text
        50000
       /     \
   25000     75000
   /   \     /   \
10000 30000 60000 90000
```

Harga `50000` menjadi root karena dimasukkan pertama. Harga `25000` masuk ke kiri karena lebih kecil dari `50000`. Harga `75000` masuk ke kanan karena lebih besar dari `50000`. Harga `10000` masuk ke kiri dari `25000`, sedangkan `30000` masuk ke kanan dari `25000`. Harga `60000` masuk ke kiri dari `75000`, sedangkan `90000` masuk ke kanan dari `75000`.

Kemudian pengguna memilih:

**Pilih menu: 3**

Menu nomor 3 digunakan untuk menampilkan harga dari murah ke mahal. Program menjalankan inorder traversal, lalu menampilkan:

```text
Daftar harga dari murah ke mahal: Rp10000 Rp25000 Rp30000 Rp50000 Rp60000 Rp75000 Rp90000
```

Output tersebut menunjukkan bahwa data harga berhasil ditampilkan secara terurut dari harga paling murah sampai harga paling mahal.

Selanjutnya pengguna memilih:

**Pilih menu: 2**
**Masukkan harga produk yang dicari: 30000**

Program akan mencari harga `30000` di dalam BST. Karena harga tersebut ada, maka program menampilkan:

```text
Harga produk Rp30000 ditemukan.
```

Artinya data harga produk tersebut berhasil ditemukan di dalam tree.

Jika pengguna mencari harga yang tidak ada, misalnya:

**Masukkan harga produk yang dicari: 45000**

Maka program akan menampilkan:

```text
Harga produk Rp45000 tidak ditemukan.
```

Artinya harga tersebut belum tersimpan di dalam BST.

Kemudian pengguna memilih:

**Pilih menu: 6**

Menu nomor 6 digunakan untuk mencari harga produk termurah. Program akan bergerak ke cabang paling kiri dari tree. Karena node paling kiri adalah `10000`, maka program menampilkan:

```text
Harga produk termurah: Rp10000
```

Setelah itu pengguna memilih:

**Pilih menu: 7**

Menu nomor 7 digunakan untuk mencari harga produk termahal. Program akan bergerak ke cabang paling kanan dari tree. Karena node paling kanan adalah `90000`, maka program menampilkan:

```text
Harga produk termahal: Rp90000
```

Kemudian pengguna memilih:

**Pilih menu: 8**

Menu nomor 8 digunakan untuk menghitung jumlah produk yang tersimpan. Karena ada 7 harga produk dalam tree, maka program menampilkan:

```text
Jumlah produk yang tersimpan: 7
```

Selanjutnya pengguna memilih:

**Pilih menu: 9**

Menu nomor 9 digunakan untuk menghitung total seluruh harga produk. Dari data:

```text
50000 + 25000 + 75000 + 10000 + 30000 + 60000 + 90000
```

Totalnya adalah:

```text
340000
```

Maka program menampilkan:

```text
Total semua harga produk: Rp340000
```

Terakhir pengguna memilih:

**Pilih menu: 10**

Program menampilkan:

```text
Program selesai.
```

Artinya program berhenti dijalankan.

## Kesimpulan

Program ini menerapkan struktur data Binary Search Tree untuk menyimpan harga produk online secara terstruktur. Harga yang lebih kecil ditempatkan di sebelah kiri node, sedangkan harga yang lebih besar ditempatkan di sebelah kanan node. Dengan menggunakan BST, program dapat menambahkan harga produk, mencari harga tertentu, menampilkan harga secara urut, mencari harga termurah dan termahal, menghitung jumlah produk, serta menghitung total semua harga produk.

Program ini cocok digunakan sebagai contoh sederhana penerapan Binary Search Tree dalam sistem toko online, terutama untuk pengelolaan data harga produk.

