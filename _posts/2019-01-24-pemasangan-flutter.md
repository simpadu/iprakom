---
layout: post
title:  "Pemasangan Flutter"
date:   2019-01-24 14:11:30 +0700
categories: pemrograman, flutter
---

Materi ini akan membahas bagaimana memasang **Flutter** agar dapat digunakan untuk mengembangkan aplikasi pada Android atau iOS.

Hal yang menjadi kendala untuk mengembangkan sebuah aplikasi berbasis Android atau iOS adalah borosnya penggunaan memori komputer karena harus menjalankan _emulator_ dan berkali-kali melakukan proses _build_ agar dapat melihat pratinjau yang tentu saja memakan waktu yang cukup lama. 

Namun dengan menggunakan fasilitas _hot reload_ yang ditawarkan **Flutter**, hal tersebut sekarang menjadi menyenangkan, bahkan pada saat menggunakan perangkat aslinya untuk melakukan uji coba dan pratinjau, fasilitas ini bekerja dengan baik.

Untuk membangun sebuah aplikasi _mobile_ di Android atau iOS dengan Flutter, tentunya akan membutuhkan perlengkapan tempur yang cukup sesuai dengan Sistem Operasi yang kita gunakan, berikut adalah macamnya :

* Windows : 
    * Versi Windows 7 keatas 64-bit.
    * Kapasitas Ruang _Disk_ sebesar 400 MB
    * Windows PowerShell versi 5 ke atas
    * Aplikasi Git, dan pastikan perintah `git` dapat dijalankan melalui _command_ atau _PowerShell_
* Linux :
    * Distro apapun dengan versi Sistem Operasi 64-bit.
    * Kapasitas Ruang _Disk_ sebesar 600 MB belum termasuk IDE dan _Emulator_ yang akan digunakan
    * Beberapa aplikasi yang biasanya sudah terpasang dan seharusnya ada :
        - `bash`
        - `curl`
        - `git`
        - `mkdir`
        - `rm`
        - `unzip`
        - `which`
        - `xz-utils`
        - `libglu1-mesa`
* MacOS :
    * Versi Sistem Operasi sebaiknya menggunakan 64-bit
    * Kapasitas Ruang _Disk_ sebesar 700 MB belum termasuk IDE dan _Emulator_ yang akan digunakan.
    * Beberapa aplikasi yang biasanya sudah terpasang dan seharusnya ada :
        - `bash`
        - `curl`
        - `git`
        - `mkdir`
        - `rm`
        - `unzip`
        - `which`

Selanjutnya yang perlu disiapkan adalah _Integrated Development Environment_ (IDE) dimana biasanya bergantung dengan selera masing-masing, yang biasanya digunakan adalah IDE berikut :

* Android Studio dengan versi 3 ke atas
* Intellij IDEA Community atau Ultimate versi 2017.1
* Visual Studio Code

cukup pilih salah satu saja.

Setelah IDE terpasang, pada masing-masing IDE perlu dipasang _plugins_ untuk : 

* Flutter
* Dart

_Plugins_ Flutter sendiri digunakan untuk mempercepat proses pembentukan _template_ proyek dan beberapa utilitas lain, sedangkan Dart, karena memang bahasa yang digunakan oleh Flutter adalah bahasa Dart ini.

Tidak perlu takut karena bahasa Dart ini intuitif dan mirip seperti JavaScript, C, PHP, atau apapun yang pernah kita pelajari, kecuali bahasa ibu dan bahasa qolbu.. apalagi bahasa isyarat 😜

Cara pemasangan _plugins_ pada Intellij IDEA, cukup masuk ke menu **Preference** kemudian pilih menu **Plugins** dan cari _plugins_ Flutter dan Dart seperti gambar berikut :

![Pemasangan Plugin Flutter di Intellij IDEA](2019-01-24-plugin-idea.png)

Sedangkan untuk pemasangan _plugins_ pada Visual Studio Code, ada pada menu **Extensions** dan carilah ekstensi dengan nama Flutter dan Dart seperti gambar berikut :

![Pemasangan Plugin Flutter di Visual Studio Code](2019-01-24-plugin-vsc.png)

