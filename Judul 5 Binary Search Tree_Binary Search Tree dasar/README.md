## Judul Program

# Simulasi Sistem Harga Produk Online menggunakan Binary Search Tree

# Deskripsi Singkat

Program ini digunakan untuk  sistem penyimpanan harga produk pada toko online menggunakan struktur data Binary Search Tree (BST). Binary Search Tree adalah struktur data berbentuk pohon biner yang menyimpan data secara terurut berdasarkan aturan tertentu.

Pada program ini, setiap harga produk disimpan sebagai sebuah node. Jika harga produk lebih kecil dari node utama, maka harga tersebut akan masuk ke bagian kiri. Jika harga produk lebih besar, maka harga tersebut akan masuk ke bagian kanan. Dengan aturan ini, data harga produk dapat dicari, ditampilkan, dihitung, serta diurutkan dengan lebih mudah.

Program ini memungkinkan pengguna untuk menambahkan harga produk, mencari harga produk tertentu, menampilkan harga dari murah ke mahal, menampilkan traversal preorder dan postorder, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, serta menghitung total semua harga produk yang tersimpan.

Pada Binary Search Tree, operasi pencarian dan penambahan data memiliki kompleksitas waktu rata-rata O(log n) jika bentuk tree seimbang. Namun, pada kondisi terburuk, kompleksitasnya dapat menjadi O(n) apabila tree tidak seimbang.

# Sumber Kode

<img width="586" height="908" alt="Cuplikan layar 2026-05-26 212751" src="https://github.com/user-attachments/assets/76cc83c3-24eb-4ce8-8adb-4e8d2381ad5f" />
<img width="515" height="878" alt="Cuplikan layar 2026-05-26 212807" src="https://github.com/user-attachments/assets/b3139a75-a14e-402d-84af-38cab5b4e74f" />
<img width="515" height="878" alt="Cuplikan layar 2026-05-26 212807" src="https://github.com/user-attachments/assets/60dd2993-c74a-428d-8a14-aebfcc3c9bfd" />
<img width="761" height="860" alt="Cuplikan layar 2026-05-26 212832" src="https://github.com/user-attachments/assets/4c5cafb8-d3e8-45ab-9d07-53f35fd941db" />
<img width="665" height="204" alt="Cuplikan layar 2026-05-26 212839" src="https://github.com/user-attachments/assets/9a336c74-b301-4258-a57f-31b9dabe5502" />



# Penjelasan Logika Perbaris


# Penjelasan Logika Perbaris

# 1. Bagian Class Node

**Class Node =** berfungsi sebagai cetakan untuk membuat node atau simpul pada Binary Search Tree. Setiap node dipakai untuk menyimpan satu nilai harga produk.

**Def `__init__(self, key)` =** berfungsi sebagai konstruktor, yaitu fungsi yang otomatis berjalan saat objek node dibuat. Parameter `key` digunakan untuk menerima nilai harga produk yang akan disimpan.

**`self.key = key` =** berfungsi untuk menyimpan nilai harga produk ke dalam node tersebut.

**`self.left = None` =** berfungsi untuk menyiapkan cabang kiri dari node. Nilainya dibuat `None` karena saat pertama dibuat, node belum memiliki anak kiri.

**`self.right = None` =** berfungsi untuk menyiapkan cabang kanan dari node. Nilainya juga `None` karena node baru belum memiliki anak kanan.

---

### 2. Bagian Class BSTHargaOnline

**Class BSTHargaOnline =** berfungsi sebagai class utama untuk mengatur seluruh proses Binary Search Tree, seperti menambah data, mencari data, menampilkan data, mencari harga minimum, maksimum, menghitung jumlah node, dan menjumlahkan semua harga.

**Def `__init__(self)` =** berfungsi sebagai konstruktor untuk class BSTHargaOnline. Fungsi ini otomatis berjalan saat objek BST dibuat.

