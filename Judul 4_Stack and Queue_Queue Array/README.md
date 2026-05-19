
# Judul Program
 
 Simulasi Antrian Pendaftaran KRS Mahasiswa menggunakan Queue Array


# Deskripsi Singkat

Program ini digunakan untuk mensimulasikan sistem antrian pendaftaran KRS (Kartu Rencana Studi) mahasiswa di loket administrasi universitas menggunakan struktur data Queue (Antrian) berbasis Array.Queue adalah struktur data yang mengikuti prinsip FIFO (First In,First Out), artinya data yang pertama masuk akan pertama keluar,seperti antrian nyata di kehidupan sehari-hari.

Algoritma Queue Array memiliki kompleksitas waktu O(1) untuk operasi enqueue (masuk antrian) dan dequeue (keluar antrian). Program inimemungkinkan mahasiswa untuk masuk antrian, dipanggil satu per satu,dan menampilkan status antrian secara real-time. Jika antrian penuh,sistem akan menolak mahasiswa baru. Jika antrian kosong, tidak ada
mahasiswa yang bisa dipanggil.

# Sumber Kode

<img width="909" height="886" alt="Image" src="https://github.com/user-attachments/assets/a28789ae-0b44-4543-bf78-bd4b07dab1c5" />
--
<img width="935" height="843" alt="Image" src="https://github.com/user-attachments/assets/38184a95-5338-4cb9-992b-7f7583ea3524" />
--
<img width="518" height="82" alt="Image" src="https://github.com/user-attachments/assets/b4ae3b9d-7edc-41be-b9af-4480b533b111" />
--


# Penjelasan Logika Perbaris

 class  QueueArray.

Class ini dipakai sebagai cetakan untuk membuat sistem antrian. Jadi semua data dan fungsi antrian disimpan di dalam class ini.


---

def __init__(self, max_size=100):

Ini adalah constructor. Fungsi ini otomatis dijalankan saat objek queue dibuat.

max_size=100 berarti kapasitas maksimal antrian adalah 100 data mahasiswa.


---

self.MAXN = max_size

Baris ini menyimpan ukuran maksimal antrian ke dalam variabel MAXN.

Jika max_size bernilai 100, maka self.MAXN juga bernilai 100.


---

self.q = [None] * self.MAXN

Baris ini membuat array/list kosong dengan panjang 100.

Isinya sementara None, artinya belum ada data mahasiswa yang masuk.

Contohnya kira-kira:

[None, None, None, None, ...]


---

self.front_idx = -1

front_idx digunakan untuk menunjukkan posisi data paling depan dalam antrian.

Nilai -1 berarti antrian masih kosong.


---

self.rear_idx = -1

rear_idx digunakan untuk menunjukkan posisi data paling belakang dalam antrian.

Nilai -1 juga berarti belum ada data yang masuk. Jadi depan kosong, belakang kosong. Sepi kayak loket pas jam istirahat.


---

def is_empty(self):

Baris ini membuat fungsi untuk mengecek apakah antrian kosong.


---

return self.front_idx == -1

Kalau front_idx bernilai -1, berarti antrian kosong.

Jika benar, hasilnya True. Jika tidak, hasilnya False.


---

def is_full(self):

Baris ini membuat fungsi untuk mengecek apakah antrian sudah penuh.


---

return (self.rear_idx + 1) % self.MAXN == self.front_idx

Ini mengecek apakah posisi setelah rear_idx sudah kembali ke front_idx.

Karena kode ini memakai circular queue, indeksnya bisa muter lagi ke awal array.

Misalnya array penuh, maka posisi belakang tidak bisa maju lagi karena akan menabrak posisi depan.


---

def enqueue(self, x):

Fungsi enqueue digunakan untuk menambahkan data mahasiswa ke dalam antrian.

Parameter x adalah data yang dimasukkan, dalam konteks ini bisa dianggap sebagai NPM mahasiswa.


---

if self.is_full():

Baris ini mengecek apakah antrian penuh.


---

print("Antrian pendaftaran KRS penuh")

Kalau antrian penuh, program menampilkan pesan bahwa antrian tidak bisa ditambah lagi.


---

return

return menghentikan fungsi enqueue.

Jadi kalau antrian penuh, data tidak akan dimasukkan.


---

if self.is_empty():

Baris ini mengecek apakah antrian masih kosong.


---

self.front_idx = 0

Kalau antrian kosong, data pertama akan ditempatkan di indeks 0.

