# TugasServerLiux

Nama : Ferdio Putra Prakarsa

NIM : 09011282328025

Mata Kuliah : Sistem Operasi

Laporan Tugas Server Linux

# Write Up Akses Server Base OS dengan SSH

# 1. Pengertian Protokol SSH 

SSH (Secure Shell) adalah protokol jaringan yang digunakan untuk mengamankan koneksi antara dua komputer melalui jaringan yang tidak aman. SSH memungkinkan pengguna untuk mengakses dan mengontrol komputer jarak jauh secara aman, menggunakan enkripsi untuk melindungi data yang dikirim. SSH sering digunakan untuk login jarak jauh, transfer file, dan menjalankan perintah pada server atau perangkat lain.

# 2. Pembahasan

**2.1. Cek Alamat IP Host Server**
Pengecekan IP Address digunakan dengan memasukkan command *$ifconfig*
![WhatsApp Image 2024-10-29 at 19 30 37_bd6cabf9](https://github.com/user-attachments/assets/9ce8bc9b-9164-40f7-9d8f-9f516eab0974)


**2.2 Pengecekan Open Port pada Host Server**
Dengan fitur nmap pada linux, dapat dimanfaatkan untuk melihat adanya open port pada Host Server, dengan menggunakan command *$nmap <IP Address>*

![WhatsApp Image 2024-10-29 at 19 47 53_2bb44860](https://github.com/user-attachments/assets/b6c88f03-9980-4767-b46e-8d915345f8df)

**2.3 Melakukan koneksi pada port dengan menggunakan protokol SSH**
Koneksi ke default port, yaitu port 22, dapat menggunakan command berikut :

*$ ssh -p 22 <usernameHost@alamatiphost>*

![WhatsApp Image 2024-10-29 at 19 52 44_d46952bb](https://github.com/user-attachments/assets/96c7cd2a-9b64-4c05-b100-9f1a75522c4f)

**2.4 Konfigurasi port 40 ke host server**

Untuk melakukan modifikasi yang lebih leluasa, dapat digunakan command *$sudo su* untuk masuk ke super user mode

**2.5 Modifikasi file ssh_config**

Untuk menghindari adanya corrupted file, maka kita dapat melakukan copy terlebih dahulu untuk file ssh_config, dengan menggunakan command berupa :

*$ cp /etc/ssh/ssh_config /etc/ssh/ssh_config.backup*

Lalu, untuk mengakses isi file ssh_config, dapat digunakan command sebagai berikut :

*$ nano /etc/ssh_config*

![WhatsApp Image 2024-10-29 at 21 11 51_5641717f](https://github.com/user-attachments/assets/1ae0e7ee-fb66-4ec5-8021-012a67c7dc8d)

setelah membuka file ssh_config menggunakan perintah nano ubah konfigurasi dengan beberapa hal ini dengan mengubah baris yang terdapat unsur port 22:

Protocol 2

Port 40

![WhatsApp Image 2024-10-29 at 21 18 54_8c5ea1bc](https://github.com/user-attachments/assets/cab4d34f-0457-4216-ba46-baff282af7ce)

**2.6 Mengaktifkan dan menerapkan perubahan port pada sistem**

Untuk menerapkan perubahan dan mengaktifkannya, dapat menggunakan command berikut :

*$ ufw allow 40/tcp*

*$ ufw enable*

Untuk pengecekan status UFW, dapat menggunakan command berikut :

*$ ufw status*

![WhatsApp Image 2024-10-29 at 21 20 58_08b71273](https://github.com/user-attachments/assets/fecd1cd8-2264-440d-87c1-ebd0971636c5)

**2.7 Melakukan koneksi pada port 40**

Setelah konfigurasi, maka untuk melakukan koneksi dapat menggunakan command sebagai berikut :

*$ ssh -p 40 <usernameHost@alamatiphost>*

![image](https://github.com/user-attachments/assets/610f1f70-1d65-4d86-919d-5296384dd33c)
