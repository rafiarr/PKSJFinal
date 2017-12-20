# Eksplorasi Cuckoo

Dalam eksplorasi cuckoo kelompok kami menggunakan windows 10 untuk menginstall cuckoo dan ubuntu sebagai subsystem

##Tahap Installasi

Sebelum dapat menganalisa file menggunakan cuckoo maka ada beberapa hal yang harus di persiapkan sebelum install cuckoo.

### Mengaktifkan Windows Subsystem for Linux

Untuk mengaktifkan WSL dapat dilakukan melalui PowerShell dengan menuliskan sintaks berikut.

```shell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### Install Ubuntu 

Setelah menjalankan perintah tersebut windows akan meminta untuk *reboot* agar fitur dapat diaktifkan.

Berikutnya install ubuntu melalui Microsoft Store. Jika download telah berhasil jalankan ubuntu melalui windows. Lakukan instalasi ubuntu dengan me











### Referensi
* [Link Tutorial](https://www.youtube.com/watch?v=nLGJHgv6uWA)
* [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
