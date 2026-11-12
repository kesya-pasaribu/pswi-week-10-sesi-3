*/
Nama: Kesya Elisa Martauli Pasaribu
Nim : 41426003
Prodi : D-IV TRPL
/*

1. Cara Menjalankan 

   Disini aku buat file html dan js nya dulu kemudian,  di html aku sambungkan file js  
   kemudian di file html aku klik kanan pilih "Open With Live Server"
   baru di situlah aku dapat melihat hasil codingan java script kita.


2. tahapan perubahan kode :

A. Struktur HTML Form (index.html):
   saya menambahkan elemen <form> yang berisi input teks dengan atribut required, tombol submit, elemen <p id="pesan"> untuk status (menggunakan role="status" agar ramah aksesibilitas/screen reader), dan elemen <ul> penampung list peserta.\

B. Manajemen State dan Penambahan Data main.js 
   Saya mendeklarasikan state berupa array kosong let peserta = [] dan penghitung ID lokal let berikutnya = 1. Saat form disubmit (submit), fungsi event.preventDefault() dipanggil agar halaman tidak melakukan refresh otomatis. Nilai input dibersihkan dari spasi berlebih menggunakan trim()

C. Rendering Dinamis & Tombol Hapus:
   Fungsi render() membersihkan isi list lama menggunakan daftar.replaceChildren() (cara aman DOM manipulation), lalu meloop data peserta untuk membuat elemen <li>, <span> untuk nama, dan <button> Hapus yang dilengkapi atribut unik.

D. Event Delegation:
   Memasang event listener ke setiap tombol hapus satu per satu (yang boros memori jika data banyak), Saya cukup memasang satu event listener pada elemen pembungkusnya (daftar / <ul>). Dengan bantuan method .closest("button[data-id]"), sistem bisa mendeteksi tombol mana yang diklik secara akurat meskipun tombol tersebut dibuat secara dinamis.



 3. Hasil Uji 
A. Submit Enter:
   Mengetik nama valid lalu tekan Enter atau klik tombol Tambah Hasilnya, Item berhasil dirender ke DOM dengan ID yang sesuai

B. Nama Spasi Saja:
   Mengisi input hanya dengan spasi (" ") lalu submit Hasilnya, State peserta tidak bertambah dan pesan peringatan muncul


C. Hapus Dinamis:
   Mengklik tombol "Hapus" pada salah satu item list Hasilnya, Tombol dinamis berfungsi dengan baik melalui teknik event delegation



4. Batasan 

1. Validasi input yang diterapkan masih berupa validasi dasar di sisi klien (seperti mengecek apakah input nama kosong atau hanya berisi spasi) tanpa bantuan framework atau aturan validasi tingkat lanjut.

2. Program ini berfokus murni pada manipulasi DOM, penanganan event form, dan event delegation secara lokal di sisi klien. 

3. Data peserta yang dimasukkan hanya disimpan di dalam memori (state array JavaScript). Ketika halaman web direload (dimuat ulang), state memori akan kembali ke awal dan data yang telah ditambahkan akan hilang. Program ini belum menggunakan penyimpanan permanen seperti LocalStorage, SessionStorage, atau basis data server.   