# Minpro-2-PBO-SistemPendataanWargaKurangMampu <br>  

# Judul : Sistem Pendataan Warga Kurang Mampu  

---

## 1. Deskripsi Singkat Program  
Pada program ini saya membuat sistem sederhana berbasis CLI untuk membantu proses pendataan warga yang berhak menerima bantuan sosial. di dalam program ini juga bisa menambah data warga, menampilkan daftar warga yang udah di input, mengubah data kalau ada yang salah, dan menghapus data dari daftar. Program ini lebih berfokus pada pendataan warga kurang mampu dan penyaluran bantuan sosial dari pemerintah. Lalu pada sistem ini dikembangkan lebih baik lagi dengan menerapkan konsep Inheritance atau Pewarisan, untuk membagi kategori warga (Warga Lansia dan Warga Disabilitas), pengintegrasian class KriteriaKemiskinan, validasi input yang lebih ketat, serta penyediaan dummy data awal di dalam ArrayList.

---  

## 2. Penjelasan Class & Atribut  
Pada project ini, strukturnya dibagi ke beberapa class, yaitu:  

Pada Package PendataanWarga disini ada :  

* **Warga (superclass)** 
  * nik
  * nama
  * alamat
  * jumlahTanggungan
 
* **WargaLansia (subclass)**
  * umur
  * kondisiKesehatan
 
* **WargaDisabilitas (subclass)**
  * jenisDisabilitas
  * kebutuhanAlatBantu
 
* **KriteriaKemiskinan**
  * idKriteria
  * jenisPekerjaan
  * pendapatanBulanan
  * statusRumah

* **DataPusatWarga**
  * idData
  * tanggalPendataan
  * statusValidasi
  * daftarWargaKurangMampu (ArrayList)  

Pada Package main disini ada :  
* **Main** (Entry point)

---

## 3. Penjelasan tiap Class 

* **Warga**
 * Penjelasan class: Pada class ini saya pakai untuk menyimpan informasi data diri warga.
 * Pada class ini saya menggunakan atribut ber-access modifier private (encapsulation) yaitu nik, nama, alamat, jumlahTanggungan, serta objek kriteria dari class KriteriaKemiskinan.
 * Saya juga menggunakan constructor, getter, setter, serta validasi di setJumlahTanggungan agar nilainya tidak bisa minus (kalau kurang dari 0 bakal otomatis ke 0 lagi ke set), serta method tampilkanInfo() yang nantinya di-override oleh subclass.

* **WargaLansia**
 * Penjelasan class: Class turunan (subclass) pertama dari class Warga yang khusus menampung data warga kategori lansia.
 * Pada class ini saya menggunakan atribut tambahan umur dan kondisiKesehatan.
 * Saya juga menggunakan super pada constructor untuk memanggil atribut induknya, terdapat validasi pada setUmur agar umur lansia minimal 60 tahun, serta menerapkan method overriding pada tampilkanInfo() untuk mencetak data lansia. Pada setUmur juga jika menginput umur dibawah 60, maka tidak dapat dan melakukan isi ulang umur yang sesuai kriteria.

* **WargaDisabilitas**
 * Penjelasan class: Class turunan (subclass) kedua dari class Warga yang khusus menampung data warga kategori penyandang disabilitas.
 * Pada class ini saya menggunakan atribut tambahan jenisDisabilitas dan kebutuhanAlatBantu.
 * Saya juga menggunakan super pada constructor serta menerapkan method overriding pada tampilkanInfo() untuk menampilkan informasi spesifik kebutuhan alat bantu dan jenis disabilitasnya.  

* **KriteriaKemiskinan**
  * Penjelasan class: Pada class ini saya gunakan untuk menampung atau syarat status ekonomi dan kelayakan warga.
  * Atribut yang dipakai meliputi idKriteria, jenisPekerjaan, pendapatanBulanan, dan statusRumah.
  * Pada class ini saya menggunakan validasi pada setPendapatanBulanan agar nilainya tidak bernilai negatif.

* **DataPusatWarga**
  * Penjelasan Class: dan disini pusat pengolahan data dan penyimpanan sementara.
  * Memiliki atribut idData, tanggalPendataan, statusValidasi, serta daftarWargaKurangMampu yang menggunakan ArrayList untuk menampung data-data warga secara dinamis. Kenapa cuma di class ini yang pakai ArrayList? Karena class ini yang bertugas sebagai pengelola/pusat data yang menampung banyak objek warga sekaligus, sedangkan class Warga atau KriteriaKemiskinan fokus membentuk satu struktur data individunya saja.
  * disini penggunaaan (Create, Read, Update, Delete).

* **Main**
  * Penjelasan Class: disini entry point nya sebagai tempat program.
  * disini saya memasukkan perulangan menu dan Scanner untuk membaca input pilihan.
 
---  

## 4. Penjelasan Penerapan Encapsulation & Inheritance  
* **Encapsulation**
* Pada program ini, semua atribut pada setiap class (Warga, WargaLansia, WargaDisabilitas, KriteriaKemiskinan, DataPusatWarga) menggunakan access modifier private, agar variabel tidak bisa diakses secara langsung dari luar class.
* Untuk mengakses dan mengubah nilainya, saya menggunakan method getter dan setter.
* Terdapat validasi data pada setter, seperti :
* setJumlahTanggungan: Jika input minus, otomatis di set ke 0.
* setPendapatanBulanan: Mengembalikan pesan error dan mengatur nilai ke 0 jika input negatif.
* setUmur pada WargaLansia: Memastikan umur lansia minimal 60 tahun (jika kurang dari 60, otomatis diset ke 60).

* **Inheritance**
* Class Warga bertindak sebagai Superclass yang menyimpan data umum (NIK, Nama, Alamat, Tanggungan, Kriteria).
* Class WargaLansia dan WargaDisabilitas bertindak sebagai Subclass yang mewarisi (extends) class Warga.
* Pada Inheritance ini saya menggunakan super pada constructor subclass untuk meneruskan data dasar ke superclass, dan super.tampilkanInfo() untuk memanggil cetakan informasi dari superclass.

---

## 5. Penjelasan Alur Program dan Dokumentasi Output  
Saat program dijalankan, sistem otomatis memanggil method isiDataAwal() di DataPusatWarga untuk mengisikan dummy data awal ke ArrayList, sehingga data warga langsung tampil saat menu Read pertama kali dipilih.  

Pada saat program dijalankan, nanti nya akan menampilkan menu utama di terminal dengan 5 pilihan:  
<img width="224" height="114" alt="image" src="https://github.com/user-attachments/assets/531efc68-2e02-4367-a393-c8fef6045e25" />
