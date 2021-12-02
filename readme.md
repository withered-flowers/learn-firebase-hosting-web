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
- Pernah menggunakan `nodejs` (Karena aplikasi yang dibuat pada pembelajaran ini menggunakan `nodejs`)
- Pernah menggunakan `git` (Karena aplikasi yang digunakan pada pembelajaran ini akan dicopy menggunakan `git`)

### Apa itu Firebase Hosting
Dikutip dari web firebase.google.com, Firebase Hosting merupakan suatu tempat untuk melakukan hosting konten web yang *production-grade* yang cukup ramah dengan developer. Firebase Hosting ini merupakan bagian dari produk Firebase yang dikelola oleh Google.

Pada Firebase Hosting sebenarnya kita bisa meng-*hosting* aplikasi web yang bersifat statik (hanya html js css saja) ataupun yang bersifat dinamis beserta kemampuan microservices (seperti meletakkan logic server expressjs ataupun APIs).

Namun pada pembelajaran hari ini kita hanya akan menggunakan yang statik saja yah !

### Mempersiapkan Kode Aplikasi
(Pastikan pada langkah ini, git cli / gui sudah terpasang !)
Apabila belum, bisa melihat pada langkah instalasi yang ada di sini:
- https://www.petanikode.com/git-install/

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

(Pastikan pada langkah ini, nodejs sudah terpasang !)
Apabila belum, bisa mengunduh file instalasi di sini:
- https://nodejs.org/en/

Bukalah terminal / cmd / powershell pada folder yang sudah diclone dan jalankan `npm install` untuk menginstall package

```bash
# Pindah ke folder learn-firebase-hosting-web
cd /jalur/menuju/learn-firebase-hosting-web
# Pindah ke folder sources yang ada di dalam folder learn-firebase-hosting-web
cd sources
# Jalankan perintah untuk menginstall package
npm install
```

Setelah package untuk menjalankan aplikasi sudah terpasang, kita sudah bisa mencoba untuk melihat aplikasi yang dibuat dalam mode development dengan menjalankan perintah berikut

```bash
npm run dev
```

Apabila berhasil, maka output dari menjalankan `npm run dev` adalah sebagai berikut:

```bash
  vite v2.6.14 dev server running at:

  > Local: http://localhost:3000/
  > Network: use `--host` to expose

  ready in xxxxms.
```

