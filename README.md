# Lab9Web.
 File: home.php
File ini adalah halaman utama (home page). Di dalamnya menggunakan fungsi require() untuk menyertakan file header.php dan footer.php. Konten utama halaman ditambahkan di antara kedua file tersebut.

<?php require('header.php'); ?>
<div class="content">
    <h2>Ini Halaman Home</h2>
<p>Ini adalah bagian content dari halaman.</p>
</div>
<?php require('footer.php'); ?>

![Screenshot 2024-11-29 041723](https://github.com/user-attachments/assets/8e300c7d-bbdd-400e-92e7-c5ca4e41996a)

File: about.php
File ini adalah halaman "Tentang" (About). Struktur file serupa dengan home.php, tetapi konten diubah sesuai dengan topik halaman.

<?php require('header.php'); ?>
<div class="content">
<h2>Ini Halaman About</h2>
<p>Ini adalah bagian content dari halaman.</p>
</div>
<?php require('footer.php'); ?>

![Screenshot 2024-11-29 041732](https://github.com/user-attachments/assets/c774c010-4dc4-4085-a4b1-ab8e89cb80bb)

ini adalah halaman utama kontak
File: footer.php
File ini berisi footer HTML standar. Bagian ini menampilkan elemen footer pada setiap halaman.

<footer>
<p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>

![image](https://github.com/user-attachments/assets/95a8620f-1449-4de7-83bf-9da9300a3c76)

Pertanyaan dan Tugas
Implementasikan konsep modularisasi pada kode program praktikum 8 tentang
database, sehingga setiap halamannya memiliki template tampilan yang sama.

ini adalah halaman utama
<?php
include("koneksi.php");

// Query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);

if (!$result) {
    die("Query gagal: " . mysqli_error($conn));
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<body>
<div class="container">
    <h1>Data Barang</h1>
    <nav>
    <a href="index.php">Home</a>
    <a href="data.php">Data</a>
    <a href="about.php">About</a>
</nav>

    <div class="main">
        <table border="1">
            <thead>
                <tr>
                    <th>Gambar</th>
                    <th>Nama Barang</th>
                    <th>Kategori</th>
                    <th>Harga Beli</th>
                    <th>Harga Jual</th>
                    <th>Stok</th>
                    <th>Aksi</th>
                </tr>
            </thead>
            <tbody>
                <?php if ($result && mysqli_num_rows($result) > 0): ?>
                    <?php while ($row = mysqli_fetch_array($result)): ?>
                        <tr>
                            <td>
                                <img src="gambar/<?= htmlspecialchars($row['gambar']); ?>" 
                                     alt="<?= htmlspecialchars($row['nama']); ?>" 
                                     style="width:100px; height:auto;">
                            </td>
                            <td><?= htmlspecialchars($row['nama']); ?></td>
                            <td><?= htmlspecialchars($row['kategori']); ?></td>
                            <td><?= htmlspecialchars($row['harga_beli']); ?></td>
                            <td><?= htmlspecialchars($row['harga_jual']); ?></td>
                            <td><?= htmlspecialchars($row['stok']); ?></td>
                            <td>
                                <a href="edit.php?id=<?= $row['id_barang']; ?>">Edit</a> |
                                <a href="delete.php?id=<?= $row['id_barang']; ?>" onclick="return confirm('Hapus data ini?');">Hapus</a>
                            </td>
                        </tr>
                    <?php endwhile; ?>
                <?php else: ?>
                    <tr>
                        <td colspan="7">Belum ada data</td>
                    </tr>
                <?php endif; ?>
            </tbody>
        </table>
    </div>
</div>
</body>
</html>
<?php require('footer.php'); ?>

![Screenshot 2024-11-30 192744](https://github.com/user-attachments/assets/e9c81c76-b82f-4e8b-8040-9f654bf2da3f)

Ini adalah halaman about
<?php require('header.php'); ?>

<?php
// Data untuk halaman About
$about_info = [
    'title' => 'Tentang Aplikasi Kami',
    'description' => 'Aplikasi ini dikembangkan untuk memberikan pengalaman terbaik dalam mendengarkan musik. Kami berkomitmen untuk menyediakan koleksi musik yang beragam dan fitur-fitur canggih untuk memanjakan pengguna.',
    'mission' => 'Misi kami adalah untuk memberikan platform musik yang mudah diakses, kaya fitur, dan dapat disesuaikan dengan preferensi pribadi pengguna.',
    'team' => [
        'Lead Developer' => 'John Doe',
        'UI/UX Designer' => 'Jane Smith',
        'Backend Developer' => 'James Brown'
    ],
    'contact' => 'Jika Anda memiliki pertanyaan, silakan hubungi kami di email@example.com'
];
?>

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title><?php echo $about_info['title']; ?></title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <header>
        <h1><?php echo $about_info['title']; ?></h1>
    </header>

    <section>
        <h2>Deskripsi</h2>
        <p><?php echo $about_info['description']; ?></p>
    </section>

    <section>
        <h2>Misi Kami</h2>
        <p><?php echo $about_info['mission']; ?></p>
    </section>

    <section>
        <h2>Tim Kami</h2>
        <ul>
            <?php foreach ($about_info['team'] as $role => $name): ?>
                <li><strong><?php echo $role; ?>:</strong> <?php echo $name; ?></li>
            <?php endforeach; ?>
        </ul>
    </section>

    <section>
        <h2>Kontak</h2>
        <p><?php echo $about_info['contact']; ?></p>
    </section>

</body>
</html>

<?php require('footer.php'); ?>

![Screenshot 2024-11-30 193509](https://github.com/user-attachments/assets/f9313590-42c8-42d5-a923-5b601d5dd525)

ini adalah halaman kontak

<?php require('header.php'); ?>
<div class="content">
<h2>Hubungi Kami</h2>
<p>Untuk informasi lebih lanjut mengenai produk dan layanan kami, silakan hubungi kami melalui salah satu cara berikut:</p>
<ul>
    <li><strong>Alamat:</strong> Jalan Jendral Sudirman No. 45, Jakarta Pusat</li>
    <li><strong>Email:</strong> sales@ponselku.com</li>
    <li><strong>Telepon:</strong> +62 812 3456 7890</li>
    <li><strong>WhatsApp:</strong> +62 812 3456 7890</li>
    <li><strong>Jam Operasional:</strong> Senin - Sabtu, 09:00 - 17:00</li>
</ul>

<h3>Produk Unggulan</h3>
<p>Kami menawarkan berbagai jenis ponsel dari merek ternama dengan harga bersaing:</p>
<ul>
    <li><strong>Samsung Galaxy S Series</strong> - Desain premium dan performa tinggi.</li>
    <li><strong>iPhone 14</strong> - Kualitas terbaik dengan teknologi canggih.</li>
    <li><strong>Xiaomi Redmi Note Series</strong> - Fitur lengkap dengan harga terjangkau.</li>
    <li><strong>Oppo Reno Series</strong> - Kamera unggulan untuk fotografi.</li>
    <li><strong>Vivo V Series</strong> - Pilihan terbaik untuk pengguna sosial media.</li>
</ul>

<p>Kunjungi toko kami untuk melihat langsung produk-produk terbaru dan dapatkan penawaran terbaik!</p>
</div>
<?php require('footer.php'); ?>

![Screenshot 2024-11-30 193444](https://github.com/user-attachments/assets/b96d2d5a-34a3-4c75-baae-cf167d44685d)

