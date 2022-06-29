---
layout: post
title: Cara Install Git dan GitHub
subtitle: OS Linux
description: Cara Install Git dan Github di komputer
date: 2022-06-25 11:00:00 -0400
background: '/img/posts/03.jpg'
categories: [Github, Coding]
permalink: /cara-install-git/
lang: id
---

# Cara Install Git dan GitHub
<hr/>

## Cara Install Git di Linux

### Memperbaharui Sistem 
  
Sebelum memulai proses instalasi, kita harus memastikan untuk memperbarui program yang sudah ada di dalam komputer, dengan menjalankan perintah ini di dalam Terminal 
  
Untuk membuka terminal kamu bisa menggunakan short-cut : CTRL+alt+T
  
  ```bash
  sudo apt update
  sudo apt upgrade  
  ```
  
### Instalasi Git
  
Kemungkinan besar, kamu sudah memiliki Git di dalam komputer kamu, namun untuk memastikan kita mempunyai Versi Git yang terbaru, jalankan perintah ini
  
```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```
### Melihat Versi Git 
   
Setelah semua berjalan, harusnya kamu sudah memiliki versi Git terbaru di dalam komputer. Untuk mengetahui versi Git yang ada di komputer kamu :
   
```bash
git --version
```
   
## Menghubungkan Git 
   
Untuk menggunakan Git dengan benar, kita harus memberitahukan pada Git siapa kita, Jadi Git bisa menghubungkan kita (melalui jaringan komputer) dengan GitHub.
   
Perintah di bawah ini akan membuat Git bisa mengenal kita (local komputer).
   
Pastikan kamu mengisi dengan nama pengguna dan email kamu yang sebenarnya.
   
Nama Kamu dan Email yang di gunakan boleh beda dengan nama pengguna dan email yang kamu daftarkan saat membuat akun GitHub.
   
Dan jangan hapus tanda kutipnya ya, karena itu di perlukan untuk menjalankan perintah.

```bash
git config --global user.name "Nama Kamu"
git config --global user.email "emailkamu@domain.com"
```

__Update Terbaru__ : Git merubah nama cabang (branch) bawaan dalam repositori pembuatan baru, dari _Master_ ke __Main__

Pastikan kamu memperbaharui nya juga, dengan menjalankan perintah ini 

```bash
git config --global init.defaultBranch Main
```

Perintah di bawah ini, untuk tampilan terminal jadi menarik.
Jadi nanti, saat kamu bekerja menggunakan Git di terminal, kamu akan melihat perintah dengan warna berbeda.  

```bash
git config --global color.ui auto
```

Periksa apakah semua proses sudah berjalan dengan benar, dengan menjalankan printah ini 

```bash
git config --get user.name
git config --get user.email
```

Jika hasil yang keluar di terminal sesuai dengan nama pengguna dan email kamu, artinya Git sudah mengenal komputer kamu.



## Cara Menghubungkan Git dan Github

### Buat akun Github  

Buka [Github.com](https://github.com/) dan buat akun baru, atau kamu bisa langsung masuk jika sudah memiliki akun.


### Membuat SSH Key

SSH key adalah autentikasi ganda, ibaratnya tuh, seperti kunci yang hanya bisa dipakai oleh kamu saja. Karena enkripsinya menggunakan kriptografi membuat SSH key lebih sulit untuk bisa di eksploitasi.

SSH key digunakan untuk mengotorisasi saat kamu ingin masuk ke sebuah server, dalam hal ini server GitHub ya, tanpa harus mengetikan password.

SSH keys ini, akan membuat proses update repo ke GitHub menjadi lebih simple, karena kamu tidak perlu lagi, menuliskan nama pengguna dan password, setiap kamu ingin mengirimkan perubahan ke GitHub.

Pertama, kamu lihat apakah kamu memiliki algoritma Ed25519 SSH key.

Jalan kan perintah ini di terminal untuk memeriksa 

```bash
ls ~/.ssh/id_ed25519.pub
```

Kalo terminal memberikan hasil "No such file or directory" berarti kamu belum punya.

Klo sudah ada kamu bisa skip proses di bawah ini, dan langsung ke proses "Menghubungkan SSH Key dengan GitHub"

__Perhatian !__

Perintah -C yang di ikuti dengan alamat email kamu, harus di ikut sertakan, untuk memastikan GitHub mengetahui siapa kamu.

Untuk membuat SSH key, kamu jalankan perintah ini :

```bash
 ssh-keygen -t ed25519 -C emailkamu@domain.com
```

Saat keluar permintaan di terminal, yang menanyakan lokasi yang ingin di gunakan untuk menyimpan, langsung tekan saja Enter.

Selanjutnya, dia akan menanyakan password, masukan saja password pilihan kamu, tidak pake password juga bisa.

## Menghubungkan SSH Key dengan GitHub

Sekarang, kamu harus memberitahu GitHub SSH Key kamu. Jadi nanti, saat kamu melakukan _git push_ kamu tidak perlu lagi input password.

Pertama, masuk ke GitHub, klik tanda panah kecil yang ada di sebelah kanan foto profil kamu, lalu pilih _setting_ (pengaturan).   

Setelah _setting_ terbuka, lihat menu di sebelah kiri kamu, cari dan pilih _SSH and GPG keys_

Klik tombol hijau yang ada di sebelah kanan atas, yang bertuliskan "New SSH Key". Beri nama biar kamu ingat, SSH Key untuk apa itu. 

Biarkan terbuka, saat kamu mengambil SSH key yang ada di komputer kamu, untuk di taruh di GitHub.

Jalankan perintah ini

```bash
cat ~/.ssh/id_ed25519.pub
```
Copy file yang keluar di terminal kamu, di mulai dengan __ssh-ed25519__ dan di akhiri dengan email kamu.

Short-cut untuk meng-copy tulisan yang ada di terminal : CTRL+shift+C
Dan untuk menempel (paste) : CTRL+shift+C

Sekarang, balik lagi ke halaman GitHub yang tadi saya minta jangan di tutup, lalu tempel kode yang kamu dapat dari terminal ke kotak yang ada tulisan __key__.

Lalu klik, _Add SSH key_. 

Yes! Kamu sudah berhasil menambahkan SSH key ke GitHub.

### Periksa koneksi SSH

Sekarang, kamu tinggal memastikan apakah komputer kamu sudah terhubung dengan GitHub atau tidak, dengan menjalankan perintah ini :

```bash
ssh -T git@github.com
```

Kalo keluar hasil seperti gambar di bawah ini artinya kamu sudah berhasil

![ssh](./img/post/ss-succeed.png)

Selamat, sekarang kamu sudah bisa menggunakan Git dan GitHub di komputer kamu !


## Catatan

Untuk tutorial cara install Git, saya mengikuti tutorial dari [The Odin Project] (https://www.theodinproject.com/lessons/foundations-setting-up-git)
  
Kenapa saya menggunakan The Odin Project?
  
Karena menurut saya, saat tulisan ini di buat (ditahun 2022) perintah konfigurasi Git lebih update dan mudah untuk di ikuti untuk orang awam. 
  
Dan karena saya sudah berhasil mencobanya sendiri.
