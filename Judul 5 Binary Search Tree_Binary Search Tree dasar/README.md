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

