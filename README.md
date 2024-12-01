# Lab9Web.
1. File: header.php
File ini berisi template header HTML standar dan navigasi. Bagian ini digunakan untuk elemen yang muncul di setiap halaman, seperti judul halaman, link CSS, dan menu navigasi.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/css" media="screen" />
</head>
<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="about.php">data</a>
            <a href="kontak.php">about</a>
        </nav>
      
  ![Screenshot 2024-11-29 041739](https://github.com/user-attachments/assets/87017b85-3f54-4ee9-8890-9aeb7cdf48e6)

2. File: footer.php
File ini berisi footer HTML standar. Bagian ini menampilkan elemen footer pada setiap halaman.

Isi File:
<footer>
<p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>

![Screenshot 2024-11-29 041732](https://github.com/user-attachments/assets/d548c902-b407-482c-8bb1-325d150aac02)

3. File: home.php
File ini adalah halaman utama (home page). Di dalamnya menggunakan fungsi require() untuk menyertakan file header.php dan footer.php. Konten utama halaman ditambahkan di antara kedua file tersebut.
<?php require('header.php'); ?>
<div class="content">
    <h2>Ini Halaman Home</h2>
<p>Ini adalah bagian content dari halaman.</p>
</div>
<?php require('footer.php'); ?>

![Screenshot 2024-11-29 041723](https://github.com/user-attachments/assets/15b03916-76e1-452a-a207-2ea5fdd19de2)