**`self.root = None` =** berfungsi untuk membuat root atau akar utama tree. Nilainya `None` karena pada awal program tree masih kosong.

---

### 3. Bagian Fungsi Insert Node

**Def `insert_node(self, root, key)` =** berfungsi untuk memasukkan nilai harga produk ke dalam tree. Fungsi ini bekerja secara rekursif, yaitu memanggil dirinya sendiri sampai menemukan posisi yang tepat.

**`if root is None` =** berfungsi untuk mengecek apakah posisi node yang sedang diperiksa masih kosong.

**`return Node(key)` =** jika posisi kosong, maka program membuat node baru berisi harga produk tersebut.

**`if key < root.key` =** berfungsi untuk mengecek apakah harga yang dimasukkan lebih kecil dari nilai root atau node yang sedang diperiksa.

**`root.left = self.insert_node(root.left, key)` =** jika harga lebih kecil, maka data akan dimasukkan ke cabang kiri. Fungsi akan terus mencari posisi kosong di bagian kiri tree.

**`elif key > root.key` =** berfungsi untuk mengecek apakah harga yang dimasukkan lebih besar dari nilai root atau node yang sedang diperiksa.

**`root.right = self.insert_node(root.right, key)` =** jika harga lebih besar, maka data akan dimasukkan ke cabang kanan. Fungsi akan terus mencari posisi kosong di bagian kanan tree.

**`return root` =** berfungsi untuk mengembalikan root yang sudah diperbarui agar susunan tree tetap tersambung dengan benar.

Catatan: jika harga yang dimasukkan sama dengan harga yang sudah ada, data tidak dimasukkan lagi. Jadi kode ini tidak menyimpan data duplikat. Sistemnya tegas, tidak seperti manusia yang suka masukin data sama berkali-kali lalu bingung sendiri.

---

### 4. Bagian Fungsi Insert

**Def `insert(self, key)` =** berfungsi sebagai fungsi sederhana untuk menambahkan harga produk ke dalam tree.

**`self.root = self.insert_node(self.root, key)` =** berfungsi untuk memulai proses penambahan data dari root. Setelah proses selesai, hasil tree yang baru disimpan kembali ke `self.root`.

---

### 5. Bagian Fungsi Search Node

**Def `search_node(self, root, key)` =** berfungsi untuk mencari apakah suatu harga produk ada di dalam tree.

**`if root is None` =** berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

**`return False` =** jika node kosong, berarti harga yang dicari tidak ditemukan.

**`if root.key == key` =** berfungsi untuk mengecek apakah nilai node saat ini sama dengan harga yang dicari.

**`return True` =** jika nilainya sama, berarti harga ditemukan.

**`if key < root.key` =** berfungsi untuk mengecek apakah harga yang dicari lebih kecil dari nilai node saat ini.

**`return self.search_node(root.left, key)` =** jika lebih kecil, pencarian dilanjutkan ke cabang kiri.

**`return self.search_node(root.right, key)` =** jika harga tidak lebih kecil dan tidak sama, berarti harga lebih besar, maka pencarian dilanjutkan ke cabang kanan.

---

### 6. Bagian Fungsi Search

**Def `search(self, key)` =** berfungsi sebagai fungsi pembungkus untuk mencari harga produk.

**`return self.search_node(self.root, key)` =** berfungsi untuk memulai pencarian dari root dan mengembalikan hasil berupa `True` jika ditemukan atau `False` jika tidak ditemukan.

---

### 7. Bagian Fungsi Inorder

**Def `inorder(self, root)` =** berfungsi untuk menampilkan harga produk secara urut dari yang paling murah ke paling mahal.

**`if root is None` =** berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

**`return` =** jika node kosong, fungsi berhenti dan kembali ke proses sebelumnya.

**`self.inorder(root.left)` =** berfungsi untuk menelusuri cabang kiri terlebih dahulu, karena dalam BST cabang kiri berisi nilai yang lebih kecil.