Maka posisi depan antrian menjadi 0.


---

self.rear_idx = 0

Karena baru ada satu data, posisi belakang juga sama, yaitu indeks 0.

Jadi data pertama adalah depan sekaligus belakang.


---

else:

Kalau antrian tidak kosong, maka data baru akan dimasukkan ke posisi berikutnya.


---

self.rear_idx = (self.rear_idx + 1) % self.MAXN

Baris ini memindahkan posisi belakang ke indeks berikutnya.

Karena memakai % self.MAXN, kalau sudah sampai akhir array, indeks bisa kembali ke awal.

Contoh: kalau rear_idx = 99, maka:

(99 + 1) % 100 = 0

Jadi balik lagi ke indeks 0. Ini namanya circular queue. Muter, bukan hilang kayak tanggung jawab manusia.


---

self.q[self.rear_idx] = x

Data mahasiswa x dimasukkan ke array pada posisi rear_idx.

Misalnya x = 2555061005, maka NPM itu masuk ke posisi belakang antrian.


---

print(f"Mahasiswa dengan NPM {x} berhasil masuk antrian pendaftaran KRS")

Program menampilkan pesan bahwa mahasiswa berhasil masuk antrian.


---

def dequeue(self):

Fungsi dequeue digunakan untuk mengeluarkan data dari antrian.

Dalam kasus ini, artinya mahasiswa paling depan dipanggil ke loket administrasi.


---

if self.is_empty():

Mengecek apakah antrian kosong.


---

print("Antrian pendaftaran KRS kosong")

Kalau kosong, tampilkan pesan bahwa belum ada mahasiswa dalam antrian.


---

return

Fungsi dihentikan karena tidak ada data yang bisa dikeluarkan.


---

print(f"Mahasiswa dengan NPM {self.q[self.front_idx]} dipanggil ke loket administrasi")

Baris ini menampilkan NPM mahasiswa paling depan yang akan dilayani.

self.q[self.front_idx] artinya mengambil data pada posisi paling depan.


---

if self.front_idx == self.rear_idx:

Baris ini mengecek apakah hanya ada satu data dalam antrian.

Kalau posisi depan sama dengan posisi belakang, berarti antrian hanya berisi satu mahasiswa.


---

self.front_idx = -1

Setelah satu-satunya mahasiswa dilayani, antrian jadi kosong.

Maka front_idx dikembalikan ke -1.


---

self.rear_idx = -1

rear_idx juga dikembalikan ke -1, karena tidak ada data lagi.


---

else:

Kalau data dalam antrian lebih dari satu, maka cukup geser posisi depan.


---

self.front_idx = (self.front_idx + 1) % self.MAXN

Posisi depan dipindah ke data berikutnya.

Karena circular queue, indeks juga bisa muter ke awal kalau sudah sampai akhir array.


---

def peek(self):

Fungsi peek digunakan untuk melihat data paling depan tanpa menghapusnya.

Jadi cuma lihat mahasiswa yang akan dipanggil berikutnya, bukan melayani dia duluan.


---

if self.is_empty():

Mengecek apakah antrian kosong.


---

print("Antrian pendaftaran KRS kosong")

Kalau kosong, tampilkan pesan bahwa tidak ada mahasiswa dalam antrian.


---

return

Fungsi dihentikan.


---

print(f"Mahasiswa paling depan dalam antrian: {self.q[self.front_idx]}")

Menampilkan NPM mahasiswa yang berada di posisi paling depan.

Data tidak dihapus dari antrian.


---

def display(self):

Fungsi display digunakan untuk menampilkan seluruh isi antrian.


---

if self.is_empty():

Mengecek apakah antrian kosong.


---

print("Antrian pendaftaran KRS kosong")

Kalau kosong, tampilkan pesan kosong.


---

return

Fungsi dihentikan.


---

print("Daftar antrian pendaftaran KRS dari depan ke belakang: ", end="")

Menampilkan teks awal sebelum daftar antrian.

end="" membuat output berikutnya tetap berada di baris yang sama.


---

i = self.front_idx

Variabel i dimulai dari posisi depan antrian.

Jadi program akan mencetak data dari mahasiswa paling depan dulu.


---

while True:

Membuat perulangan tanpa batas sementara.

Nanti perulangan ini akan dihentikan pakai break.


---

print(self.q[i], end=" ")

Mencetak data pada indeks i.

