## Judul Program

# Simulasi Sistem Harga Produk Online menggunakan Binary Search Tree

# Deskripsi Singkat

Program ini digunakan untuk  sistem penyimpanan harga produk pada toko online menggunakan struktur data Binary Search Tree (BST). Binary Search Tree adalah struktur data berbentuk pohon biner yang menyimpan data secara terurut berdasarkan aturan tertentu.

Pada program ini, setiap harga produk disimpan sebagai sebuah node. Jika harga produk lebih kecil dari node utama, maka harga tersebut akan masuk ke bagian kiri. Jika harga produk lebih besar, maka harga tersebut akan masuk ke bagian kanan. Dengan aturan ini, data harga produk dapat dicari, ditampilkan, dihitung, serta diurutkan dengan lebih mudah.

Program ini memungkinkan pengguna untuk menambahkan harga produk, mencari harga produk tertentu, menampilkan harga dari murah ke mahal, menampilkan traversal preorder dan postorder, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, serta menghitung total semua harga produk yang tersimpan.

Pada Binary Search Tree, operasi pencarian dan penambahan data memiliki kompleksitas waktu rata-rata O(log n) jika bentuk tree seimbang. Namun, pada kondisi terburuk, kompleksitasnya dapat menjadi O(n) apabila tree tidak seimbang.

## Sumber Kode

Image

--

Image

--

Image

--

## Penjelasan Logika Perbaris

**class Node:**

Class ini digunakan untuk membuat sebuah node atau simpul pada Binary Search Tree. Setiap node akan menyimpan satu nilai, yaitu harga produk.

**def __init__(self, key):**

Fungsi ini otomatis dijalankan ketika objek node dibuat. Parameter `key` digunakan untuk menyimpan nilai harga produk.

**self.key = key**

Baris ini menyimpan nilai harga produk ke dalam variabel `key`.

Contohnya jika harga produk adalah `50000`, maka nilai tersebut akan disimpan di dalam node.

**self.left = None**

Baris ini digunakan untuk membuat cabang kiri dari node.

Cabang kiri akan digunakan untuk menyimpan harga produk yang lebih kecil dari node saat ini.

**self.right = None**

Baris ini digunakan untuk membuat cabang kanan dari node.

Cabang kanan akan digunakan untuk menyimpan harga produk yang lebih besar dari node saat ini.

---

**class BSTHargaOnline:**

Class ini digunakan untuk membuat sistem Binary Search Tree yang menyimpan harga produk online. Semua fungsi seperti menambahkan data, mencari data, traversal, mencari nilai minimum, maksimum, menghitung jumlah node, dan menghitung total harga disimpan di dalam class ini.

**def __init__(self):**

Fungsi ini otomatis dijalankan ketika objek BST dibuat.

**self.root = None**

Baris ini membuat root atau akar dari tree.

Nilai awalnya adalah `None`, artinya tree masih kosong dan belum ada harga produk yang dimasukkan.

---

**def insert_node(self, root, key):**

Fungsi ini digunakan untuk memasukkan harga produk baru ke dalam Binary Search Tree.

Parameter `root` digunakan sebagai posisi node yang sedang dicek, sedangkan `key` adalah harga produk yang akan dimasukkan.

**if root is None:**

Baris ini mengecek apakah posisi node masih kosong.

Jika kosong, maka harga produk baru akan dimasukkan di posisi tersebut.

**return Node(key)**

Jika node masih kosong, program akan membuat node baru yang berisi harga produk.

Contohnya jika `key = 50000`, maka program membuat node baru dengan isi harga `50000`.

**if key < root.key:**

Baris ini mengecek apakah harga produk yang dimasukkan lebih kecil dari harga pada node saat ini.

Jika lebih kecil, maka data akan diarahkan ke cabang kiri.

**root.left = self.insert_node(root.left, key)**

Baris ini memasukkan harga produk ke bagian kiri tree.

Misalnya root bernilai `50000`, lalu data baru adalah `25000`, maka `25000` akan masuk ke kiri karena lebih kecil dari `50000`.

**elif key > root.key:**

Baris ini mengecek apakah harga produk yang dimasukkan lebih besar dari harga pada node saat ini.

Jika lebih besar, maka data akan diarahkan ke cabang kanan.

**root.right = self.insert_node(root.right, key)**

Baris ini memasukkan harga produk ke bagian kanan tree.

Misalnya root bernilai `50000`, lalu data baru adalah `75000`, maka `75000` akan masuk ke kanan karena lebih besar dari `50000`.