**`print Rp root.key` =** berfungsi untuk menampilkan nilai harga pada node saat ini dalam format rupiah.

**`end=" "` =** berfungsi agar hasil cetakan tidak langsung pindah baris, tetapi tetap berada dalam satu baris dengan spasi.

**`self.inorder(root.right)` =** berfungsi untuk menelusuri cabang kanan setelah node saat ini ditampilkan.

Logika inorder adalah kiri, root, kanan. Karena itu hasilnya menjadi urut dari murah ke mahal.

---

### 8. Bagian Fungsi Preorder

**Def `preorder(self, root)` =** berfungsi untuk menampilkan data dengan urutan root, kiri, kanan.

**`if root is None` =** berfungsi untuk mengecek apakah node kosong.

**`return` =** jika node kosong, fungsi berhenti.

**`print Rp root.key` =** berfungsi untuk menampilkan nilai node saat ini terlebih dahulu.

**`self.preorder(root.left)` =** berfungsi untuk menelusuri cabang kiri setelah root ditampilkan.

**`self.preorder(root.right)` =** berfungsi untuk menelusuri cabang kanan setelah cabang kiri selesai.

Logika preorder adalah root, kiri, kanan. Biasanya digunakan untuk melihat susunan tree dari bagian paling atas terlebih dahulu.

---

### 9. Bagian Fungsi Postorder

**Def `postorder(self, root)` =** berfungsi untuk menampilkan data dengan urutan kiri, kanan, root.

**`if root is None` =** berfungsi untuk mengecek apakah node kosong.

**`return` =** jika node kosong, fungsi berhenti.

**`self.postorder(root.left)` =** berfungsi untuk menelusuri cabang kiri terlebih dahulu.

**`self.postorder(root.right)` =** berfungsi untuk menelusuri cabang kanan setelah cabang kiri selesai.

**`print Rp root.key` =** berfungsi untuk menampilkan nilai node saat ini setelah cabang kiri dan kanan selesai ditelusuri.

Logika postorder adalah kiri, kanan, root. Jadi root ditampilkan paling akhir.

---

### 10. Bagian Fungsi Find Min

**Def `find_min(self, root)` =** berfungsi untuk mencari harga produk paling murah dalam tree.

**`if root is None` =** berfungsi untuk mengecek apakah tree masih kosong.

**`return -1` =** jika tree kosong, fungsi mengembalikan nilai `-1` sebagai tanda bahwa data tidak tersedia.

**`current = root` =** berfungsi untuk membuat variabel penunjuk sementara yang dimulai dari root.

**`while current.left is not None` =** berfungsi untuk terus mengecek apakah masih ada node di sebelah kiri.

**`current = current.left` =** jika masih ada cabang kiri, maka penunjuk berpindah ke node kiri berikutnya.

**`return current.key` =** jika sudah tidak ada cabang kiri, maka node saat ini adalah nilai paling kecil, lalu nilainya dikembalikan.

Dalam BST, harga paling murah selalu berada di node paling kiri. Ini konsep dasarnya, bukan hasil nebak-nebak kayak jawaban ujian pas belum belajar.

---

### 11. Bagian Fungsi Find Max

**Def `find_max(self, root)` =** berfungsi untuk mencari harga produk paling mahal dalam tree.

**`if root is None` =** berfungsi untuk mengecek apakah tree kosong.

**`return -1` =** jika tree kosong, fungsi mengembalikan nilai `-1` sebagai tanda data belum ada.

**`current = root` =** berfungsi untuk membuat penunjuk sementara yang dimulai dari root.

**`while current.right is not None` =** berfungsi untuk terus mengecek apakah masih ada node di sebelah kanan.

**`current = current.right` =** jika masih ada cabang kanan, maka penunjuk berpindah ke node kanan berikutnya.

