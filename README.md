#  STRATEGY DESIGN PATTERN
**Nama Anggota Kelompok:**<br>
Sherly Agnesya (23100019)<br>
Nopeliba (23100023)<br>
**Mata Kuliah:** Pemrograman Berorientasi Objek II<br>
**Kelas:** STI-A

## 1. PENGERTIAN :
Strategy Pattern adalah salah satu pola desain (design pattern) dalam kategori Behavioral Patterns yang digunakan untuk mendefinisikan sekumpulan algoritma, membungkusnya dalam kelas-kelas terpisah, dan membuatnya dapat dipertukarkan satu sama lain tanpa mengubah kode yang menggunakan algoritma tersebut.

## 2. KAPAN PENGGUNAAAN STRATEGY PATTERN: 
Berikut adalah beberapa situasi di mana Anda harus mempertimbangkan penggunaan pola strategi:
1. Ketika memiliki beberapa algoritma yang dapat digunakan secara bergantian berdasarkan konteks yang berbeda, seperti algoritma pengurutan (pengurutan gelembung, pengurutan gabungan, pengurutan cepat), algoritma pencarian, algoritma kompresi, dll.
2. Ketika ingin merangkum (enkapsulasi) detail implementasi algoritma secara terpisah dari konteks yang menggunakannya, sehingga memungkinkan pemeliharaan, pengujian, dan modifikasi algoritma lebih mudah tanpa memengaruhi kode klien.
3. Pemilihan waktu proses, saat kita perlu memilih dan beralih secara dinamis di antara berbagai algoritma saat proses berlangsung berdasarkan preferensi pengguna, pengaturan konfigurasi, atau status sistem.
4. Mengurangi pernyataan kondisional,  ketika kita  memiliki kelas dengan beberapa pernyataan kondisional yang memilih di antara perilaku yang berbeda, menggunakan pola Strategi membantu menghilangkan kebutuhan akan pernyataan kondisional dan membuat kode lebih modular dan mudah dipelihara.
5. Pengujian dan ekstensibilitas, bila kita ingin memfasilitasi pengujian unit yang lebih mudah dengan mengaktifkan substitusi algoritme dengan objek tiruan atau rintisan.

## 3. KELEBIHAN:
1. Kumpulan algoritma dapat didefinisikan dalam hierarki kelas.<br>
Dengan pola ini, berbagai algoritma yang memiliki fungsi serupa dapat dikelompokkan dalam sebuah hierarki kelas. Hal ini memungkinkan pengguna untuk dengan mudah mengganti algoritma yang digunakan tanpa perlu mengubah arsitektur utama dari aplikasi.
2. Memudahkan penambahan algoritma baru.<br>
Karena setiap algoritma dikemas dalam kelas terpisah dan mengikuti interface yang sama, maka kita dapat dengan mudah menambahkan algoritma baru tanpa harus mengubah kode yang sudah ada.
3. Dapat mengganti strategi saat program sedang berjalan.<br>
Aplikasi dapat secara dinamis mengganti strategi atau algoritma yang digunakan saat program sedang berjalan, sehingga lebih fleksibel dalam menyesuaikan kebutuhan yang berubah.
4. Menghindari penggunaan pernyataan “switch” atau “if-else” yang kompleks.<br>
Dengan menggunakan strategy pattern, pemilihan algoritma dilakukan secara lebih terstruktur dan modular, tanpa perlu menggunakan banyak pernyataan kondisi seperti switch atau if-else yang bisa membuat kode sulit dibaca dan dipelihara.
5. Struktur data yang digunakan dalam algoritma terpisah dari kelas utama.<br>
Karena algoritma diimplementasikan dalam kelas-kelas strategy, struktur data yang digunakan oleh algoritma tidak perlu diakses oleh kelas utama. Ini membuat perubahan dalam algoritma tidak akan berdampak langsung pada kelas utama, sehingga memudahkan pemeliharaan dan pengembangan aplikasi.

