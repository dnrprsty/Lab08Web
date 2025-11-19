# 📘 Praktikum 8 – PHP dan MySQL

---

# 1. Tujuan Praktikum
Praktikum ini bertujuan untuk memahami cara:
- Menghubungkan PHP dengan MySQL.
- Membuat aplikasi CRUD (Create, Read, Update, Delete).
- Mengelola data menggunakan query SQL.
- Mengupload file (gambar) ke server.
- Menampilkan data dari database dalam format tabel.

---

# 2. Membuat Database dan Tabel

### Database yang digunakan:
latihan1

### Struktur tabel:
data_barang
```sql
id_barang INT AUTO_INCREMENT
kategori VARCHAR(100)
nama VARCHAR(200)
gambar VARCHAR(200)
harga_beli INT
harga_jual INT
stok INT
```
<img width="1366" height="740" alt="image" src="https://github.com/user-attachments/assets/e27e1a03-004e-4335-ba82-c33a5e62e213" />

---

# 3. Koneksi Database (koneksi.php)

```php
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db = "latihan1";

$conn = mysqli_connect($host, $user, $pass, $db);

if (!$conn) {
    die("Koneksi gagal: " . mysqli_connect_error());
}
?>
```


4. Menampilkan Data (index.php)

Fungsi:

- Menampilkan seluruh data barang.

- Menampilkan gambar dari folder /gambar.

- Terdapat tombol Tambah, Edit, dan Hapus.

<img width="1366" height="740" alt="Screenshot from 2025-11-18 00-24-44" src="https://github.com/user-attachments/assets/2bc42b4f-cc07-4144-9bc1-858ae3c49bf9" />


5. Menambah Data (tambah.php)

Fungsi:

- Menginput nama, kategori, harga beli, harga jual, stok.

- Mengupload gambar ke folder /gambar.

- Menyimpan path gambar ke database.

Contoh kode upload gambar:

```python
$filename = str_replace(' ', '_', $_FILES['file_gambar']['name']);
$destination = 'gambar/' . $filename;
move_uploaded_file($_FILES['file_gambar']['tmp_name'], $destination);
```
<img width="1366" height="740" alt="Screenshot from 2025-11-18 00-13-42" src="https://github.com/user-attachments/assets/a1efbb59-8aee-4aa1-ae45-5811b6503d48" />

6. Mengubah Data (ubah.php)

Fungsi:

-    Menampilkan data berdasarkan id_barang.

-    Mengupdate data yang telah diinput.

-    Jika gambar baru diupload, gambar lama diganti.

<img width="1366" height="740" alt="image" src="https://github.com/user-attachments/assets/4fe2d550-2b67-496e-abf2-1b5c9f7b444f" />

7. Menghapus Data (hapus.php)

```php
<?php
include_once 'koneksi.php';

$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang='$id'";
mysqli_query($conn, $sql);

header('location: index.php');
?>
```
<img width="1366" height="740" alt="Screenshot from 2025-11-18 00-24-35" src="https://github.com/user-attachments/assets/70eb3606-adb8-4ff6-8ef6-9ca68d876525" />


8. Hasil Akhir Program

Aplikasi berhasil:

- Menampilkan data barang lengkap.

- Upload gambar berhasil.

- CRUD berfungsi (Tambah, Edit, Hapus).

- Tampilan tabel rapi sesuai praktikum.

<img width="1366" height="740" alt="image" src="https://github.com/user-attachments/assets/ff4dc341-14e1-40fa-8a0b-6ad518eac7b4" />
<img width="1366" height="740" alt="Screenshot from 2025-11-18 00-48-28" src="https://github.com/user-attachments/assets/96adb7f1-5bee-48e3-825f-4cf0a95694cb" />
<img width="1366" height="740" alt="Screenshot from 2025-11-18 00-24-35" src="https://github.com/user-attachments/assets/69185f16-4366-4381-80b7-13e64a9b0cce" />

9. Kesimpulan

Pada praktikum ini, saya telah berhasil membuat aplikasi CRUD menggunakan PHP dan MySQL serta memahami:

- Cara membuat database dan tabel.

- Cara menampilkan data ke halaman web.

- Cara melakukan operasi tambah, edit, dan hapus.






