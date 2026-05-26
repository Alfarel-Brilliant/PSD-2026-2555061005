## JUDUL PROGRAM

Sistem Harga Produk Online menggunakan Binary Search Tree

# Deskripsi Singkat

Program ini digunakan untuk  sistem penyimpanan harga produk pada toko online menggunakan struktur data Binary Search Tree (BST). Binary Search Tree adalah struktur data berbentuk pohon biner yang menyimpan data secara terurut berdasarkan aturan tertentu.

Pada program ini, setiap harga produk disimpan sebagai sebuah node. Jika harga produk lebih kecil dari node utama, maka harga tersebut akan masuk ke bagian kiri. Jika harga produk lebih besar, maka harga tersebut akan masuk ke bagian kanan. Dengan aturan ini, data harga produk dapat dicari, ditampilkan, dihitung, serta diurutkan dengan lebih mudah.

Program ini memungkinkan pengguna untuk menambahkan harga produk, mencari harga produk tertentu, menampilkan harga dari murah ke mahal, menampilkan traversal preorder dan postorder, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, serta menghitung total semua harga produk yang tersimpan.

Pada Binary Search Tree, operasi pencarian dan penambahan data memiliki kompleksitas waktu rata-rata O(log n) jika bentuk tree seimbang. Namun, pada kondisi terburuk, kompleksitasnya dapat menjadi O(n) apabila tree tidak seimbang.

# Sumber Kode

