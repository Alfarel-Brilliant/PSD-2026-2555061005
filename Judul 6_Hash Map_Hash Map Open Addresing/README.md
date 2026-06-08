### Judul
Program Hash Map Data Barang Toko Menggunakan Open Addressing

### Deskripsi Singkat

Program ini merupakan implementasi struktur data Hash Map yang digunakan untuk menyimpan dan mengelola data barang pada sebuah toko sederhana. Dalam program ini, setiap barang memiliki "kode barang" sebagai **key** dan "nama barang" sebagai **value**. Key berfungsi sebagai identitas unik yang digunakan untuk menentukan lokasi penyimpanan data di dalam hash table, sedangkan value merupakan informasi barang yang disimpan. Melalui program ini, pengguna dapat memahami proses penambahan data, pencarian data, penghapusan data, serta penampilan seluruh isi tabel.

Struktur data yang diterapkan pada program ini adalah Hash Map Open Addressing dengan metode **linear probing**. Metode ini bekerja dengan cara menghitung indeks penyimpanan menggunakan fungsi hash. Apabila terjadi **collision**, yaitu ketika dua key menghasilkan indeks yang sama, maka program akan mencari slot kosong berikutnya secara berurutan. Dengan demikian, data tetap dapat disimpan di dalam hash table meskipun terdapat tabrakan indeks. Penerapan metode ini menunjukkan bahwa Hash Map dapat digunakan untuk mempercepat proses pencarian data dibandingkan pencarian secara berurutan.


### Penjelasan kode



#### 1. Bagian Class SlotState



class SlotState berfungsi sebagai class untuk menyimpan status setiap slot pada Hash Table. Status ini digunakan agar program dapat mengetahui apakah sebuah slot masih kosong, sudah terisi, atau sudah pernah dihapus.



EMPTY = 0 berfungsi sebagai tanda bahwa slot masih kosong dan belum pernah digunakan untuk menyimpan data barang.



OCCUPIED = 1 berfungsi sebagai tanda bahwa slot sudah terisi oleh data barang. Jika slot berstatus ini, maka program akan mengecek apakah key yang dimasukkan sama atau berbeda.



DELETED = 2 berfungsi sebagai tanda bahwa slot sebelumnya pernah berisi data, tetapi data tersebut sudah dihapus. Status ini penting pada Linear Probing agar proses pencarian data tetap bisa melewati slot yang sudah dihapus.



#### 2. Bagian Class Entry



class Entry berfungsi sebagai class untuk membuat satu slot penyimpanan pada Hash Table. Setiap slot akan menyimpan key, value, dan state.



def init self berfungsi sebagai konstruktor yang otomatis dijalankan ketika objek Entry dibuat.



self.key = None berfungsi untuk menyimpan key dari data barang. Pada studi kasus toko, key digunakan sebagai kode barang.



self.value = None berfungsi untuk menyimpan value atau isi data barang. Value dapat berupa nama barang, stok, dan harga barang.



self.state = SlotState.EMPTY berfungsi untuk memberikan status awal pada slot, yaitu kosong. Artinya, saat slot pertama kali dibuat, slot tersebut belum berisi data.



#### 3. Bagian Class HashMapOpenAddressing



class HashMapOpenAddressing berfungsi sebagai class utama untuk mengelola Hash Map. Di dalam class ini terdapat fungsi untuk memasukkan data, mencari data, menghapus data, dan menampilkan data barang.



def init self, size=10 berfungsi sebagai konstruktor untuk membuat Hash Table dengan ukuran default 10 slot.



self.SIZE = size berfungsi untuk menyimpan ukuran Hash Table. Jika tidak diubah, maka ukuran tabel adalah 10.



self.table = Entry for range self.SIZE berfungsi untuk membuat list yang berisi objek Entry sebanyak ukuran Hash Table. Setiap objek Entry menjadi satu slot penyimpanan data barang.



#### 4. Bagian Fungsi hash_function



def hash_function self, key berfungsi untuk menentukan posisi awal penyimpanan data berdasarkan key. Pada program toko, key yang digunakan adalah kode barang.



return key % self.SIZE berfungsi untuk menghasilkan index penyimpanan dari key. Misalnya kode barang 101 dimasukkan ke tabel berukuran 10, maka hasilnya adalah 101 % 10 = 1. Artinya data barang diarahkan ke index 1.



#### 5. Bagian Fungsi insert



def insert self, key, value berfungsi untuk memasukkan data barang ke dalam Hash Table. Parameter key digunakan sebagai kode barang, sedangkan value digunakan sebagai data barang.



idx = self.hash_function key berfungsi untuk menentukan index awal berdasarkan kode barang yang dimasukkan.



first_deleted = -1 berfungsi untuk menyimpan posisi slot yang sudah dihapus. Nilai awal -1 berarti belum ada slot DELETED yang ditemukan.



for step in range self.SIZE berfungsi untuk melakukan perulangan sebanyak ukuran Hash Table. Perulangan ini digunakan untuk mencari slot yang sesuai.



i = idx + step % self.SIZE berfungsi untuk menjalankan Linear Probing. Jika index awal sudah terisi, maka program akan mengecek index berikutnya secara berurutan.



if self.table i state == SlotState.OCCUPIED berfungsi untuk mengecek apakah slot pada index tersebut sudah terisi data.



if self.table i key == key berfungsi untuk mengecek apakah kode barang yang dimasukkan sama dengan kode barang yang sudah ada.



self.table i value = value berfungsi untuk memperbarui data barang jika kode barang yang dimasukkan sudah pernah tersimpan sebelumnya.



return True berfungsi untuk mengembalikan nilai bahwa proses penyimpanan atau pembaruan data berhasil.