**`return current.key` =** jika sudah tidak ada cabang kanan, maka node saat ini adalah nilai terbesar, lalu nilainya dikembalikan.

Dalam BST, harga paling mahal selalu berada di node paling kanan.

---

### 12. Bagian Fungsi Count Nodes

**Def `count_nodes(self, root)` =** berfungsi untuk menghitung jumlah node atau jumlah harga produk yang tersimpan dalam tree.

**`if root is None` =** berfungsi untuk mengecek apakah node kosong.

**`return 0` =** jika node kosong, maka jumlah node dianggap nol.

**`return 1 + count kiri + count kanan` =** berfungsi untuk menghitung satu node saat ini, lalu menambahkan jumlah node di cabang kiri dan cabang kanan.

Artinya, setiap node dihitung satu per satu sampai semua node dalam tree selesai dihitung.

---

### 13. Bagian Fungsi Sum Nodes

**Def `sum_nodes(self, root)` =** berfungsi untuk menghitung total seluruh harga produk yang tersimpan dalam tree.

**`if root is None` =** berfungsi untuk mengecek apakah node kosong.

**`return 0` =** jika node kosong, maka nilainya dianggap nol agar tidak memengaruhi hasil penjumlahan.

**`return root.key + jumlah kiri + jumlah kanan` =** berfungsi untuk menjumlahkan nilai harga pada node saat ini dengan semua nilai harga di cabang kiri dan cabang kanan.

Contohnya, jika harga yang tersimpan adalah 10000, 20000, dan 30000, maka hasil totalnya adalah 60000.

---

## 14. Bagian Fungsi Main

**Def `main()` =** berfungsi sebagai fungsi utama yang menjalankan program.

**`bst = BSTHargaOnline()` =** berfungsi untuk membuat objek BST dari class `BSTHargaOnline`. Objek ini dipakai untuk menyimpan dan mengelola seluruh data harga produk.

**`pilih = 0` =** berfungsi untuk memberi nilai awal pada variabel pilihan menu.

**`while pilih != 10` =** berfungsi untuk membuat program terus berjalan selama pengguna belum memilih menu keluar, yaitu nomor 10.

---

## 15. Bagian Tampilan Menu

**Print judul sistem =** berfungsi untuk menampilkan nama program, yaitu sistem harga produk online.

**Print menu 1 =** berfungsi untuk menampilkan pilihan menambah harga produk.

**Print menu 2 =** berfungsi untuk menampilkan pilihan mencari harga produk.

**Print menu 3 =** berfungsi untuk menampilkan pilihan menampilkan harga dari murah ke mahal.

**Print menu 4 =** berfungsi untuk menampilkan pilihan traversal preorder.

**Print menu 5 =** berfungsi untuk menampilkan pilihan traversal postorder.

**Print menu 6 =** berfungsi untuk menampilkan pilihan mencari harga termurah.

**Print menu 7 =** berfungsi untuk menampilkan pilihan mencari harga termahal.

**Print menu 8 =** berfungsi untuk menampilkan pilihan menghitung jumlah produk yang tersimpan.

**Print menu 9 =** berfungsi untuk menampilkan pilihan menghitung total semua harga produk.

**Print menu 10 =** berfungsi untuk menampilkan pilihan keluar dari program.

---

## 16. Bagian Input Pilihan Menu

**`try` =** berfungsi untuk mencoba menjalankan input pilihan menu dan mencegah program langsung error jika input salah.

**Input pilihan menu =** berfungsi untuk meminta pengguna memasukkan angka menu.

**`int(input(...))` =** berfungsi untuk mengubah input pengguna menjadi angka integer.

**`except ValueError` =** berfungsi untuk menangani error jika pengguna memasukkan input yang bukan angka.

**Print input tidak valid =** berfungsi untuk memberi tahu bahwa input harus berupa angka.

**`continue` =** berfungsi untuk mengulang program kembali ke tampilan menu tanpa menjalankan proses menu lain.

---

