# Jarkom-Modul-4-B10-2022

# Anggota Kelompok
Anggota  | NRP
---------|-------
Zunia Aswaroh | 5025201058
Frederick Wijayadi Susilo | 5025201111

# Soal 
![image](https://github.com/zunia25/Modul-4/blob/main/soal%20shift%204.png)

- Soal shift dikerjakan pada Cisco Packet Tracer dan GNS3 menggunakan metode perhitungan CLASSLESS yang berbeda. Keterangan: Bila di CPT menggunakan VLSM, maka di GNS3 menggunakan CIDR atau Sebaliknya
- Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR dan DAPAT DIKERJAKAN. Untuk di GNS3 CLOUD merupakan NAT1 jangan sampai salah agar bisa terkoneksi internet.
- Pembagian IP menggunakan Prefix IP yang telah ditentukan pada modul pengenalan.
- Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.

Dalam mengerjakan soal ini, kami menggunakan teknik VLSM dengan menggunakan CPT, dan teknik CIDR dengan menggunakan GNS 3

# VLSM - CPT
## Pembagian Subnet
Hal pertama yang kami lakukan adalah dengan menentukan subnet yang ada pada topologi. Dikarenakan metode yang dipakai adalah VLSM. Kami melingkari tiap host yang terhubung pada interface router dan menghitung IP yang dibutuhkan. Berikut adalah gambaran pembagian subnetnya
![image](https://github.com/zunia25/Modul-4/blob/main/VLSM-CPT.png)

## Jumlah IP
Setelah melakukan pembagian subnet kita melakukan penjumlahan pada ip, Sehingga didapatkan hasil penjumlahan ip berikut :
![image](https://github.com/zunia25/Modul-4/blob/main/Tabel2.png)

## VSLM-Tree
Setelah mendapatkan penjumlahan ip kita membuat tree yang terdapat pada topologi. pada subnet memiliki NID 10.8.0.0 dengan netmask /20 sehingga pembagian IP berdasarkan NID dan Netmask yang di dapat.
![image](https://github.com/zunia25/Modul-4/blob/main/VLSM-Tree.png)

Pada VLSM ini diturunkan sesuai dengan netmask atasnya sehingga ketika /20 akan diturunkan menjadi /21, lakukan secara berulang-ulang sampai node semua terpenuhi.

## Pembagian IP
Kemudian kita bagi dengan tetap menggunakan ip perfix `10.8` . hasil pembagian seperti berikut :
![image](https://github.com/zunia25/Modul-4/blob/main/Tabel1.png)


# Config VSLM
## Menambah Ethernet / Port
Karena default hanya memiliki 2 port ethernet, maka kita bisa menambah port pada tab physical
![image](https://github.com/zunia25/Modul-4/blob/main/Port.png)

## config ip pada Node
![image](https://github.com/zunia25/Modul-4/blob/main/Router.png)

Contoh pada The Minister, kita menambahkan IP dan Subnet Mask sesuai dengan pembagian yang telah dilakukan, dengan IP ditambah 1 dari subnetnya.

Pada server & Client ditambahkan juga gateway yang mengarah ke router terdekat.
![image](https://github.com/zunia25/Modul-4/blob/main/Client.png)

Lakukan berulang-ulang pada semua node.

# Routing 
Pada routing berikut adalah config yang berada pada router.




