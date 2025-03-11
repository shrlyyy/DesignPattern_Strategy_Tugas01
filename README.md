# DesignPattern_Strategy_Tugas01
Pemrograman Berorientasi Objek 2
Strategy Pattern

Reference
https://www.geeksforgeeks.org/strategy-pattern-set-1/
https://auth0-com.translate.goog/blog/strategy-design-pattern-in-python/?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=id&_x_tr_pto=sge&_x_tr_hist=true 

## PENGERTIAN :
 Strategy Pattern adalah salah satu pola desain (design pattern) dalam kategori Behavioral Patterns yang digunakan untuk mendefinisikan sekumpulan algoritma, membungkusnya dalam kelas-kelas terpisah, dan membuatnya dapat dipertukarkan satu sama lain tanpa mengubah kode yang menggunakan algoritma tersebut.

## KAPAN PENGGUNAAAN STRATEGY PATTERN: 
Berikut adalah beberapa situasi di mana Anda harus mempertimbangkan penggunaan pola Strategi:
1. Ketika memiliki beberapa algoritma yang dapat digunakan secara bergantian berdasarkan konteks yang berbeda, seperti algoritma pengurutan (pengurutan gelembung, pengurutan gabungan, pengurutan cepat), algoritma pencarian, algoritma kompresi, dll.
2. Ketika ingin merangkum ( Enkapsulasi) detail implementasi algoritma secara terpisah dari konteks yang menggunakannya, sehingga memungkinkan pemeliharaan, pengujian, dan modifikasi algoritma lebih mudah tanpa memengaruhi kode klien.
Pemilihan Waktu Proses, Saat kita perlu memilih dan beralih secara dinamis di antara berbagai algoritma saat proses berlangsung berdasarkan preferensi pengguna, pengaturan konfigurasi, atau status sistem.
Mengurangi Pernyataan Kondisional,  Ketika kita  memiliki kelas dengan beberapa pernyataan kondisional yang memilih di antara perilaku yang berbeda, menggunakan pola Strategi membantu menghilangkan kebutuhan akan pernyataan kondisional dan membuat kode lebih modular dan mudah dipelihara.
Pengujian dan Ekstensibilitas, Bila kita ingin memfasilitasi pengujian unit yang lebih mudah dengan mengaktifkan substitusi algoritme dengan objek tiruan atau rintisan. Selain itu, pola Strategi memudahkan perluasan sistem dengan algoritme baru tanpa mengubah kode yang ada.

## KELEBIHAN:
Kumpulan algoritma dapat didefinisikan dalam hierarki kelas.
Dengan pola ini, berbagai algoritma yang memiliki fungsi serupa dapat dikelompokkan dalam sebuah hierarki kelas (bikin kelas baru). Hal ini memungkinkan pengguna untuk dengan mudah mengganti algoritma yang digunakan tanpa perlu mengubah arsitektur utama (main) dari aplikasi.
Memudahkan penambahan algoritma baru.
Karena setiap algoritma dikemas dalam kelas terpisah dan mengikuti interface yang sama, maka kita dapat dengan mudah menambahkan algoritma baru tanpa harus mengubah kode yang sudah ada.
Dapat mengganti strategi saat program sedang berjalan.
Aplikasi dapat secara dinamis mengganti strategi atau algoritma yang digunakan saat program sedang berjalan, sehingga lebih fleksibel dalam menyesuaikan kebutuhan yang berubah.
Menghindari penggunaan pernyataan “switch” atau “if-else” yang kompleks.
Dengan menggunakan strategy pattern, pemilihan algoritma dilakukan secara lebih terstruktur dan modular, tanpa perlu menggunakan banyak pernyataan kondisi seperti switch atau if-else yang bisa membuat kode sulit dibaca dan dipelihara.
Struktur data yang digunakan dalam algoritma terpisah dari kelas utama.
Karena algoritma diimplementasikan dalam kelas-kelas strategy, struktur data yang digunakan oleh algoritma tidak perlu diakses oleh kelas utama. Ini membuat perubahan dalam algoritma tidak akan berdampak langsung pada kelas utama, sehingga memudahkan pemeliharaan dan pengembangan aplikasi.




### KEKURANGAN:
Aplikasi harus mengetahui semua strategi yang ada.
Ketika menggunakan strategy pattern, aplikasi harus tahu semua strategi yang tersedia agar bisa memilih strategi yang tepat untuk situasi tertentu. Hal ini menyebabkan kode menjadi lebih kompleks seiring dengan strategi yang bertambah, penggunaan memori yang lebih besar jika semua strategi dibuat sekaligus, dapat menyebabkan kesusahan dalam mengelola daftar strategi yang terus bertambah.
Semua kelas strategi harus memiliki interface yang sama.
Strategy pattern bekerja dengan interface atau kelas abstrak yang harus diikuti semua strategi. Tetapi, tidak semua strategi butuh semua metode dalam interface tersebut sehingga dapat menyebabkan kode tidak berguna atau tidak diimplementasikan dalam beberapa strategi.
Perlu membuat dan mengelola banyak objek.
Dalam strategy pattern, biasanya cenderung membuat object untuk context dan object untuk strategy sehingga harus menangani dua objek atau lebih. Hal ini membuat lebih banyak objek yang harus dibuat dan dikelola, saat strategi dibuat dalam jumlah besar maka dapat menyebabkan overhead memori, ketika strategi sering berubah maka harus dibuat objek baru yang dapat mengurangi efisiensi.
