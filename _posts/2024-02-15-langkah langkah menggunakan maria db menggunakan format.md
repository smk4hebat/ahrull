# tutorial menggunakan maria db menggunakan format ,markdown agar bisa di copyBerikut adalah tutorial menggunakan MariaDB dalam format Markdown agar dapat dicopy:

1. Instalasi MariaDB
    Unduh dan instal MariaDB dari situs resmi MariaDB.
2. Masuk ke MariaDB menggunakan Terminal
   
       mysql -u username -p
   Gantilah "username" dengan nama pengguna MariaDB Anda.
   
   Anda akan diminta untuk memasukkan kata sandi setelah itu.
4. Membuat Basis Data
   
        CREATE DATABASE nama_database;
   
   Gantilah "nama_database" dengan nama basis data yang diinginkan.
   
6. Pilih Basis Data
   
       USE nama_database;
   
8. Membuat Tabel Biodata Siswa
   
        CREATE TABLE biodata_siswa (
        id INT AUTO_INCREMENT PRIMARY KEY,
        nama VARCHAR(50) NOT NULL,
        tanggal_lahir DATE NOT NULL,
        alamat TEXT,
        kelas VARCHAR(10),
       nilai DECIMAL(5, 2)
       );
10. Menambahkan Data ke Tabel
    
    INSERT INTO biodata_siswa (nama, tanggal_lahir, alamat, kelas, nilai)
    VALUES
    
         ('NamaSiswa1', '2000-01-01', 'AlamatSiswa1', 'KelasA', 85.50),
         ('NamaSiswa2', '2001-02-02', 'AlamatSiswa2', 'KelasB', 78.75),
         ('NamaSiswa3', '2002-03-03', 'AlamatSiswa3', 'KelasC', 92.00);
12. Menampilkan Data dari Tabel
    
    
         SELECT * FROM biodata_siswa;
    
14. Memperbarui Data
    
        UPDATE biodata_siswa
        SET nilai = 90.00
        WHERE nama = 'NamaSiswa1';
    
16. Menghapus Data
    
        DELETE FROM biodata_siswa WHERE nama = 'NamaSiswa2';
    
18. Keluar dari MariaDB
    
        exit;
        Ini akan keluar dari shell MariaDB.


   Pastikan untuk menyesuaikan nama basis data, tabel, dan nilai sesuai kebutuhan Anda. Anda dapat menyalin dan menjalankan setiap perintah SQL di terminal MariaDB Anda.