**return root**

Baris ini mengembalikan root setelah proses penambahan data selesai.

---

**def insert(self, key):**

Fungsi ini digunakan sebagai fungsi utama untuk memasukkan harga produk ke dalam BST.

**self.root = self.insert_node(self.root, key)**

Baris ini memanggil fungsi `insert_node` mulai dari root.

Jika tree masih kosong, harga pertama akan menjadi root. Jika tree sudah berisi data, harga baru akan ditempatkan sesuai aturan BST.

---

**def search_node(self, root, key):**

Fungsi ini digunakan untuk mencari apakah harga produk tertentu ada di dalam tree.

Parameter `root` adalah node yang sedang dicek, sedangkan `key` adalah harga produk yang dicari.

**if root is None:**

Baris ini mengecek apakah node yang diperiksa kosong.

Jika kosong, berarti harga produk tidak ditemukan.

**return False**

Mengembalikan nilai `False` karena harga produk tidak ada di dalam tree.

**if root.key == key:**

Baris ini mengecek apakah harga pada node saat ini sama dengan harga yang dicari.

**return True**

Jika sama, maka harga produk ditemukan dan program mengembalikan nilai `True`.

**if key < root.key:**

Baris ini mengecek apakah harga yang dicari lebih kecil dari harga node saat ini.

Jika lebih kecil, maka pencarian dilanjutkan ke cabang kiri.

**return self.search_node(root.left, key)**

Program mencari harga produk di bagian kiri tree.

**return self.search_node(root.right, key)**

Jika harga yang dicari lebih besar dari node saat ini, maka pencarian dilanjutkan ke cabang kanan.

---

**def search(self, key):**

Fungsi ini digunakan untuk memulai pencarian harga produk dari root.

**return self.search_node(self.root, key)**

Baris ini memanggil fungsi `search_node` dari root tree.

---

**def inorder(self, root):**

Fungsi ini digunakan untuk menampilkan data harga produk dengan urutan dari harga termurah ke harga termahal.

Urutan inorder adalah:

**kiri - root - kanan**

**if root is None:**

Jika node kosong, maka fungsi berhenti.

**return**

Menghentikan fungsi jika tidak ada node yang diproses.

**self.inorder(root.left)**

Program menelusuri cabang kiri terlebih dahulu, karena cabang kiri berisi harga yang lebih kecil.

**print(f"Rp{root.key}", end=" ")**

Program mencetak harga produk pada node saat ini.

**self.inorder(root.right)**

Setelah mencetak root, program melanjutkan ke cabang kanan yang berisi harga lebih besar.

Dengan cara ini, harga produk akan tampil dari murah ke mahal.

---

**def preorder(self, root):**

Fungsi ini digunakan untuk menampilkan data harga produk dengan urutan preorder.

Urutan preorder adalah:

**root - kiri - kanan**

**if root is None:**

Jika node kosong, fungsi berhenti.

**return**

Menghentikan fungsi jika tidak ada node.

**print(f"Rp{root.key}", end=" ")**

Program mencetak harga pada node saat ini terlebih dahulu.

**self.preorder(root.left)**

Setelah root dicetak, program menelusuri cabang kiri.

**self.preorder(root.right)**

Setelah cabang kiri selesai, program menelusuri cabang kanan.

Preorder biasanya digunakan untuk melihat struktur tree dari root terlebih dahulu.

---

**def postorder(self, root):**

Fungsi ini digunakan untuk menampilkan data harga produk dengan urutan postorder.

Urutan postorder adalah:

**kiri - kanan - root**

**if root is None:**

Jika node kosong, fungsi berhenti.

**return**

Menghentikan fungsi jika tidak ada node.

**self.postorder(root.left)**

Program menelusuri cabang kiri terlebih dahulu.

**self.postorder(root.right)**

Setelah kiri selesai, program menelusuri cabang kanan.

**print(f"Rp{root.key}", end=" ")**

Setelah kiri dan kanan selesai, barulah program mencetak harga pada node saat ini.

---

**def find_min(self, root):**

Fungsi ini digunakan untuk mencari harga produk termurah dalam BST.

Pada BST, harga terkecil selalu berada di cabang paling kiri.

**if root is None:**

Baris ini mengecek apakah tree masih kosong.

**return -1**

Jika tree kosong, program mengembalikan nilai `-1` sebagai tanda bahwa tidak ada data harga produk.

**current = root**

Variabel `current` digunakan untuk menelusuri node mulai dari root.

**while current.left is not None:**

