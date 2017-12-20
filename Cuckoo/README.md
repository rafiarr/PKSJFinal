# Eksplorasi Cuckoo

Dalam eksplorasi cuckoo kelompok kami menggunakan windows 10 untuk menginstall cuckoo dan windows 7 sebagai sandbox dari cuckoo

## Tahap Installasi

Sebelum dapat menganalisa file menggunakan cuckoo maka ada beberapa hal yang harus di persiapkan sebelum install cuckoo.

### Mengaktifkan Windows Subsystem for Linux

Untuk mengaktifkan WSL dapat dilakukan melalui PowerShell dengan menuliskan sintaks berikut.

```shell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### Install Ubuntu 

Setelah menjalankan perintah tersebut windows akan meminta untuk *reboot* agar fitur dapat diaktifkan.

Berikutnya install ubuntu melalui Microsoft Store. Jika download telah berhasil jalankan ubuntu melalui windows. Lakukan instalasi ubuntu dengan menajalankan aplikasi ubuntu melalui windows.

Jika Ubuntu sudah terinstall lakukan update dan upgrade agar ubuntu memiliki library yang lengkap
```bash
sudo apt-get update
sudo apt-get upgrade
```
### Install lamp-server, mongodb

Kemudian setelah ubuntu bisa berjalan dengan baik, kita perlu menginstall lamp-server agar dapat menjalankan apache dan mysql juga mendownload mongodb

```bash
sudo apt-get install lamp-server
sudo apt-get install mongodb
```

### Jalankan service apache, mysql dan mongodb

Setelah semuanya terinstall sekarang waktunya untuk menjalankan nya dengan sintaks berikut

```bash
sudo service apache2 start
sudo service mysql start
sudo service mongodbstart
``` 

Setelah semuanya telah selesai di download dan kemudian di jalankan, maka kita dapat mengecek apakah http server apache dapat benar benar berjalan dengan mengakses **localhost** pada browser di windows

### Install Cuckoo

Pada tahap ini pastikan python sudah dapat di akses melalui *commandprompt* windows. Kemudian install dengan menggunakan pip dengan sintaks berikut
```shell
pip install cuckoo
```
Setelah cuckoo berhasil terinstall kemudian install mysql-pyhton agar cuckoo yang dibangun berdasarkan python dapat mengakses mysql.
```shell
easy_install mysql-pyhton
```
Jika sudah, jalankan  cuckoo init untuk membuat folder yang berisi file file konfigurasi dari cuckoo yang akan terletak pada C:\Users\<user>\.cuckoo

### Install VirtualBox dan Windows7

Sebelum memasuki tahapan konfigurasi pastikan windows 7 yang akan menjadi sandbox sudah dapat diakses melalui virtualbox yang nantinya akan dijadikan sebagai sandbox yang akan di pantau oleh cuckoo. Install pillow menggunakan pip dari python agar dapat di capture oleh cuckoo, berikut adalah sintaknya. 
```shell
pip install pillow
```

### Mengatur Konfigurasi Cuckoo

Pada tahap ini instalasi sudah selesai dan ada beberapa konfigurasi yang perlu di setting agar cuckoo dapat berjalan dengan semestinya.

**Pertama** kita perlu membuat database yang akan digunakan oleh cuckoo baik untuk membuat maupun menambahkan data report yang baru yaitu dengan login ke mysql dengan menuliskan sintaks berikut di terminal, tak hanya itu untuk mengakses databases tersebut dibutuhkan user yang diberikan permission untuk melakukannya, maka kita juga perlu membuatkannya.

```bash
mysql -u root -p
[Password user root]
``` 
Sete
```msql
create databases cuckoo
```
```mysql
create user 'Raf'@'localhost' identified by 'Raf';
create user 'Raf'@'%' identified by 'Raf';

grant all on *.* to 'Raf'@'localhost';
grant all on *.* to 'Raf'@'%';
```

**Kedua** pada file cuckoo.conf yang terdapat di folder .cuckoo\conf ada beberapa hal yang perlu diubah yaitu :
* connection = [mysql://<username>:<password>@127.0.0.1/cuckoo]
* 



### Referensi
* [Link Tutorial](https://www.youtube.com/watch?v=nLGJHgv6uWA)
* [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