elif self.table i state == SlotState.DELETED berfungsi untuk mengecek apakah slot tersebut merupakan slot yang sudah pernah dihapus.



if first_deleted == -1 berfungsi untuk mengecek apakah sebelumnya sudah ditemukan slot DELETED atau belum.



first_deleted = i berfungsi untuk menyimpan posisi slot DELETED agar dapat digunakan kembali untuk menyimpan data baru.



else dijalankan jika slot yang diperiksa berstatus EMPTY atau kosong.



if first_deleted != -1 berfungsi untuk mengecek apakah sebelumnya ada slot DELETED yang bisa digunakan kembali.



i = first_deleted berfungsi untuk mengarahkan penyimpanan data ke slot DELETED yang ditemukan sebelumnya.



self.table i key = key berfungsi untuk menyimpan kode barang ke dalam slot.



self.table i value = value berfungsi untuk menyimpan data barang ke dalam slot.



self.table i state = SlotState.OCCUPIED berfungsi untuk mengubah status slot menjadi terisi.



return False berfungsi untuk mengembalikan nilai bahwa data gagal dimasukkan karena Hash Table penuh.



#### 6. Bagian Fungsi search



def search self, key berfungsi untuk mencari data barang berdasarkan kode barang.



idx = self.hash_function key berfungsi untuk menentukan index awal pencarian menggunakan fungsi hash.



for step in range self.SIZE berfungsi untuk melakukan pencarian maksimal sebanyak ukuran Hash Table.



i = idx + step % self.SIZE berfungsi untuk mencari data menggunakan Linear Probing. Jika data tidak ditemukan di index awal, program akan mengecek index berikutnya.



if self.table i state == SlotState.EMPTY berfungsi untuk menghentikan pencarian jika menemukan slot kosong. Jika slot kosong ditemukan, berarti data tidak ada.



return None berfungsi untuk mengembalikan nilai kosong karena data tidak ditemukan.



if self.table i state == SlotState.OCCUPIED and self.table i key == key berfungsi untuk mengecek apakah slot berisi data dan key-nya sama dengan kode barang yang dicari.



return self.table i berfungsi untuk mengembalikan slot yang berisi data barang yang ditemukan.



#### 7. Bagian Fungsi remove_key



def remove_key self, key berfungsi untuk menghapus data barang berdasarkan kode barang.



entry = self.search key berfungsi untuk mencari data barang terlebih dahulu sebelum dihapus.



if entry is None berfungsi untuk mengecek apakah data barang tidak ditemukan.



return False berfungsi untuk mengembalikan nilai bahwa proses penghapusan gagal.



entry.state = SlotState.DELETED berfungsi untuk mengubah status slot menjadi DELETED. Data tidak langsung dikosongkan agar proses pencarian pada Linear Probing tetap berjalan dengan benar.



return True berfungsi untuk mengembalikan nilai bahwa data berhasil dihapus.



#### 8. Bagian Fungsi display



def display self berfungsi untuk menampilkan seluruh isi Hash Table.



print Data Barang di Toko berfungsi untuk menampilkan judul output program.



for i in range self.SIZE berfungsi untuk mengulang seluruh index Hash Table dari awal sampai akhir.



print i berfungsi untuk menampilkan nomor index Hash Table.



if self.table i state == SlotState.EMPTY berfungsi untuk mengecek apakah slot masih kosong.



print EMPTY berfungsi untuk menampilkan keterangan bahwa slot kosong.



elif self.table i state == SlotState.DELETED berfungsi untuk mengecek apakah slot sudah dihapus.



print DELETED berfungsi untuk menampilkan keterangan bahwa slot pernah berisi data tetapi sudah dihapus.



else dijalankan jika slot berisi data barang.



print Kode Barang dan Data berfungsi untuk menampilkan kode barang dan data barang yang tersimpan.



#### 9. Bagian Fungsi main



def main berfungsi sebagai fungsi utama untuk menjalankan program.



hashmap = HashMapOpenAddressing berfungsi untuk membuat objek Hash Map dengan ukuran default 10.



hashmap.insert 101, Beras 5 Kg, Stok 20, Harga Rp75.000 berfungsi untuk memasukkan data barang beras ke dalam Hash Table.



hashmap.insert 111, Minyak Goreng 1 Liter, Stok 35, Harga Rp18.000 berfungsi untuk memasukkan data minyak goreng. Kode 111 mengalami collision dengan kode 101 karena sama-sama menghasilkan index 1.



hashmap.insert 121, Gula Pasir 1 Kg, Stok 40, Harga Rp15.000 berfungsi untuk memasukkan data gula pasir. Kode 121 juga mengalami collision sehingga program mencari slot kosong berikutnya.



hashmap.insert 102, Telur Ayam 1 Kg, Stok 25, Harga Rp28.000 berfungsi untuk memasukkan data telur ayam ke dalam Hash Table.



hashmap.display berfungsi untuk menampilkan seluruh data barang yang sudah tersimpan.



hasil = hashmap.search 111 berfungsi untuk mencari barang dengan kode 111.



if hasil is not None berfungsi untuk mengecek apakah barang ditemukan.



print Data barang berfungsi untuk menampilkan data barang jika ditemukan.



hashmap.remove_key 111 berfungsi untuk menghapus data barang dengan kode 111.



hashmap.display berfungsi untuk menampilkan kembali isi Hash Table setelah data barang dihapus.



hasil = hashmap.search 121 berfungsi untuk mencari barang dengan kode 121 setelah barang dengan kode 111 dihapus.



if name sama dengan main berfungsi untuk memastikan program utama hanya dijalankan ketika file Python dijalankan secara langsung.



main berfungsi untuk memanggil fungsi utama agar seluruh proses program berjalan.