Kemudian kita bisa melihat aplikasi yang sudah jalan dalam mode development ini pada browser kita (http://localhost:3000)

Apabila berjalan dengan lancar, aplikasi yang akan muncul adalah sbb:

![Image Aplikasi](/assets/image01.png)

Ya, pada tahap ini kita sudah selesai dan bisa menjalankan aplikasi kita dalam mode development

Sedikit gambaran tentang aplikasi ini:
- Aplikasi ini dibangun dengan menggunakan Vite sebagai *build tool*, Svelte sebagai *Frontend Framework* dan Tailwind sebagai *CSS Framework*
- Data yang diambil dan dimasukkan ke dalam tabel berasal dari `https://jsonplaceholder.typicode.com/users`
- Ingat dalam membangun aplikasi web yang *kekinian*, memang dibutuhkan *tooling application* seperti ini, tidak hanya sekadar murni html css js kemudian bisa langsung digunakan yah !

### Membangun Aplikasi
Setelah sudah melihat aplikasi yang dibuat dalam mode development, sekarang kita akan membangun aplikasi ini supaya siap untuk masuk dalam tahap production dan siap di*hosting*.

Mengapa ada perbedaan antara mode development dan production?
- Dalam mode development, aplikasi tentunya akan ada lebih banyak informasi debugging yang diberikan oleh *build tool* yang ada (Vite), sedangkan pada mode production, tidak ada informasi debugging yang diberikan lagi.
- Dalam mode development, umumnya ukuran size aplikasi akan lebih besar, sedangkan pada mode production, umumnya karena sudah di-*stripped-down* dan di-*minified* dan di-*compress*, ukuran aplikasi bisa jauh menjadi lebih kecil.
- Sebagai perbandingan dari ukuran network pada browser (`Inspect Network`), ukuran aplikasi yang dibuat pada pembelajaran ini dalam mode development adalah `324.73 KB`, sedangkan pada mode production adalah `12.33 KB`. Silahkan dihitung lebih kecil berapa kali lipat.

Langkah untuk membangun aplikasi ini adalah dengan menjalankan perintah berikut
```
npm run build
```

Apabila berhasil, maka output dari menjalankan `npm run build` adalah sebagai berikut:

```text
> vite build

vite v2.6.14 building for production...
transforming (7) node_modules\svelte\index.mjs
warn - You have enabled the JIT engine which is currently in preview.
warn - Preview features are not covered by semver, may introduce breaking changes, and can change at any time.
✓ 8 modules transformed.
dist/index.html                  0.49 KiB
dist/assets/index.390f6a6f.js    3.11 KiB / gzip: 1.52 KiB
dist/assets/index.b2b4ee34.css   3.57 KiB / gzip: 1.40 KiB
dist/assets/vendor.2b6b50fb.js   3.22 KiB / gzip: 1.49 KiB
```

(Ada kemungkinan angka yang ada di akhir bisa berbeda, abaikan saja bila berbeda yah)

Perhatikan bahwa sampai pada langkah ini, semua file yang di-bangun ada pada folder `dist`

Kemudian untuk menjalankan aplikasi yang sudah dibangun pada mode production ini, bisa menggunakan perintah berikut

```bash
npm run serve
```

Apabila berhasil, maka output dari menjalankan `npm run serve` adalah sebagai berikut:

```bash
> svelte-data-fetcher@0.0.0 serve
> vite preview

> Local: http://localhost:5000/
> Network: use `--host` to expose
```

Kemudian kita bisa melihat aplikasi yang sudah jalan dalam mode production ini pada browser kita (http://localhost:5000)

Perhatikan port yang digunakan berbeda (development pada port 3000 dan production di port 5000)

(Demo aplikasi untuk production juga dapat dilihat pada https://040an5al6bjqbbv6vq7vb2cg6qt8on6144rs180fa4s36ne4sjds7q8.siasky.net/)

Selanjutnya kita akan memasuki bagian terpenting dari pembelajaran ini: Hosting aplikasi ke Firebase Hosting !

### Hosting Aplikasi
(Pastikan pada langkah ini, Anda sudah memiliki sebuah akun GMail dan firebase cli sudah terpasang !)
Apabila belum memiliki akun GMail bisa membuat akun GMail di https://accounts.google.com/signup/
Apabila belum memasang firebase cli, dapat dilihat panduannya di https://firebase.google.com/docs/cli?hl=id

Pertama-tama yang harus dilakukan adalah kita harus melakukan login terlebih dahulu ke dalam firebase cli.

Login dapat dilakukan dengan perintah

```bash
firebase login
```

Ketika perintah ini dijalankan, maka akan diminta untuk membuka browser untuk melakukan login akun GMail yang dimiliki.

(Apabila diminta untuk memperbolehkan Firebase untuk mengambil data penggunaan CLI, pilih saja No)

![Image Firebase CLI](/assets/image02.png)

(Apabila diminta untuk percaya terhadap Firebase CLI, pilih saja Allow)

![Image Firebase Authenticate](/assets/image03.png)

Apabila berhasil login, akan muncul tulisan seperti berikut
```bash
✔  Success! Logged in as xxx@gmail.com
```

Selanjutnya kita akan memulai untuk inisialisasi project hosting Firebase.

Hal ini dapat dilakukan dengan perintah
```bash
firebase init hosting
```

**Pastikan** melakukan perintah di atas, pada folder `sources` yang ada di repositori yang sudah diclone (`.../learn-firebase-hosting-web/sources`)

Kemudian kita akan diberikan opsi opsi sebagai berikut
```bash
# Pilih opsi yang digunakan
# kita akan membuat projek yang baru
Please select an option: `Create a new project`

# Masukkan nama project id yang kita inginkan
# Tidak bisa diganti !
Please specify a unique project id: `Silakan masukkan project id (bebas)`

# Masukkan nama project
# bila tidak diisi, akan mengacu pada unique project id di atas
What would you like to call your project? (defaults to your project ID)? `Silakan masukkan nama project (bebas)`

# Pilih folder utama yang akan digunakan untuk hosting
# Karena pada saat melakukan npm run build tadi foldernya adalah di dist
# Maka kita harus mengganti folder utama menjadi folder dist juga
What do you want to use as your public directory? `dist`

# Tergantung dari project yang dibuat
# Apabila ingin membuat single page application
# Gunakan yes
# Bila tidak gunakan no
# Pada pembelajaran ini baik yes maupun no tidak ada dampak signifikan
Configure as a single-page app? (rewrite all urls to /index.html)? `No`

# Bisa juga sebenarnya menggunakan cara push-to-deploy dari github
# Jadi ketika Github melakukan push, akan secara otomatis ter-hosting
# Di luar scope pembelajaran ini
Set up automatic builds and deploys with GitHub? `No`

# Ketika kita melakukan npm run build, file index.html sudah dibentuk
# Hal ini akan ditanyakan karena firebase sebenarnya ada template awal
# untuk index.html sendiri
# Kita skip, karena kita akan menggunakan index.html versinya kita
File dist/index.html already exists. Overwrite? `No`
```

Apabila sudah memilih perintah di atas, akan muncul output seperti di bawah ini
```bash
i  Skipping write of dist/index.html

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...

✔  Firebase initialization complete!
```

Dan itu artinya project kita sudah siap untuk di-hosting !

Bagaimana cara untuk melakukan hostingnya?

Kita cukup menggunakan perintah berikut:
```bash
firebase deploy
```

Apabila berhasil, akan muncul output seperti di bawah ini
```bash
=== Deploying to 'nama-project-id-yang-dipilih'...

i  deploying hosting
i  hosting[nama-project-id-yang-dipilih]: beginning deploy...
i  hosting[nama-project-id-yang-dipilih]: found 6 files in dist
✔  hosting[nama-project-id-yang-dipilih]: file upload complete
i  hosting[nama-project-id-yang-dipilih]: finalizing version...
✔  hosting[nama-project-id-yang-dipilih]: version finalized
i  hosting[nama-project-id-yang-dipilih]: releasing new version...
✔  hosting[nama-project-id-yang-dipilih]: release complete

✔  Deploy complete!

Project Console: https://console.firebase.google.com/project/nama-project-id-yang-dipilih/overview
Hosting URL: https://nama-project-id-yang-dipilih.web.app
```

Perhatikan di atas sudah mendapatkan `Hosting URL`, silakan dibuka halaman tersebut, dan *voila*, kita sudah berhasil melakukan hosting aplikasi web yang kita buat sebelumnya, dengan domain *.web.app, dan sudah HTTPS !

Selamat membuat aplikasi web dan ditunggu yah untuk hosting web yang Anda buat sendiri !
### Referensi
- https://vitejs.dev/
- https://svelte.dev/
- https://tailwindcss.com/
- https://nodejs.org/en/
- https://www.petanikode.com/git-install/
- https://firebase.google.com/docs/cli#install_the_firebase_cli