end=" " membuat setiap data dipisahkan dengan spasi.


---

if i == self.rear_idx:

Mengecek apakah posisi saat ini sudah sampai ke data paling belakang.


---

break

Kalau sudah sampai data belakang, perulangan dihentikan.


---

i = (i + 1) % self.MAXN

Kalau belum sampai belakang, pindah ke indeks berikutnya.

Karena circular queue, indeks bisa balik ke awal kalau sudah sampai akhir array.


---

print()

Membuat baris baru setelah semua data antrian ditampilkan.


---

def main():

Fungsi utama program.

Di sinilah menu dijalankan.


---

queue = QueueArray()

Membuat objek antrian dari class QueueArray.

Objek ini bernama queue.


---

pilih = 0

Variabel pilih dipakai untuk menyimpan pilihan menu dari pengguna.

Awalnya diberi nilai 0 supaya perulangan bisa mulai.


---

while pilih != 5:

Selama pengguna belum memilih angka 5, program akan terus berjalan.

Angka 5 digunakan untuk keluar dari program.


---

print("\n=== SISTEM ANTRIAN PENDAFTARAN KRS MAHASISWA ===")

Menampilkan judul program.

\n digunakan supaya ada baris kosong sebelum judul.


---

print("1. Daftar Antrian KRS")

Menu nomor 1 untuk memasukkan mahasiswa ke antrian.


---

print("2. Panggil Mahasiswa ke Loket")

Menu nomor 2 untuk memanggil mahasiswa paling depan.


---

print("3. Lihat Mahasiswa Terdepan")

Menu nomor 3 untuk melihat mahasiswa paling depan tanpa menghapus dari antrian.


---

print("4. Tampilkan Antrian")

Menu nomor 4 untuk menampilkan semua mahasiswa dalam antrian.


---

print("5. Keluar")

Menu nomor 5 untuk keluar dari program.


---

try:

try digunakan untuk mencoba menjalankan input.

Ini dipakai supaya program tidak langsung error kalau pengguna memasukkan huruf atau simbol.


---

pilih = int(input("Pilih: "))

Program meminta pengguna memasukkan pilihan menu.

Input diubah menjadi integer menggunakan int().


---

except ValueError:

Kalau input tidak bisa diubah ke angka, maka terjadi ValueError.

Contohnya pengguna memasukkan abc, ya Python bingung. Wajar, bukan dukun.


---

print("Input tidak valid!")

Menampilkan pesan bahwa input salah.


---

continue

Program kembali ke awal perulangan menu.

Jadi tidak lanjut ke pengecekan pilihan.


---

if pilih == 1:

Kalau pengguna memilih 1, program akan menjalankan proses pendaftaran antrian KRS.


---

try:

Mencoba meminta input NPM mahasiswa.


---

val = int(input("Masukkan NPM Mahasiswa: "))

Pengguna diminta memasukkan NPM mahasiswa.

Input diubah ke integer.


---

queue.enqueue(val)

Data NPM mahasiswa dimasukkan ke antrian menggunakan fungsi enqueue.


---

except ValueError:

Kalau NPM yang dimasukkan bukan angka, maka terjadi error input.


---

print("Input tidak valid!")

Menampilkan pesan bahwa input tidak valid.


---

elif pilih == 2:

Kalau pengguna memilih 2, program memanggil mahasiswa dari antrian.


---

queue.dequeue()

Menjalankan fungsi dequeue, yaitu mengeluarkan mahasiswa paling depan dari antrian.


---

elif pilih == 3:

Kalau pengguna memilih 3, program melihat mahasiswa paling depan.


---

queue.peek()

Menjalankan fungsi peek.

Mahasiswa paling depan ditampilkan, tapi tidak dihapus dari antrian.


---

elif pilih == 4:

Kalau pengguna memilih 4, program menampilkan semua isi antrian.


---

queue.display()

Menjalankan fungsi display.


---

elif pilih == 5:

Kalau pengguna memilih 5, program berhenti.


---

print("Program sistem antrian pendaftaran KRS selesai.")

Menampilkan pesan bahwa program selesai.


---

else:

Kalau pilihan bukan 1 sampai 5, maka masuk ke bagian ini.


---

print("Pilihan tidak valid!")

Menampilkan pesan bahwa pilihan menu salah.

Misalnya pengguna memasukkan 9, padahal menu cuma sampai 5. Klasik, baca menu aja kadang manusia gagal.


---

if __name__ == "__main__":

