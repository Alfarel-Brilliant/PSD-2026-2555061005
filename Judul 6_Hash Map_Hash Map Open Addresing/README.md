# Judul


## Deskripsi Singkat

Program ini merupakan implementasi struktur data **Hash Map** yang digunakan untuk menyimpan dan mengelola data barang pada sebuah toko sederhana. Dalam program ini, setiap barang memiliki **kode barang** sebagai **key** dan **nama barang** sebagai **value**. Key berfungsi sebagai identitas unik yang digunakan untuk menentukan lokasi penyimpanan data di dalam hash table, sedangkan value merupakan informasi barang yang disimpan. Melalui program ini, pengguna dapat memahami proses penambahan data, pencarian data, penghapusan data, serta penampilan seluruh isi tabel.

Struktur data yang diterapkan pada program ini adalah **Hash Map Open Addressing** dengan metode **Linear Probing**. Metode ini bekerja dengan cara menghitung indeks penyimpanan menggunakan fungsi hash. Apabila terjadi **collision**, yaitu ketika dua key menghasilkan indeks yang sama, maka program akan mencari slot kosong berikutnya secara berurutan. Dengan demikian, data tetap dapat disimpan di dalam hash table meskipun terdapat tabrakan indeks. Penerapan metode ini menunjukkan bahwa Hash Map dapat digunakan untuk mempercepat proses pencarian data dibandingkan pencarian secara berurutan.