Selama masih ada cabang kiri, program akan terus bergerak ke kiri.

**current = current.left**

Program berpindah ke node kiri berikutnya.

**return current.key**

Setelah tidak ada cabang kiri lagi, nilai pada node tersebut adalah harga termurah.

---

**def find_max(self, root):**

Fungsi ini digunakan untuk mencari harga produk termahal dalam BST.

Pada BST, harga terbesar selalu berada di cabang paling kanan.

**if root is None:**

Baris ini mengecek apakah tree masih kosong.

**return -1**

Jika tree kosong, program mengembalikan nilai `-1`.

**current = root**

Variabel `current` digunakan untuk menelusuri node mulai dari root.

**while current.right is not None:**

Selama masih ada cabang kanan, program akan terus bergerak ke kanan.

**current = current.right**

Program berpindah ke node kanan berikutnya.

**return current.key**

Setelah tidak ada cabang kanan lagi, nilai pada node tersebut adalah harga termahal.

---

**def count_nodes(self, root):**

Fungsi ini digunakan untuk menghitung jumlah node dalam tree.

Dalam konteks program ini, jumlah node berarti jumlah harga produk yang tersimpan.

**if root is None:**

Jika node kosong, maka tidak ada data yang dihitung.

**return 0**

Mengembalikan nilai 0 karena node kosong.

**return 1 + self.count_nodes(root.left) + self.count_nodes(root.right)**

Baris ini menghitung satu node saat ini, lalu menambahkan jumlah node di cabang kiri dan cabang kanan.

---

**def sum_nodes(self, root):**

Fungsi ini digunakan untuk menghitung total seluruh harga produk yang tersimpan dalam BST.

**if root is None:**

Jika node kosong, maka tidak ada nilai yang ditambahkan.

**return 0**

Mengembalikan nilai 0 karena node kosong.

**return root.key + self.sum_nodes(root.left) + self.sum_nodes(root.right)**

Baris ini menjumlahkan harga pada node saat ini dengan semua harga di cabang kiri dan cabang kanan.

---

**def main():**

Fungsi utama program. Di dalam fungsi ini, menu program dijalankan.

**bst = BSTHargaOnline()**

Baris ini membuat objek Binary Search Tree dengan nama `bst`.

Objek ini digunakan untuk menyimpan dan mengelola data harga produk online.

**pilih = 0**

Variabel `pilih` digunakan untuk menyimpan pilihan menu dari pengguna.

Nilai awalnya 0 supaya perulangan menu bisa berjalan.

**while pilih != 10:**

Selama pengguna belum memilih menu nomor 10, program akan terus berjalan.

Menu nomor 10 digunakan untuk keluar dari program.

---

**print("\n=== SISTEM HARGA PRODUK ONLINE ===")**

Baris ini menampilkan judul program.

**print("1. Tambah harga produk")**

Menu nomor 1 digunakan untuk memasukkan harga produk baru ke dalam BST.

**print("2. Cari harga produk")**

Menu nomor 2 digunakan untuk mencari apakah harga produk tertentu ada di dalam BST.

**print("3. Tampilkan harga dari murah ke mahal")**

Menu nomor 3 digunakan untuk menampilkan harga produk secara urut dari murah ke mahal menggunakan inorder traversal.

**print("4. Preorder harga produk")**

Menu nomor 4 digunakan untuk menampilkan harga produk dengan preorder traversal.

**print("5. Postorder harga produk")**

Menu nomor 5 digunakan untuk menampilkan harga produk dengan postorder traversal.

**print("6. Cari harga termurah")**

Menu nomor 6 digunakan untuk mencari harga paling kecil dalam BST.

**print("7. Cari harga termahal")**

Menu nomor 7 digunakan untuk mencari harga paling besar dalam BST.

**print("8. Hitung jumlah produk")**

Menu nomor 8 digunakan untuk menghitung jumlah harga produk yang tersimpan.

**print("9. Hitung total semua harga produk")**

Menu nomor 9 digunakan untuk menjumlahkan seluruh harga produk.

**print("10. Keluar")**

Menu nomor 10 digunakan untuk keluar dari program.

---

**try:**

Bagian ini digunakan untuk mencoba menjalankan input dari pengguna.

**pilih = int(input("Pilih menu: "))**

Program meminta pengguna memasukkan pilihan menu, lalu mengubah input menjadi integer.

**except ValueError:**

Bagian ini berjalan jika input tidak valid, misalnya pengguna memasukkan huruf.

**print("Input tidak valid! Masukkan angka menu.")**

