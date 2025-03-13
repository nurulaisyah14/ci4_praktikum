# Pertemuan ke 2 <img src=https://seeklogo.com/images/E/elephpant-mascot-php-logo-4C78D1AC4E-seeklogo.com.png width="120px" >

## Profil
|  |  |
| -------- | --- |
| **Nama** | Nurul Aisyah |
| **Kelas** | TI.23.A.5 |
| **Mata Kuliah** | Pemrograman Web 2 |
| **Dosen Pengampu** |  Agung Nugroho, S.Kom., M.Kom |

# Praktikum 1: PHP Framework (Codeigniter)

## Langkah-langkah Praktikum
## Persiapan
Sebelum mulai menggunakan Framework CodeIgniter, diperlukan konfigurasi pada webserver. Salah satu langkah penting adalah mengaktifkan beberapa ekstensi PHP yang dibutuhkan untuk pengembangan CodeIgniter 4. Berikut adalah beberapa ekstensi yang harus diaktifkan:
- **php-json** → Untuk mengelola data dalam format JSON.
- **php-mysqlnd** → Native driver untuk berinteraksi dengan MySQL.
- **php-xml** → Digunakan untuk memproses data berbasis XML.
- **php-intl** → Membantu dalam pengembangan aplikasi multibahasa.
- **libcurl** *(opsional)* → Diperlukan jika ingin menggunakan fitur Curl.
Untuk memastikan ekstensi-ekstensi tersebut telah aktif, Anda bisa mengeceknya melalui PowerShell atau Command Prompt dengan langkah-langkah berikut:

### Catatan : mulai dari PHP 7.0, ekstensi JSON biasanya sudah termasuk secara bawaan.
![Screenshot 2025-03-13 135440](https://github.com/user-attachments/assets/3c670fba-1a50-41fb-bfdb-f6844b9ab9a3)
Lalu kalian bisa mencari ekstensi yang kalian butuhkan, jika ada yang belum diaktivasi kalian dapat mengaktifkan ekstensi tersebut, melalu XAMPP Control Panel, pada bagian Apache
klik Config -> PHP.ini :
![image](https://github.com/user-attachments/assets/39e7a0e8-dd11-41ac-9a1c-cbf8fdfe05c3)

<img width="410" alt="intl xampp" src="https://github.com/user-attachments/assets/f40893aa-c4df-4a48-864e-b41f98b31931" />

* Contohnya disini extension=intl belum aktif, maka cara mengaktivasinya adalah dengan menghilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.

## Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual
dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.
1. **Unduh CodeIgniter 4** dari situs resmi: [CodeIgniter Download](https://codeigniter.com/download).
2. **Ekstrak file ZIP** yang telah diunduh ke dalam folder `htdocs/lab11_ci`.
3. **Ubah nama direktori** dari `codeigniter4-framework-v4.x.xx` menjadi `ci4`.
4. **Jalankan aplikasi** dengan mengakses URL berikut di browser:  

![image](https://github.com/user-attachments/assets/1630c40f-c6cf-4302-b111-d4126b403096)


## Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka Shell pada XAMPP.

![image](https://github.com/user-attachments/assets/f692207a-5cf1-4e4b-bc2c-c9ade865a13f)


Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (Contoh : cd htdocs/lab11_ci/ci4)

Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:

### php spark
![Screenshot 2025-03-13 135458](https://github.com/user-attachments/assets/037e584f-5136-41c4-a634-93559964abbd)


## Mengaktifkan Mode Debugging
Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.

Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan seperti berikut.
![image](https://github.com/user-attachments/assets/03861a39-45f6-489d-af73-c993dddbb264)


Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya,
maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment
variable CI_ENVIRONMENT menjadi development.
![image](https://github.com/user-attachments/assets/99ec3800-c128-47ca-b8e9-c9e907074454)
Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable
CI_ENVIRONMENT menjadi development.
#### Catatan : Kadang, CodeIgniter tidak membaca file .env karena masih dikomentari, pastikan tidak ada tanda # di depan CI_ENVIRONMENT.
![image](https://github.com/user-attachments/assets/117dac6c-7c90-4a11-88bb-efa4d17be296)
Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file
app/Controller/Home.php hilangkan titik koma pada akhir kode return view('welcome_message').
![image](https://github.com/user-attachments/assets/dd01824a-94dd-4f06-99c6-4f2e37a5ef1c)
## Memahami konsep MVC
Codeigniter menggunakan konsep MVC. MVC meripakan singkatan dari Model-View-
Controller. MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan
tampilan. Untuk logic proses diletakkan pada direktori Contoller, Objek data diletakkan pada direktori Model, dan desain tampilan diletakkan pada direktori View.

Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan konsep MVC.

Model merupakan kode program yang berisi pemodelan data. Data dapat berupa database ataupun sumber lainnya.

View merupakan kode program yang berisi bagian yang menangani terkait tampilan user interface sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan dengan html dan css.

Controller merupakaan kode program yang berkaitan dengan logic proses yang menghubungkan antara view dan model. Controller berfungsi untuk menerima request dan data dari user kemudian diproses dengan menghubungkan bagian model dan view.

## Routing dan Controller
Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4, routing bertujuan untuk menentukan Controller mana yang harus merespon sebuah request. Controller
adalah class atau script yang bertanggung jawab merespon sebuah request.

Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk
meudian oleh router tesebut diarahkan ke Controller.

Router terletak pada file app/config/Routes.php
![image](https://github.com/user-attachments/assets/42f9f20c-f664-4161-bf7a-35047d068012)
Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.
Contoh:
```` python
$routes->get('/', 'Home::index');
````
Kode tersebut akan mengarahkan rute untuk halaman home.

#### Membuat Route Baru.
Tambahkan kode berikut di dalam Routes.php
```` python
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
````
Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.

php spark routes
![image](https://github.com/user-attachments/assets/1e0beb8e-07c3-47dc-bfaf-e823d4b7de98)



Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about
![image](https://github.com/user-attachments/assets/3542bb80-4e01-45b9-b6a1-afc483b30974)


Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

#### Membuat Controller
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.

```` python
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        echo "Ini halaman About";
    }
    public function contact()
    {
        echo "Ini halaman Contact";
    }
    public function faqs()
    {
        echo "Ini halaman FAQ";
    }
}
````

![image](https://github.com/user-attachments/assets/200c988e-21ee-4579-b433-b87153295935)

#### Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.

```` python
$routes->get('page/tos', 'Page::tos');
$routes->setAutoRoute(true);
````

Tambahkan method baru pada Controller Page seperti berikut.
```` python
public function tos()
{
    echo "ini halaman Term of Services";
}
````

Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos
![image](https://github.com/user-attachments/assets/793276bf-58cb-4059-a8ef-73d08b9bde70)



### Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori Views (app/Views/about.php) kemudian isi kodenya seperti berikut.
```` python
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>

<body>
    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>
</body>

</html>
````

Ubah method about pada class Controller Page menjadi seperti berikut:
``` python
    public function about()
    {
        return view('about', [
            'title' => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
        ]);
    }
```

Kemudian lakukan refresh pada halaman tersebut.

![image](https://github.com/user-attachments/assets/879ca1dc-5d81-401b-bd6c-2fd751c037d3)

### Membuat Layout Web dengan CSS
Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.

Buat file css pada direktori public dengan nama style.css

![image](https://github.com/user-attachments/assets/2382acdf-8a7b-46ee-a7c4-a50789db261e)


Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php

File app/Views/template/header.php
```python
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css'); ?>">
</head>

<body>
    <div id="container">
        <header>
            <h1>Layout Sederhana</h1>
        </header>
        <nav>
            <a href="<?= base_url('/'); ?>" class="active">Home</a>
            <a href="<?= base_url('/artikel'); ?>">Artikel</a>
            <a href="<?= base_url('/about'); ?>">About</a>
            <a href="<?= base_url('/contact'); ?>">Kontak</a>
        </nav>
        <section id="wrapper">
            <section id="main"></section>
```

File app/Views/template/footer.php
```python
</section>
<aside id="sidebar">
    <div class="widget-box">
        <h3 class="title">Widget Header</h3>
        <ul>
            <li><a href="#">Widget Link</a></li>
            <li><a href="#">Widget Link</a></li>
        </ul>
    </div>
    <div class="widget-box">
        <h3 class="title">Widget Text</h3>
        <p>Vestibulum lorem elit, iaculis in nisl volutpat,
            malesuada tincidunt arcu. Proin in leo fringilla, vestibulum mi porta,
            faucibus felis. Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
    </div>
</aside>
</section>
<footer>
    <p>&copy; 2021 - Universitas Pelita Bangsa</p>
</footer>
</div>
</body>

</html>
```

Kemudian ubah file app/Views/about.php seperti berikut.
```python
<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>
```

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about
![image](https://github.com/user-attachments/assets/1a970168-af83-411a-a09b-4492aa123f26)