## 4. KEKURANGAN:
1. Aplikasi harus mengetahui semua strategi yang ada.<br>
Ketika menggunakan strategy pattern, aplikasi harus tahu semua strategi yang tersedia agar bisa memilih strategi yang tepat untuk situasi tertentu. Hal ini menyebabkan kode menjadi lebih kompleks seiring dengan strategi yang bertambah, penggunaan memori yang lebih besar jika semua strategi dibuat sekaligus, dapat menyebabkan kesusahan dalam mengelola daftar strategi yang terus bertambah.
2. Semua kelas strategi harus memiliki interface yang sama.<br>
Strategy pattern bekerja dengan interface atau kelas abstrak yang harus diikuti semua strategi. Tetapi, tidak semua strategi butuh semua metode dalam interface tersebut sehingga dapat menyebabkan kode tidak berguna atau tidak diimplementasikan dalam beberapa strategi.
3. Perlu membuat dan mengelola banyak objek.<br>
Dalam strategy pattern, biasanya cenderung membuat object untuk context dan object untuk strategy sehingga harus menangani dua objek atau lebih. Hal ini membuat lebih banyak objek yang harus dibuat dan dikelola, saat strategi dibuat dalam jumlah besar maka dapat menyebabkan overhead memori, ketika strategi sering berubah maka harus dibuat objek baru yang dapat mengurangi efisiensi.

## 5. PERBANDINGAN STRATEGY DAN STATE PATTERN:
| Strategy Pattern | State Pattern |
| ---------------- | ------------- |
| Strategy pattern digunakan untuk mengenkapsulasi sekumpulan algoritma terkait, sehingga klien dapat memilih dan menggunakan perilaku yang dapat dipertukarkan saat runtime melalui komposisi dan delegasi. | State pattern digunakan untuk mengelola perubahan perilaku suatu objek berdasarkan kondisi atau status internalnya. |
| Strategy pattern mengenkapsulasi algoritma atau strategi, yang dapat digunakan kembali dalam konteks yang berbeda. | State pattern mengenkapsulasi status objek, yang umumnya spesifik dan tidak dapat digunakan kembali dalam objek lain. |
| Dalam strategy pattern, strategi tidak memiliki referensi ke konteksnya, hanya menyediakan perilaku yang digunakan oleh objek konteks. | Dalam state pattern, setiap state biasanya memiliki referensi ke objek konteks agar dapat mengelola transisi antar state. |
| Dalam strategy pattern, strategi dipilih oleh klien dan dapat diberikan parameter. | Dalam state pattern, state merupakan bagian dari objek konteks, dan objek tersebut akan berpindah dari satu state ke state lain secara internal. |

##  6. CONTOH KODE DALAM JAVA
```java
//Interface
public interface PaymentMethod {
    void pay(int amount);
}
```

```java
//Strategi pembayaran tunai
public class CashPayment implements PaymentMethod {
    @Override
    public void pay(int amount) {
        System.out.println("Bayar Rp " + amount + " pakai uang tunai.");
    }
}
```

```java
//Strategi pembayaran e-wallet
public class EWalletPayment implements PaymentMethod {
    @Override
    public void pay(int amount) {
        System.out.println("Bayar Rp " + amount + " pakai e-wallet.");
    }
}
```

```java
//Strategi pembayaran kartu kredit
public class CreditCardPayment implements PaymentMethod {
    @Override
    public void pay(int amount) {
        System.out.println("Bayar Rp " + amount + " pakai kartu kredit.");
    }
}
```

```java
//Context
public class PaymentSystem {
    private PaymentMethod paymentMethod;

    public void setPaymentMethod(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod;
    }

    public void processPayment(int amount) {
        if (paymentMethod == null) {
            System.out.println("Silakan pilih metode pembayaran dulu.");
        } else {
            paymentMethod.pay(amount);
        }
    }
}
```

```java
//Main class
public class Main {
    public static void main(String[] args) {
        PaymentSystem kasir = new PaymentSystem();

        // Pelanggan bayar pakai uang tunai
        kasir.setPaymentMethod(new CashPayment());
        kasir.processPayment(50000);

        // Pelanggan lain bayar pakai kartu kredit
        kasir.setPaymentMethod(new CreditCardPayment());
        kasir.processPayment(100000);

        // Pelanggan lain bayar pakai e-wallet
        kasir.setPaymentMethod(new EWalletPayment());
        kasir.processPayment(75000);
    }
}
```

##  7. OUTPUT YANG DIHASILKAN
```
Bayar Rp 50000 pakai uang tunai.
Bayar Rp 100000 pakai kartu kredit.
Bayar Rp 75000 pakai e-wallet.
```

#  Referensi:
[Strategy Design - GeeksforGeeks](https://www.geeksforgeeks.org/strategy-pattern-set-1/) <br>
[Strategy Design Pattern in Python - Auth0](https://auth0-com.translate.goog/blog/strategy-design-pattern-in-python/?_x_tr_sl=en&_x_tr_tl=id&_x_tr_hl=id&_x_tr_pto=sge&_x_tr_hist=true)

