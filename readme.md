# Belajar Hosting Web dengan Firebase
## Daftar Isi
- [Persyaratan Dasar](#persyaratan-dasar)
- [Apa itu Firebase Hosting](#apa-itu-firebase-hosting)
- [Mempersiapkan Kode Aplikasi](#mempersiapkan-kode-aplikasi)
- [Membangun Aplikasi](#membangun-aplikasi)
- [Hosting Aplikasi](#hosting-aplikasi)
- [Referensi](#referensi)

### Persyaratan Dasar
- Mengerti pembuatan website sederhana
- Pernah menggunakan nodejs (Karena aplikasi yang dibuat pada pembelajaran ini menggunakan nodejs)
- Pernah menggunakan `git` (Karena aplikasi yang digunakan pada pembelajaran ini akan dicopy menggunakan `git`)

### Apa itu Firebase Hosting
Dikutip dari web firebase.google.com, Firebase Hosting merupakan suatu tempat untuk melakukan hosting konten web yang *production-grade* yang cukup ramah dengan developer. Firebase Hosting ini merupakan bagian dari produk Firebase yang dikelola oleh Google.

Pada Firebase Hosting sebenarnya kita bisa meng-*hosting* aplikasi web yang bersifat statik (hanya html js css saja) ataupun yang bersifat dinamis beserta kemampuan microservices (seperti meletakkan logic server expressjs ataupun APIs).

Namun pada pembelajaran hari ini kita hanya akan menggunakan yang statik saja yah !

### Mempersiapkan Kode Aplikasi
(Pastikan pada langkah ini, git cli / gui sudah terpasang !)

Sebelum kita melakukan Hosting Aplikasi, tentunya kita harus membuat aplikasinya terlebih dahulu. Namun pada pembelajaran kali ini kita tinggal melakukan cloning terhadap repository git yang ada, kemudian akan mencoba untuk meng-*hosting* aplikasi tersebut yah !


Kita hanya perlu melakukan clone repositori yang ada di sini:
```
https://github.com/withered-flowers/learn-firebase-hosting-web
```
Silahkan gunakan clone git dengan cara yang manapun (https ataupun via gh cli)

```bash
# cara 1 (https)
git clone https://github.com/withered-flowers/learn-firebase-hosting-web.git
# cara 2 (gh cli)
gh repo clone withered-flowers/learn-firebase-hosting-web
```

Setelah itu kita akan membuka terminal untuk menginstall package yang dibutuhkan pada aplikasi yang akan di-*hosting*.



### Membangun Aplikasi

### Hosting Aplikasi

### Referensi
- https://firebase.google.com/docs/cli#install_the_firebase_cli