## 17. Bagian Menu 1: Tambah Harga Produk

**`if pilih == 1` =** berfungsi untuk mengecek apakah pengguna memilih menu tambah harga produk.

**`try` =** berfungsi untuk menangani kemungkinan input harga yang salah.

**Input harga produk =** berfungsi untuk meminta pengguna memasukkan harga produk.

**`int(input(...))` =** berfungsi untuk mengubah input harga menjadi angka integer.

**`bst.insert(harga)` =** berfungsi untuk memasukkan harga tersebut ke dalam Binary Search Tree.

**Print harga berhasil dimasukkan =** berfungsi untuk menampilkan pesan bahwa harga produk sudah berhasil disimpan.

**`except ValueError` =** berfungsi untuk menangani jika harga yang dimasukkan bukan angka.

**Print harga harus berupa angka =** berfungsi untuk memberi tahu pengguna bahwa input harga tidak boleh berupa huruf atau simbol.

---

## 18. Bagian Menu 2: Cari Harga Produk

**`elif pilih == 2` =** berfungsi untuk mengecek apakah pengguna memilih menu mencari harga produk.

**`try` =** berfungsi untuk menangani kesalahan input.

**Input harga yang dicari =** berfungsi untuk meminta pengguna memasukkan harga produk yang ingin dicari.

**`int(input(...))` =** berfungsi untuk mengubah input menjadi angka.

**`if bst.search(harga)` =** berfungsi untuk memanggil fungsi pencarian dan mengecek apakah harga ditemukan dalam tree.

**Print harga ditemukan =** berfungsi untuk menampilkan pesan jika harga ada di dalam tree.

**`else` =** berfungsi untuk menjalankan kondisi ketika harga tidak ditemukan.

**Print harga tidak ditemukan =** berfungsi untuk menampilkan pesan bahwa harga tidak ada di dalam tree.

**`except ValueError` =** berfungsi untuk menangani input yang bukan angka.

**Print harga harus berupa angka =** berfungsi untuk memberi tahu pengguna bahwa input harus berbentuk angka.

---

## 19. Bagian Menu 3: Tampilkan Harga dari Murah ke Mahal

**`elif pilih == 3` =** berfungsi untuk mengecek apakah pengguna memilih menu menampilkan harga dari murah ke mahal.

**Print daftar harga =** berfungsi untuk menampilkan teks pembuka sebelum daftar harga dicetak.

**`bst.inorder(bst.root)` =** berfungsi untuk menampilkan data harga menggunakan traversal inorder, dimulai dari root.

**Print kosong setelah inorder =** berfungsi untuk membuat baris baru setelah daftar harga selesai ditampilkan.

---

## 20. Bagian Menu 4: Preorder Harga Produk

**`elif pilih == 4` =** berfungsi untuk mengecek apakah pengguna memilih menu preorder.

**Print preorder harga produk =** berfungsi untuk menampilkan teks pembuka sebelum hasil preorder dicetak.

**`bst.preorder(bst.root)` =** berfungsi untuk menampilkan data harga dengan urutan root, kiri, kanan.

**Print kosong setelah preorder =** berfungsi untuk membuat baris baru setelah hasil preorder selesai ditampilkan.

---

## 21. Bagian Menu 5: Postorder Harga Produk

**`elif pilih == 5` =** berfungsi untuk mengecek apakah pengguna memilih menu postorder.

**Print postorder harga produk =** berfungsi untuk menampilkan teks pembuka sebelum hasil postorder dicetak.

**`bst.postorder(bst.root)` =** berfungsi untuk menampilkan data harga dengan urutan kiri, kanan, root.

**Print kosong setelah postorder =** berfungsi untuk membuat baris baru setelah hasil postorder selesai ditampilkan.

---

## 22. Bagian Menu 6: Cari Harga Termurah

**`elif pilih == 6` =** berfungsi untuk mengecek apakah pengguna memilih menu mencari harga termurah.