Program menampilkan pesan kesalahan input.

**continue**

Program kembali ke awal perulangan menu.

---

**if pilih == 1:**

Jika pengguna memilih menu nomor 1, maka program akan menambahkan harga produk ke dalam BST.

**harga = int(input("Masukkan harga produk: "))**

Program meminta pengguna memasukkan harga produk.

**bst.insert(harga)**

Harga produk dimasukkan ke dalam Binary Search Tree.

**print(f"Harga produk Rp{harga} berhasil dimasukkan.")**

Program menampilkan pesan bahwa harga produk berhasil dimasukkan.

---

**elif pilih == 2:**

Jika pengguna memilih menu nomor 2, maka program akan mencari harga produk tertentu.

**harga = int(input("Masukkan harga produk yang dicari: "))**

Program meminta pengguna memasukkan harga yang ingin dicari.

**if bst.search(harga):**

Program mengecek apakah harga tersebut ada di dalam BST.

**print(f"Harga produk Rp{harga} ditemukan.")**

Jika harga ditemukan, program menampilkan pesan bahwa harga tersebut ada.

**else:**

Jika harga tidak ditemukan, program masuk ke bagian ini.

**print(f"Harga produk Rp{harga} tidak ditemukan.")**

Program menampilkan pesan bahwa harga tersebut tidak ada dalam data.

---

**elif pilih == 3:**

Jika pengguna memilih menu nomor 3, maka program menampilkan harga dari murah ke mahal.

**print("Daftar harga dari murah ke mahal: ", end="")**

Program menampilkan teks awal.

**bst.inorder(bst.root)**

Program menjalankan inorder traversal dari root.

Hasilnya harga tampil dari paling murah sampai paling mahal.

---

**elif pilih == 4:**

Jika pengguna memilih menu nomor 4, maka program menampilkan data secara preorder.

**bst.preorder(bst.root)**

Program menjalankan preorder traversal.

---

**elif pilih == 5:**

Jika pengguna memilih menu nomor 5, maka program menampilkan data secara postorder.

**bst.postorder(bst.root)**

Program menjalankan postorder traversal.

---

**elif pilih == 6:**

Jika pengguna memilih menu nomor 6, maka program mencari harga termurah.

**harga_min = bst.find_min(bst.root)**

Program mencari nilai paling kecil di dalam BST.

**if harga_min == -1:**

Jika hasilnya `-1`, berarti data masih kosong.

**print("Data harga produk masih kosong.")**

Program menampilkan pesan bahwa belum ada harga produk.

**else:**

Jika data ada, program masuk ke bagian ini.

**print(f"Harga produk termurah: Rp{harga_min}")**

Program menampilkan harga produk termurah.

---

**elif pilih == 7:**

Jika pengguna memilih menu nomor 7, maka program mencari harga termahal.

**harga_max = bst.find_max(bst.root)**

Program mencari nilai paling besar dalam BST.

**if harga_max == -1:**

Jika hasilnya `-1`, berarti data masih kosong.

**print("Data harga produk masih kosong.")**

Program menampilkan pesan bahwa belum ada data.

**else:**

Jika data ada, program masuk ke bagian ini.

**print(f"Harga produk termahal: Rp{harga_max}")**

Program menampilkan harga produk termahal.

---

**elif pilih == 8:**

Jika pengguna memilih menu nomor 8, maka program menghitung jumlah produk.

**print(f"Jumlah produk yang tersimpan: {bst.count_nodes(bst.root)}")**

Program menampilkan jumlah node atau jumlah harga produk yang tersimpan dalam BST.

---

**elif pilih == 9:**

Jika pengguna memilih menu nomor 9, maka program menghitung total semua harga produk.

**print(f"Total semua harga produk: Rp{bst.sum_nodes(bst.root)}")**

Program menampilkan hasil penjumlahan seluruh harga produk.

---

**elif pilih == 10:**

Jika pengguna memilih menu nomor 10, maka program berhenti.

**print("Program selesai.")**

Program menampilkan pesan bahwa program telah selesai dijalankan.

---

**else:**

Jika pengguna memasukkan pilihan selain 1 sampai 10, maka bagian ini dijalankan.

**print("Pilihan tidak valid!")**

Program menampilkan pesan bahwa pilihan menu salah.

---

**if __name__ == "__main__":**

Baris ini digunakan untuk mengecek apakah file Python dijalankan secara langsung.

**main()**

Jika file dijalankan langsung, maka fungsi `main()` akan dipanggil dan program mulai berjalan.

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