Baris ini mengecek apakah file Python dijalankan langsung.

Kalau iya, maka fungsi main() akan dijalankan.


---

main()

Memanggil fungsi main() agar program mulai berjalan.


---

OUTPUT
<img width="626" height="711" alt="Image" src="https://github.com/user-attachments/assets/c14aa3b9-f0b0-4a97-9fdb-37353890e260" />
---
<img width="753" height="837" alt="Image" src="https://github.com/user-attachments/assets/f32f0d9f-9f88-4261-bca7-4ba49a1eeed8" />
---
<img width="739" height="828" alt="Image" src="https://github.com/user-attachments/assets/6d806187-19c1-4be1-924d-46b9be8cdbb3" />
---

# PENJELASAN OUTPUT

Pada awalnya program menampilkan menu utama:

SISTEM ANTRIAN PENDAFTARAN KRS MAHASISWA 
1. Daftar Antrian KRS
2. Panggil Mahasiswa ke Loket
3. Lihat Mahasiswa Terdepan
4. Tampilkan Antrian
5. Keluar

Bagian ini berarti program meminta pengguna memilih salah satu menu. Pengguna bisa memilih menu untuk mendaftarkan mahasiswa ke antrian, memanggil mahasiswa ke loket, melihat mahasiswa paling depan, menampilkan seluruh antrian, atau keluar dari program.

Saat pengguna memilih menu:

Pilih: 1
Masukkan NPM Mahasiswa: 2112

Artinya pengguna memilih menu Daftar Antrian KRS. Program lalu meminta NPM mahasiswa. NPM 2112 dimasukkan ke dalam antrian, lalu program menampilkan pesan bahwa mahasiswa tersebut berhasil masuk antrian.

Setelah itu pengguna beberapa kali memilih menu nomor 1 lagi dan memasukkan NPM:

2112
2222
2332
2442
2552

Artinya ada 5 mahasiswa yang berhasil masuk ke dalam antrian pendaftaran KRS. Urutan masuknya adalah 2112, 2222, 2332, 2442, lalu 2552.

Kemudian pengguna memilih:

Pilih: 4

Menu nomor 4 adalah Tampilkan Antrian. Program lalu menampilkan:

Daftar antrian pendaftaran KRS dari depan ke belakang: 2112 2222 2332 2442 2552

Artinya urutan mahasiswa dalam antrian dari depan sampai belakang adalah 2112, 2222, 2332, 2442, dan 2552. Mahasiswa dengan NPM 2112 berada paling depan karena dia yang pertama masuk.

Selanjutnya pengguna memilih:

Pilih: 3

Menu nomor 3 adalah Lihat Mahasiswa Terdepan. Program menampilkan:

Mahasiswa paling depan dalam antrian: 2112

Artinya mahasiswa yang akan dilayani paling pertama adalah NPM 2112. Pada bagian ini, data mahasiswa belum dihapus dari antrian karena menu ini hanya melihat, bukan memanggil.

Lalu pengguna memilih menu nomor 2:

Pilih: 2
Mahasiswa dengan NPM 2112 dipanggil ke loket administrasi

Menu nomor 2 digunakan untuk memanggil mahasiswa ke loket. Karena 2112 berada paling depan, maka mahasiswa tersebut dipanggil lebih dulu dan keluar dari antrian.

Setelah itu pengguna terus memilih menu nomor 2, sehingga mahasiswa dipanggil satu per satu:

2222
2332
2442
2552

Urutan pemanggilan mahasiswa menjadi:

2112 - 2222 - 2332 - 2442 - 2552

Urutan ini sama dengan urutan saat mahasiswa masuk ke antrian. Jadi program sudah benar menerapkan prinsip FIFO, yaitu yang masuk duluan akan dilayani duluan.

Setelah semua mahasiswa dipanggil, pengguna memilih menu nomor 2 lagi. Program menampilkan:

Antrian pendaftaran KRS kosong

Artinya sudah tidak ada mahasiswa lagi di dalam antrian. Jadi program tidak bisa memanggil mahasiswa ke loket karena semua sudah selesai dilayani.

Terakhir pengguna memilih:

Pilih: 5
Program sistem antrian pendaftaran KRS selesai.

Menu nomor 5 digunakan untuk keluar dari program. Setelah itu program berhenti berjalan.

LINK YOUTUBE :https://youtu.be/BLwLaG0TFkA?si=r9HBU0eS8Uggh4qq