**`harga_min = bst.find_min(bst.root)` =** berfungsi untuk memanggil fungsi pencarian nilai terkecil dan menyimpan hasilnya ke variabel `harga_min`.

**`if harga_min == -1` =** berfungsi untuk mengecek apakah data harga masih kosong.

**Print data masih kosong =** berfungsi untuk memberi tahu bahwa belum ada harga produk yang tersimpan.

**`else` =** berfungsi untuk menjalankan kondisi ketika data harga sudah tersedia.

**Print harga produk termurah =** berfungsi untuk menampilkan harga paling kecil yang ditemukan dalam tree.

---

## 23. Bagian Menu 7: Cari Harga Termahal

**`elif pilih == 7` =** berfungsi untuk mengecek apakah pengguna memilih menu mencari harga termahal.

**`harga_max = bst.find_max(bst.root)` =** berfungsi untuk memanggil fungsi pencarian nilai terbesar dan menyimpan hasilnya ke variabel `harga_max`.

**`if harga_max == -1` =** berfungsi untuk mengecek apakah data harga masih kosong.

**Print data masih kosong =** berfungsi untuk memberi tahu bahwa belum ada harga produk yang tersimpan.

**`else` =** berfungsi untuk menjalankan kondisi ketika data harga tersedia.

**Print harga produk termahal =** berfungsi untuk menampilkan harga paling besar yang ditemukan dalam tree.

---

## 24. Bagian Menu 8: Hitung Jumlah Produk

**`elif pilih == 8` =** berfungsi untuk mengecek apakah pengguna memilih menu menghitung jumlah produk.

**Print jumlah produk yang tersimpan =** berfungsi untuk menampilkan hasil dari fungsi `count_nodes`.

**`bst.count_nodes(bst.root)` =** berfungsi untuk menghitung jumlah seluruh node atau jumlah harga produk yang tersimpan dalam tree.

---

## 25. Bagian Menu 9: Hitung Total Semua Harga Produk

**`elif pilih == 9` =** berfungsi untuk mengecek apakah pengguna memilih menu menghitung total semua harga produk.

**Print total semua harga produk =** berfungsi untuk menampilkan hasil penjumlahan semua harga.

**`bst.sum_nodes(bst.root)` =** berfungsi untuk menjumlahkan seluruh nilai harga yang ada dalam tree.

---

## 26. Bagian Menu 10: Keluar

**`elif pilih == 10` =** berfungsi untuk mengecek apakah pengguna memilih menu keluar.

**Print program selesai =** berfungsi untuk menampilkan pesan bahwa program sudah berhenti.

Karena nilai `pilih` sudah sama dengan 10, kondisi `while pilih != 10` menjadi salah, sehingga perulangan berhenti.

---

## 27. Bagian Pilihan Tidak Valid

**`else` =** berfungsi untuk menangani pilihan menu yang tidak sesuai, misalnya pengguna memasukkan angka selain 1 sampai 10.

**Print pilihan tidak valid =** berfungsi untuk memberi tahu bahwa menu yang dipilih tidak tersedia.

---

## 28. Bagian Penjalankan Program

**`if __name__ == "__main__"` =** berfungsi untuk mengecek apakah file program dijalankan secara langsung.

**`main()` =** berfungsi untuk memanggil fungsi utama agar program mulai berjalan.

---




# OUTPUT

<img width="374" height="811" alt="Cuplikan layar 2026-05-26 214005" src="https://github.com/user-attachments/assets/67c088b1-5b3a-4aa8-9c7d-857a9ec49c44" />
<img width="469" height="773" alt="Cuplikan layar 2026-05-26 214041" src="https://github.com/user-attachments/assets/d3845356-b34a-4d16-b5ae-4b56cbe64164" />
<img width="536" height="809" alt="Cuplikan layar 2026-05-26 214053" src="https://github.com/user-attachments/assets/d281354b-5848-4e58-908b-12dfe865067a" />
<img width="536" height="809" alt="Cuplikan layar 2026-05-26 214053" src="https://github.com/user-attachments/assets/52ff9e6b-bd1d-4335-a6bd-ebffc0ca5228" />