![screenshot_kode_bst_vscode.png](https://github.com/user-attachments/assets/98a547b7-872f-46a7-a56f-a39b3c2956f0)


# Penjelasan Logika Perbaris

# 1. Bagian Class Node

class Node: = berfungsi sebagai class untuk membuat node atau simpul pada Binary Search Tree. Setiap node digunakan untuk menyimpan satu nilai data, yaitu harga produk.

def __init__(self, key): = berfungsi sebagai konstruktor yang otomatis dijalankan ketika objek Node dibuat. Parameter key digunakan untuk menerima nilai harga produk yang akan disimpan.

self.key = key = berfungsi untuk menyimpan nilai key ke dalam atribut key milik nodeersebut.

self.left = None = berfungsi untuk membuat cabang kiri dari node. Nilainya None karena saat node pertama kali dibuat, node belum memiliki anak kiri.

self.right = None = berfungsi untuk membuat cabang kanan dari node. Nilainya None karena saat node pertama kali dibuat, node belum memiliki anak kanan.

# 2. Bagian Class BSTHargaOnline

class BSTHargaOnline: = berfungsi sebagai class utama yang digunakan untuk mengelola struktur Binary Search Tree. Class ini berisi fungsi untuk menambah data, mencari data, menampilkan data, mencari nilai minimum, mencari nilai maksimum, menghitung jumlah node, dan menjumlahkan seluruh nilai harga.

def __init__(self): = berfungsi sebagai konstruktor pada class BSTHargaOnline. Fungsi ini otomatis dijalankan ketika objek dari class tersebut dibuat.

self.root = None = berfungsi untuk membuat atribut root sebagai akar utama tree. Nilainya None karena pada awal program tree masih kosong.

# 3. Bagian Fungsi insert_node(self, root, key)

def insert_node(self, root, key): = berfungsi untuk memasukkan nilai harga produk ke dalam Binary Search Tree. Fungsi ini bekerja secara rekursif sampai menemukan posisi node yang sesuai.

if root is None: = berfungsi untuk mengecek apakah posisi node yang sedang diperiksa masih kosong.

return Node(key) = berfungsi untuk membuat node baru berisi nilai key jika posisi yang diperiksa masih kosong.

if key < root.key: = berfungsi untuk mengecek apakah nilai key lebih kecil dari nilai root.key.

root.left = self.insert_node(root.left, key) = berfungsi untuk memasukkan nilai key ke cabang kiri jika nilai tersebut lebih kecil dari nilai node yang sedang diperiksa.

elif key > root.key: = berfungsi untuk mengecek apakah nilai key lebih besar dari nilai root.key.

root.right = self.insert_node(root.right, key) = berfungsi untuk memasukkan nilai key ke cabang kanan jika nilai tersebut lebih besar dari nilai node yang sedang diperiksa.

return root = berfungsi untuk mengembalikan root yang sudah diperbarui agar struktur tree tetap tersambung dengan benar.

# 4. Bagian Fungsi insert(self, key)

def insert(self, key): = berfungsi sebagai fungsi untuk menambahkan harga produk ke dalam Binary Search Tree.

self.root = self.insert_node(self.root, key) = berfungsi untuk memulai proses penambahan data dari self.root. Setelah data berhasil diproses, hasil tree yang sudah diperbarui disimpan kembali ke self.root.

# 5. Bagian Fungsi search_node(self, root, key)

def search_node(self, root, key): = berfungsi untuk mencari apakah suatu nilai harga terdapat di dalam Binary Search Tree.

if root is None: = berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

return False = berfungsi untuk mengembalikan hasil False jika data yang dicari tidak ditemukan.

if root.key == key: = berfungsi untuk mengecek apakah nilai pada node saat ini sama dengan nilai key yang dicari.

return True = berfungsi untuk mengembalikan hasil True jika data yang dicari ditemukan.

if key < root.key: = berfungsi untuk mengecek apakah nilai key lebih kecil dari nilai node saat ini.

return self.search_node(root.left, key) = berfungsi untuk melanjutkan proses pencarian ke cabang kiri.

return self.search_node(root.right, key) = berfungsi untuk melanjutkan proses pencarian ke cabang kanan jika nilai key lebih besar dari nilai node saat ini.

# 6. Bagian Fungsi search(self, key)

def search(self, key): = berfungsi sebagai fungsi pembungkus untuk melakukan pencarian harga produk.

return self.search_node(self.root, key) = berfungsi untuk memulai pencarian dari self.root dan mengembalikan hasil berupa True jika data ditemukan atau False jika data tidak ditemukan.

# 7. Bagian Fungsi inorder(self, root)

def inorder(self, root): = berfungsi untuk menampilkan data harga secara berurutan dari nilai terkecil ke nilai terbesar.

if root is None: = berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

return = berfungsi untuk menghentikan proses fungsi jika node kosong.

self.inorder(root.left) = berfungsi untuk menelusuri cabang kiri terlebih dahulu.

print("Rp", root.key, end=" ") = berfungsi untuk menampilkan nilai harga pada node saat ini dalam format rupiah.

self.inorder(root.right) = berfungsi untuk menelusuri cabang kanan setelah nilai node saat ini ditampilkan.

# 8. Bagian Fungsi preorder(self, root)

def preorder(self, root): = berfungsi untuk menampilkan data harga dengan urutan root, kiri, lalu kanan.

if root is None: = berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

return = berfungsi untuk menghentikan proses fungsi jika node kosong.

print("Rp", root.key, end=" ") = berfungsi untuk menampilkan nilai node saat ini terlebih dahulu.

self.preorder(root.left) = berfungsi untuk menelusuri cabang kiri setelah root ditampilkan.

self.preorder(root.right) = berfungsi untuk menelusuri cabang kanan setelah cabang kiri selesai ditelusuri.

# 9. Bagian Fungsi postorder(self, root)

def postorder(self, root): = berfungsi untuk menampilkan data harga dengan urutan kiri, kanan, lalu root.

if root is None: = berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

return = berfungsi untuk menghentikan proses fungsi jika node kosong.

self.postorder(root.left) = berfungsi untuk menelusuri cabang kiri terlebih dahulu.

self.postorder(root.right) = berfungsi untuk menelusuri cabang kanan setelah cabang kiri selesai ditelusuri.

print("Rp", root.key, end=" ") = berfungsi untuk menampilkan nilai node saat ini setelah cabang kiri dan cabang kanan selesai ditelusuri.

# 10. Bagian Fungsi find_min(self, root)

def find_min(self, root): = berfungsi untuk mencari nilai harga paling kecil di dalam Binary Search Tree.

if root is None: = berfungsi untuk mengecek apakah tree masih kosong.

return -1 = berfungsi untuk mengembalikan nilai -1 sebagai tanda bahwa data belum tersedia.

current = root = berfungsi untuk membuat variabel penunjuk sementara yang dimulai dari root.

while current.left is not None: = berfungsi untuk melakukan perulangan selama node di sebelah kiri masih ada.

current = current.left = berfungsi untuk memindahkan penunjuk ke node kiri berikutnya.

return current.key = berfungsi untuk mengembalikan nilai paling kecil setelah node paling kiri ditemukan.

# 11. Bagian Fungsi find_max(self, root)

def find_max(self, root): = berfungsi untuk mencari nilai harga paling besar di dalam Binary Search Tree.

if root is None: = berfungsi untuk mengecek apakah tree masih kosong.

return -1 = berfungsi untuk mengembalikan nilai -1 sebagai tanda bahwa data belum tersedia.

current = root = berfungsi untuk membuat variabel penunjuk sementara yang dimulai dari root.

while current.right is not None: = berfungsi untuk melakukan perulangan selama node di sebelah kanan masih ada.

current = current.right = berfungsi untuk memindahkan penunjuk ke node kanan berikutnya.

return current.key = berfungsi untuk mengembalikan nilai paling besar setelah node paling kanan ditemukan.

# 12. Bagian Fungsi count_nodes(self, root)

def count_nodes(self, root): = berfungsi untuk menghitung jumlah node atau jumlah harga produk yang tersimpan dalam tree.

if root is None: = berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

return 0 = berfungsi untuk mengembalikan nilai 0 jika node kosong.

return 1 + self.count_nodes(root.left) + self.count_nodes(root.right) = berfungsi untuk menghitung satu node saat ini, kemudian menambahkan jumlah node dari cabang kiri dan cabang kanan.

# 13. Bagian Fungsi sum_nodes(self, root)

def sum_nodes(self, root): = berfungsi untuk menghitung total seluruh nilai harga produk yang tersimpan di dalam tree.

if root is None: = berfungsi untuk mengecek apakah node yang sedang diperiksa kosong.

return 0 = berfungsi untuk mengembalikan nilai 0 jika node kosong agar tidak memengaruhi hasil penjumlahan.

return root.key + self.sum_nodes(root.left) + self.sum_nodes(root.right) = berfungsi untuk menjumlahkan nilai pada node saat ini dengan seluruh nilai pada cabang kiri dan cabang kanan.

# 14. Bagian Fungsi main()

def main(): = berfungsi sebagai fungsi utama yang menjalankan program.

bst = BSTHargaOnline() = berfungsi untuk membuat objek bernama bst dari class BSTHargaOnline. Objek ini digunakan untuk mengakses seluruh fungsi yang ada di dalam class tersebut.

pilih = 0 = berfungsi untuk memberikan nilai awal pada variabel pilih. Variabel ini digunakan untuk menyimpan pilihan menu dari pengguna.

while pilih != 10: = berfungsi untuk menjalankan perulangan selama nilai pilih tidak sama dengan 10. Program akan terus berjalan sampai pengguna memilih menu keluar.

# 15. Bagian Tampilan Menu

print() = berfungsi untuk memberikan baris kosong agar tampilan menu terlihat lebih rapi.

print("SISTEM HARGA PRODUK ONLINE") = berfungsi untuk menampilkan judul utama program.

print("1. Tambah harga produk") = berfungsi untuk menampilkan pilihan menu nomor 1, yaitu menambah harga produk ke dalam tree.

print("2. Cari harga produk") = berfungsi untuk menampilkan pilihan menu nomor 2, yaitu mencari harga produk tertentu di dalam tree.

print("3. Tampilkan harga dari murah ke mahal") = berfungsi untuk menampilkan pilihan menu nomor 3, yaitu menampilkan data harga secara berurutan dari nilai terkecil ke nilai terbesar.

print("4. Tampilkan preorder harga produk") = berfungsi untuk menampilkan pilihan menu nomor 4, yaitu menampilkan data harga menggunakan traversal preorder.

print("5. Tampilkan postorder harga produk") = berfungsi untuk menampilkan pilihan menu nomor 5, yaitu menampilkan data harga menggunakan traversal postorder.

print("6. Cari harga produk termurah") = berfungsi untuk menampilkan pilihan menu nomor 6, yaitu mencari harga paling kecil yang tersimpan di dalam tree.

print("7. Cari harga produk termahal") = berfungsi untuk menampilkan pilihan menu nomor 7, yaitu mencari harga paling besar yang tersimpan di dalam tree.

print("8. Hitung jumlah produk yang tersimpan") = berfungsi untuk menampilkan pilihan menu nomor 8, yaitu menghitung jumlah data harga produk yang tersimpan.

print("9. Hitung total semua harga produk") = berfungsi untuk menampilkan pilihan menu nomor 9, yaitu menghitung total seluruh harga produk yang tersimpan.

print("10. Keluar") = berfungsi untuk menampilkan pilihan menu nomor 10, yaitu keluar dari program.

# 16. Bagian Input Pilihan Menu

try: = berfungsi untuk mencoba menjalankan proses input pilihan menu. Bagian ini digunakan untuk mencegah program berhenti jika pengguna memasukkan input yang tidak sesuai.

pilih = int(input("Masukkan pilihan menu: ")) = berfungsi untuk meminta pengguna memasukkan pilihan menu. Fungsi input() menerima masukan dari pengguna, kemudian int() mengubah masukan tersebut menjadi tipe data integer.

except ValueError: = berfungsi untuk menangani kesalahan jika pengguna memasukkan input yang tidak dapat diubah menjadi angka.

print("Input tidak valid. Pilihan harus berupa angka.") = berfungsi untuk menampilkan pesan bahwa input yang dimasukkan harus berupa angka.

continue = berfungsi untuk mengulang program kembali ke awal perulangan while, sehingga menu akan ditampilkan kembali tanpa menjalankan pilihan menu lainnya.

# 17. Bagian Menu 1: Tambah Harga Produk

if pilih == 1: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 1.

try: = berfungsi untuk mencoba menjalankan proses input harga produk dan mencegah program berhenti jika input harga tidak valid.

harga = int(input("Masukkan harga produk: ")) = berfungsi untuk meminta pengguna memasukkan harga produk. Input tersebut kemudian diubah menjadi tipe data integer dan disimpan ke dalam variabel harga.

bst.insert(harga) = berfungsi untuk memasukkan nilai harga ke dalam Binary Search Tree melalui fungsi insert().

print("Harga berhasil dimasukkan.") = berfungsi untuk menampilkan pesan bahwa harga produk berhasil disimpan ke dalam tree.

except ValueError: = berfungsi untuk menangani kesalahan jika pengguna memasukkan harga yang bukan angka.

print("Harga harus berupa angka.") = berfungsi untuk menampilkan pesan bahwa input harga harus berupa angka.

# 18. Bagian Menu 2: Cari Harga Produk

elif pilih == 2: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 2.

try: = berfungsi untuk mencoba menjalankan proses input harga yang ingin dicari.

harga = int(input("Masukkan harga yang dicari: ")) = berfungsi untuk meminta pengguna memasukkan harga yang ingin dicari. Input tersebut kemudian diubah menjadi integer dan disimpan dalam variabel harga.

if bst.search(harga): = berfungsi untuk memanggil fungsi search() guna mengecek apakah nilai harga terdapat di dalam tree.

print("Harga ditemukan.") = berfungsi untuk menampilkan pesan jika harga yang dicari terdapat di dalam tree.

else: = berfungsi untuk menjalankan kondisi ketika harga yang dicari tidak ditemukan.

print("Harga tidak ditemukan.") = berfungsi untuk menampilkan pesan bahwa harga yang dicari tidak terdapat di dalam tree.

except ValueError: = berfungsi untuk menangani kesalahan jika input harga bukan angka.

print("Harga harus berupa angka.") = berfungsi untuk menampilkan pesan bahwa input harga harus berupa angka.

# 19. Bagian Menu 3: Tampilkan Harga dari Murah ke Mahal

elif pilih == 3: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 3.

print("Daftar harga dari murah ke mahal:") = berfungsi untuk menampilkan keterangan bahwa program akan menampilkan daftar harga dari nilai terkecil ke nilai terbesar.

bst.inorder(bst.root) = berfungsi untuk menjalankan fungsi inorder() dari root agar data harga ditampilkan secara berurutan.

print() = berfungsi untuk membuat baris baru setelah hasil traversal inorder selesai ditampilkan.

# 20. Bagian Menu 4: Preorder Harga Produk

elif pilih == 4: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 4.

print("Preorder harga produk:") = berfungsi untuk menampilkan keterangan bahwa program akan menampilkan data harga menggunakan traversal preorder.

bst.preorder(bst.root) = berfungsi untuk menjalankan fungsi preorder() dari root dengan urutan root, kiri, dan kanan.

print() = berfungsi untuk membuat baris baru setelah hasil traversal preorder selesai ditampilkan.

# 21. Bagian Menu 5: Postorder Harga Produk

elif pilih == 5: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 5.

print("Postorder harga produk:") = berfungsi untuk menampilkan keterangan bahwa program akan menampilkan data harga menggunakan traversal postorder.

bst.postorder(bst.root) = berfungsi untuk menjalankan fungsi postorder() dari root dengan urutan kiri, kanan, dan root.

print() = berfungsi untuk membuat baris baru setelah hasil traversal postorder selesai ditampilkan.

# 22. Bagian Menu 6: Cari Harga Termurah

elif pilih == 6: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 6.

harga_min = bst.find_min(bst.root) = berfungsi untuk memanggil fungsi find_min() dan menyimpan hasil harga terkecil ke dalam variabel harga_min.

if harga_min == -1: = berfungsi untuk mengecek apakah data harga masih kosong.

print("Data harga masih kosong.") = berfungsi untuk menampilkan pesan bahwa belum ada data harga yang tersimpan di dalam tree.

else: = berfungsi untuk menjalankan kondisi ketika data harga sudah tersedia.

print("Harga produk termurah: Rp", harga_min) = berfungsi untuk menampilkan harga produk termurah yang ditemukan di dalam tree.

# 23. Bagian Menu 7: Cari Harga Termahal

elif pilih == 7: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 7.

harga_max = bst.find_max(bst.root) = berfungsi untuk memanggil fungsi find_max() dan menyimpan hasil harga terbesar ke dalam variabel harga_max.

if harga_max == -1: = berfungsi untuk mengecek apakah data harga masih kosong.

print("Data harga masih kosong.") = berfungsi untuk menampilkan pesan bahwa belum ada data harga yang tersimpan di dalam tree.

else: = berfungsi untuk menjalankan kondisi ketika data harga sudah tersedia.

print("Harga produk termahal: Rp", harga_max) = berfungsi untuk menampilkan harga produk termahal yang ditemukan di dalam tree.

# 24. Bagian Menu 8: Hitung Jumlah Produk

elif pilih == 8: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 8.

print("Jumlah produk yang tersimpan:", bst.count_nodes(bst.root)) = berfungsi untuk menampilkan jumlah seluruh node atau jumlah data harga produk yang tersimpan di dalam tree.

# 25. Bagian Menu 9: Hitung Total Semua Harga Produk

elif pilih == 9: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 9.

print("Total semua harga produk: Rp", bst.sum_nodes(bst.root)) = berfungsi untuk menampilkan total seluruh harga produk yang tersimpan di dalam tree.

# 26. Bagian Menu 10: Keluar

elif pilih == 10: = berfungsi untuk mengecek apakah pengguna memilih menu nomor 10.

print("Program selesai.") = berfungsi untuk menampilkan pesan bahwa program telah selesai dijalankan.

# 27. Bagian Pilihan Tidak Valid

else: = berfungsi untuk menangani pilihan menu yang tidak sesuai, misalnya pengguna memasukkan angka selain 1 sampai 10.

print("Pilihan tidak valid.") = berfungsi untuk menampilkan pesan bahwa menu yang dipilih tidak tersedia.

# 28. Bagian Menjalankan Program

if __name__ == "__main__": = berfungsi untuk mengecek apakah file program dijalankan secara langsung.

main() = berfungsi untuk memanggil fungsi main agar program mulai dijalankan.



# OUTPUT

![screenshot_teks_terminal_bst_tanpa_bezel.png](https://github.com/user-attachments/assets/032aa216-1862-4e18-8420-5400873bb4f1)


# Penjelasan Output

Output tersebut menunjukkan proses penggunaan program sistem harga produk online yang menggunakan struktur data Binary Search Tree. Pada program ini, data harga yang dimasukkan adalah Rp100, Rp500, dan Rp900.

Pada awal program, sistem menampilkan menu utama. Menu tersebut berisi beberapa pilihan, seperti menambah harga produk, mencari harga produk, menampilkan harga dari murah ke mahal, menampilkan preorder dan postorder, mencari harga termurah, mencari harga termahal, menghitung jumlah produk, menghitung total harga, serta keluar dari program.

Pertama, pengguna memilih menu nomor 1 untuk menambahkan harga produk. Harga yang pertama dimasukkan adalah Rp100. Karena sebelumnya belum ada data di dalam tree, maka harga Rp100 menjadi data pertama sekaligus menjadi root atau akar utama pada Binary Search Tree.

Setelah itu, pengguna kembali memilih menu nomor 1 dan memasukkan harga Rp500. Karena nilai Rp500 lebih besar dari Rp100, maka data tersebut ditempatkan di sebelah kanan dari node Rp100.

Kemudian, pengguna memasukkan harga Rp900. Nilai Rp900 lebih besar dari Rp100 dan juga lebih besar dari Rp500, sehingga data tersebut ditempatkan di sebelah kanan node Rp500. Jadi, susunan data yang tersimpan dalam tree adalah Rp100, Rp500, dan Rp900.

Selanjutnya, pengguna memilih menu nomor 2 untuk mencari harga produk. Harga yang dicari adalah Rp500. Program kemudian menampilkan bahwa harga produk Rp500 ditemukan, yang berarti data tersebut memang sudah tersimpan di dalam Binary Search Tree.

Pada menu nomor 3, program menampilkan daftar harga dari murah ke mahal, yaitu Rp100, Rp500, dan Rp900. Hasil ini diperoleh dari proses inorder traversal, yaitu proses penelusuran tree yang menampilkan data dari nilai terkecil sampai nilai terbesar.

Pada menu nomor 4, program menampilkan hasil preorder traversal, yaitu Rp100, Rp500, dan Rp900. Pada preorder, data ditampilkan mulai dari root terlebih dahulu, kemudian dilanjutkan ke cabang berikutnya.

Pada menu nomor 5, program menampilkan hasil postorder traversal, yaitu Rp900, Rp500, dan Rp100. Pada postorder, data dari cabang ditampilkan lebih dulu, sedangkan root ditampilkan di bagian akhir.

Pada menu nomor 6, program menampilkan harga produk termurah, yaitu Rp100. Harga ini menjadi nilai terkecil karena tidak ada data lain yang lebih kecil dari Rp100.

Pada menu nomor 7, program menampilkan harga produk termahal, yaitu Rp900. Harga ini menjadi nilai terbesar karena berada pada bagian paling kanan dalam susunan Binary Search Tree.

Pada menu nomor 8, program menampilkan jumlah produk yang tersimpan, yaitu 3. Jumlah tersebut sesuai dengan data yang sudah dimasukkan sebelumnya, yaitu Rp100, Rp500, dan Rp900.

Pada menu nomor 9, program menampilkan total semua harga produk, yaitu Rp1500. Total tersebut diperoleh dari penjumlahan Rp100 ditambah Rp500 ditambah Rp900.

Terakhir, pengguna memilih menu nomor 10 untuk keluar dari program. Setelah itu, program menampilkan pesan program selesai, yang menandakan bahwa proses penggunaan program telah berakhir.

LINK YOUTUBE: https://youtu.be/H8VyqCcfLvA?si=DdqnB1I-F4w4hBbD