Untuk pemasangan _plugins_ di Android Studio Code kurang lebih caranya sama seperti pemasangan _plugins_ pada Intellij IDEA, karena memang Android Studio Code menggunakan Intellij IDEA sebagai basisnya, dan terutama karena saya tidak melakukan pemasangan Android Studio Code 😆.

Setelah _plugins_ terpasang pada IDE, selanjutnya kita akan melakukan pemasangan Flutter yang kita dapatkan dari tautan [ini](https://flutter.io/docs/get-started/install)

Cara pemasangannya pun cukup mudah, hanya dengan melakukan ekstrak berkas yang telah diunduh, kemudian konfigurasi _environment variable_ agar kita dapat langsung mengetikan perintah `flutter` pada _command_.

Setelah terpasang dan kita dapat memanggil perintah `flutter` dari _command_, coba jalankan perintah berikut : 

```
flutter doctor
```

Dan pastikan mendapatkan hasil kurang lebih seperti berikut :

![Hasil Flutter Doctor](2019-01-24-flutter-doctor.png)

Hasil tersebut ada catatan di bagian Android Studio, karena memang saya tidak memasang aplikasi tersebut, dan bukan menjadi masalah.

Selanjutnya cukup berkata basa basi, karena pemrograman tanpa kode itu omong kosong. Kita lihat cuplikan kode berikut pada berkas `main.dart` :

```
import 'package:flutter/material.dart';

void main() {
  runApp(new MaterialApp(
    home: new MyApp()
  ));
}

class MyApp extends StatefulWidget {
  @override
  _State createState() => new _State();
}

class _State extends State<MyApp> {
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text('Judul Aplikasi'),
      ),
      body: new Container(
        padding: new EdgeInsets.all(32.0),
        child: new Center(
          child: new Column(
            children: <Widget>[
              new Text('Hai, selamat datang!')
            ],
          ),
        ),
      ),
    );
  }
}
```

Kode di atas akan berangkat dari _method_ `main`, yang akan menjalankan aplikasi dari instan `MaterialApp` yang isi didalamnya adalah instan dari kelas `MyApp`.

Kelas `MyApp` sendiri sebetulnya mewarisi kelas `StatefulWidget`, yaitu _widget_ yang secara dinamis dapat merubah isinya tanpa bergantung oleh parameter awal pada saat pembentukan. Apa itu _widget_? Saat kita membangun aplikasi dengan Flutter, kita akan menyusun tampilan tatap muka dengan _widget_, atau bisa diistilahkan lebih membumi dengan kata komponen. Komponen atau _widget_ ini dalam Flutter akan memiliki salah satu sifat, yaitu _stateful_ atau _stateless_.

_Stateless widget_ di sisi lain adalah _widget_ yang tidak perlu mengatur keadaan internal, semua parameter sudah diatur pada saat pembentukan awal instan dari objek ini.

Di dalam kelas `MyApp` melakukan `override` terhadap _method_ `createState()` milik kelas `StatefulWidget` yang akan kita isi dengan instan dari kelas `_State` yang akan dideklarasikan di baris berikut.

Deklarasi kelas berikutnya adalah kelas `_State` yang mewarisi kelas `State`, di dalam kelas ini kita melakukan _override_ terhadap _method_ `build` dengan sebuah parameter `BuildContext` disana.

Isi _method_ `build` ini hanya langsung mengembalikan nilai instan dari `Scaffold`, `Scaffold` sendiri sebetulnya komponen yang memiliki _bar_ aplikasi di atas dan isi dibawahnya.

Pada tutorial ini, _bar_ aplikasi akan terdiri dari sebuah teks `Judul Aplikasi`, sedangkan dibawahnya akan memiliki beberapa tumpuk _layout_ yang menghasilkan teks `Hai, selamat datang!`.

Apabila kode tersebut dijalankan, proses awalnya akan memakan waktu cukup banyak karena perlu adanya konversi kode dari _Dart_ ke bahasa _native_. Hasilnya kurang lebih akan terlihat seperti gambar berikut :

![Gambar Preview Hasil Flutter](2019-01-24-demo.png)

Begitulah awal kita memasang dan memulai sebuah proyek aplikasi _mobile_ di Android atau iOS.