# Penjelasan Output

Output tersebut menunjukkan proses penggunaan program Sistem Harga Produk Online yang menggunakan struktur data Binary Search Tree. Data yang dimasukkan ke dalam program adalah harga produk sebesar Rp100, Rp500, dan Rp900.

Pada awal program, sistem menampilkan menu utama yang berisi pilihan untuk menambah harga produk, mencari harga produk, menampilkan harga, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, menghitung total harga produk, dan keluar dari program.

Ketika pengguna memilih menu 1, program meminta pengguna memasukkan harga produk. Harga pertama yang dimasukkan adalah Rp100. Karena data masih kosong, harga Rp100 menjadi node utama atau root dalam Binary Search Tree.

Setelah itu, pengguna kembali memilih menu 1 dan memasukkan harga Rp500. Karena Rp500 lebih besar dari Rp100, maka harga Rp500 ditempatkan di sebelah kanan Rp100.

Kemudian pengguna memasukkan harga Rp900. Karena Rp900 lebih besar dari Rp100 dan juga lebih besar dari Rp500, maka harga Rp900 ditempatkan di sebelah kanan Rp500.

Dengan demikian, data harga yang tersimpan dalam Binary Search Tree adalah Rp100, Rp500, dan Rp900.

Ketika pengguna memilih menu 2 dan mencari harga Rp500, program menampilkan bahwa harga produk Rp500 ditemukan. Hal ini berarti harga tersebut memang sudah tersimpan di dalam Binary Search Tree.

Ketika pengguna memilih menu 3, program menampilkan daftar harga dari murah ke mahal, yaitu Rp100, Rp500, dan Rp900. Hasil ini diperoleh dari proses inorder traversal. Inorder traversal menampilkan data dari nilai terkecil ke nilai terbesar.

Ketika pengguna memilih menu 4, program menampilkan preorder harga produk, yaitu Rp100, Rp500, dan Rp900. Preorder traversal menampilkan data mulai dari root terlebih dahulu, kemudian dilanjutkan ke cabang berikutnya.

Ketika pengguna memilih menu 5, program menampilkan postorder harga produk, yaitu Rp900, Rp500, dan Rp100. Postorder traversal menampilkan data dari bagian cabang terlebih dahulu, lalu root ditampilkan terakhir.

Ketika pengguna memilih menu 6, program menampilkan harga produk termurah, yaitu Rp100. Harga ini menjadi nilai terkecil karena berada pada posisi paling awal dan tidak ada harga lain yang lebih kecil.

Ketika pengguna memilih menu 7, program menampilkan harga produk termahal, yaitu Rp900. Harga ini menjadi nilai terbesar karena berada pada bagian paling kanan dari Binary Search Tree.

Ketika pengguna memilih menu 8, program menampilkan jumlah produk yang tersimpan, yaitu 3. Jumlah tersebut sesuai dengan tiga harga yang telah dimasukkan, yaitu Rp100, Rp500, dan Rp900.

Ketika pengguna memilih menu 9, program menampilkan total semua harga produk, yaitu Rp1500. Total ini diperoleh dari penjumlahan Rp100 ditambah Rp500 ditambah Rp900.

Terakhir, ketika pengguna memilih menu 10, program menampilkan pesan Program selesai. Hal ini berarti pengguna keluar dari program dan proses selesai dijalankan.

Kesimpulannya, output tersebut menunjukkan bahwa program berhasil menjalankan fungsi Binary Search Tree untuk menambah harga produk, mencari harga produk, menampilkan data harga, mencari harga termurah dan termahal, menghitung jumlah produk, serta menghitung total seluruh harga produk.

