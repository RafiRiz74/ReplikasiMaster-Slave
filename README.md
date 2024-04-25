# Replikasi Master-Slave untuk Database pada DewaCloud
Pertama-tama masuk ke dashboard DewaCloud, lalu klik new environment diatas kiri untuk membuat database.
![1.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/1.png)

## 1. Membuat environment di DewaCloud
Setelah mengklik new environtment, maka tampilannya akan seperti dibawah ini.
![2.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/2.png)
Kemudian pilih menu SQL yang bergambar anjing laut seperti diatas, setelah itu berikan nama environment yang akan dibuat, contohnya yang saya but yaitu "masterrafi", kemudian klik create di ujung bawah kanan seperti di gambar.

Setelah itu tunggu beberapa saat kemudian environment akan berhasil dibuat seperti gambar dibawah ini.
![3.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/3.png)

Setelah membuat environment untuk master, saya mengklon master untuk membuat slave dengan nama "slaverafi", setelah di klon maka tampilannya akan seperti gambar dibawah ini.
![4.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/4.png)

## 2. Konfigurasi Database "masterrafi"
Pertama klik tombol config seperti gambar dibawah ini.
![5.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/5.png)

Kemudian cari file my.cnf, dan buka file tersebut, kemudian ubah file tersebut seperti gambar dibawah ini.
![6.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/6.png)
Jika sudah diubah, maka klik tombol save disamping tombol search, seperti gambar diatas.

Apabila telah di save, restart masterrafi dengan mengklik tombol seperti dibawah ini.
![7.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/7.png)

Setelah itu klik tombol Open in Browser seperti dibawah ini.
![8.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/8.png)

Kemudian akan muncul tampilan login seperti gambar dibawah ini.
![9.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/9.png)
Masukkan nama pengguna dan kata sandi sesuai yang dikirim pada email anda.

Setelah login, masuk ke bagian akun pengguna, kemudian klik add user account seperti gambar dibawah ini.
![10.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/10.png)

Kemudian tampilannya akan seperti ini.
![11.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/11.png)
Disini saya membuat namanya dengan rafislave, kemudian masukkan passwordnya sesuai yang anda inginkan.

Setelah itu centang replication client dan replication slave seperti gambar dibawah ini.
![12.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/12.png)
Kemudian klik kirim.

Untuk memastikan replication telah terkonfigurasi dengan benar, masuk ke bagian status, maka ada tampilan seperti dibawah ini pada status replikasi.
![13.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/13.png)
Catat nilai file dan posisition, karena akan diperlukan pada saat konfigurasi di slave.

## 3. Konfigurasi Database "slaverafi"
Sama seperti konfigurasi master, buka menu config seperti gambar dibawah ini.
![14.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/14.png)

Masuk ke file my.cnf dan ubah kodenya seperti gambar dibawah ini.
![15.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/15.png)
Klik save apabila sudah diubah.

Kemudian cari file di config.inc.php /etc/phpMyAdmin/ dan tambahkan beberapa kode seperti dibawah ini.
![16.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/16.png)

Jika sudah restart slaverafi seperti gambar dibawah ini.
![17.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/17.png)

Jika sudah, masuk ke Web SSH pada database MariaDB, kemudian jalankan kode seperti gambar dibawah ini, masukkan sesuai konfigurasi user replikasi yang telah dibuat tadi.
![18.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/18.png)

Kemudian agar bisa memulai slave nya, jalankan perintah seperti dibawah ini.
![19.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/19.png)

Untuk memastikan bahwa konfigurasi sudah benar, masuk ke database admin rafislave, kemudian pilih status, seperti gambar seperti ini.
![20.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/20.png)

## 4. Cek Hasil Replikasi
Untuk mengecek apakah teplikasi telah berhasil maka buat database baru contohnya disini saya membuat "rafiriz", setelah itu klik buat.
![21.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/21.png)

Nah apabila replikasi berhasil terbuat, maka pada database admin rafislave akan muncul juga database yang baru dibuat pada masterrafi tadi.
![22.png](https://github.com/RafiRiz74/ReplikasiMaster-Slave/blob/main/22.png)
