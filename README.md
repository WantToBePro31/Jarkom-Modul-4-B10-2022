# Jarkom-Modul-4-B10-2022

## Kelompok B10
| Name                      | NRP        | 
| ------------------------- | ---------- |
| Frederick Wijayadi Susilo | 5025201111 |
| Zunia Aswaroh             | 5025201058 |

IP Prefix Kelompok: `10.8`

# Soal dan Jawaban
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
Setelah melakukan pembagian subnet kita melakukan penjumlahan pada IP, sehingga didapatkan hasil penjumlahan ip berikut :

![image](https://github.com/zunia25/Modul-4/blob/main/Tabel2.png)

## VSLM-Tree
Setelah mendapatkan penjumlahan IP kita membuat tree yang terdapat pada topologi. Pada subnet memiliki NID 10.8.0.0 dengan netmask /20 sehingga pembagian IP berdasarkan NID dan Netmask yang di dapat.

![image](https://github.com/zunia25/Modul-4/blob/main/VLSM-Tree.png)

Pada VLSM ini diturunkan sesuai dengan netmask atasnya sehingga ketika /20 akan diturunkan menjadi /21, lakukan secara berulang-ulang sampai node semua terpenuhi.

## Pembagian IP
Kemudian kita bagi dengan tetap menggunakan IP perfix `10.8` . hasil pembagian seperti berikut :

![image](https://github.com/zunia25/Modul-4/blob/main/Tabel1.png)


# Config VSLM
## Menambah Ethernet / Port
Karena default hanya memiliki 2 port ethernet, maka kita bisa menambah port pada tab physical

![image](https://github.com/zunia25/Modul-4/blob/main/Port.png)

## Config IP pada Node
![image](https://github.com/zunia25/Modul-4/blob/main/Router.png)

Contoh pada The Minister, kita menambahkan IP dan Subnet Mask sesuai dengan pembagian yang telah dilakukan, dengan IP ditambah 1 dari subnetnya. dan jangan lupa untuk di on kan pada port nya.

Pada server & Client ditambahkan juga gateway yang mengarah ke router terdekat.

![image](https://github.com/zunia25/Modul-4/blob/main/Client.png)

Lakukan berulang-ulang pada semua node.

# Routing 
Pada routing berikut adalah config yang berada pada router. Untuk langkah nya bisa masuk kedalam router, lalu menekan menu static dan menambahkan data yang diinginkan.

## The Reference
- 10.8.0.4/30 via 10.8.0.10
- 10.8.0.64/26 via 10.8.0.10
- 10.8.8.0/22 via 10.8.0.10
- 10.8.0.0/30 via 10.8.0.10
- 10.8.2.0/24 via 10.8.0.10
- 10.8.0.24/30 via 10.8.0.26
- 10.8.6.0/23 via 10.8.0.26
- 10.8.0.16/30 via 10.8.0.18
- 10.8.0.128/30 via 10.8.0.18
- 10.8.0.20/30 via 10.8.0.18
- 10.8.1.128/25 via 10.8.0.18
- 10.8.1.0/25 via 10.8.0.18
- 10.8.0.12/30 via 10.8.0.18
- 10.8.4.0/23 via 10.8.0.18
- 10.8.3.0/24 via 10.8.0.18
- 10.8.0.28/30 via 10.8.0.18

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Refonance.png)

Pada The Reference merupakan pusat Router jadi semua IP dari subnet diasiggn ke Router The Reference agar semua bisa terhubung.

## The Order
- 0.0.0.0/0 via 10.8.0.9
- 10.8.8.0/22 via 10.8.0.6
- 10.8.0.0/30 via 10.8.0.6
- 10.8.2.0/24 via 10.8.0.6

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Order.png)

## The Minister
- 0.0.0.0/0 via 10.8.0.5
- 10.8.2.0/24 via 10.8.0.2

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Minister.png)

## The Daundless
- 0.0.0.0/0 via 10.8.0.1

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Daundless.png)

0.0.0.0 berarti mengambil semua pesan dan diarahkan ke next hop.

## The Magical
- 0.0.0.0/0 via 10.8.0.25

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Megical.png)

## The Instrument
- 0.0.0.0/0 via 10.8.0.17
- 10.8.0.20/30 via 10.8.0.22
- 10.8.1.128/25 via 10.8.0.22
- 10.8.1.0/25 via 10.8.0.22
- 10.8.0.12/30 via 10.8.0.14
- 10.8.3.0/24 via 10.8.0.14
- 10.8.4.0/23 via 10.8.0.14
- 10.8.0.28/30 via 10.8.0.14

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Instrument.png)

## The Profound
- 0.0.0.0/0 via 10.8.0.21

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Poofound.png)

## The Firefist
- 0.0.0.0/0 via 10.8.0.13
- 10.8.0.28/30 via 10.8.3.3

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Etefist.png)

## The Queen
- 0.0.0.0/0 via 10.8.3.1

![image](https://github.com/zunia25/Modul-4/blob/main/The%20Queen.png)

# Testing
Hasil dari message tiap node.

![image](https://github.com/zunia25/Modul-4/blob/main/Testing.png)

# CIDR - GNS3

## Penggabungan Subnet
Kita melakukan penggabungan subnet-subnet paling bawah dalam topologi yaitu dimulai dari subnet yang paling jauh dengan cloud/nat hingga hanya memiliki 1 subnet (induk).

- Kondisi Awal

![image](https://user-images.githubusercontent.com/67154280/203823347-02d5c9cb-6757-4cf5-ae5c-27098f1cbf16.png)

- Penggabungan Pertama (Subnet B)
</br>&nbsp;&nbsp;1. Subnet A2 dan A3 menghasilkan B1 dengan netmask /23 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /24 dari A3.
</br>&nbsp;&nbsp;2. Subnet A13 dan A14 menghasilkan B2 dengan netmask /23 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /24 dari A13.

![image](https://user-images.githubusercontent.com/67154280/203823270-e0d73eb8-c4ec-4894-b6da-c0af20b3d6f6.png)

- Penggabungan Kedua (Subnet C)
</br>&nbsp;&nbsp;1. Subnet A1 dan B1 menghasilkan C1 dengan netmask /21 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /22 dari A1.
</br>&nbsp;&nbsp;2. Subnet A12 dan B2 menghasilkan C2 dengan netmask /22 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /23 dari A12.
</br>&nbsp;&nbsp;3. Subnet A9 dan A10 menghasilkan C3 dengan netmask /24 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /25 dari A9.

![image](https://user-images.githubusercontent.com/67154280/203823201-235bbd58-e58f-471b-b2c1-4499d43ec977.png)

- Penggabungan Ketiga (Subnet D)
</br>&nbsp;&nbsp;1. Subnet C1 dan A4 menghasilkan D1 dengan netmask /20 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /21 dari C1.
</br>&nbsp;&nbsp;2. Subnet A11 dan C2 menghasilkan D2 dengan netmask /21 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /22 dari C2.
</br>&nbsp;&nbsp;3. Subnet A8 dan C3 menghasilkan D3 dengan netmask /23 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /24 dari C3.

![image](https://user-images.githubusercontent.com/67154280/203823162-b3b40dff-eb85-4965-8084-321ea1fa9660.png)

- Penggabungan Keempat (Subnet E)
</br>&nbsp;&nbsp;1. Subnet D1 dan A5 menghasilkan E1 dengan netmask /19 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /20 dari D1.
</br>&nbsp;&nbsp;2. Subnet D2 dan A15 menghasilkan E2 dengan netmask /20 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /21 dari D2.

![image](https://user-images.githubusercontent.com/67154280/203823114-561ce1e4-94e9-4241-8ed0-2b52da38952b.png)

- Penggabungan Kelima (Subnet F)
</br>&nbsp;&nbsp;1. Subnet D3 dan E2 menghasilkan F1 dengan netmask /19 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /20 dari E2.

![image](https://user-images.githubusercontent.com/67154280/203823035-2818d042-6d18-4518-8d1f-84f3f60f4f31.png)

- Penggabungan Keenam (Subnet G)
</br>&nbsp;&nbsp;1. Subnet E1 dan A6 menghasilkan G1 dengan netmask /18 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /19 dari E1.
</br>&nbsp;&nbsp;2. Subnet A7 dan F1 menghasilkan G2 dengan netmask /18 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /19 dari F1.
</br>&nbsp;&nbsp;3. Subnet A17 dan A18 menghasilkan G3 dengan netmask /22 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /23 dari A18.

![image](https://user-images.githubusercontent.com/67154280/203822948-f6075249-66ee-4691-b3db-121a4eef8410.png)

- Penggabungan Ketujuh (Subnet H)
</br>&nbsp;&nbsp;1. Subnet A16 dan G3 menghasilkan H1 dengan netmask /21 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /22 dari G3.

![image](https://user-images.githubusercontent.com/67154280/203822821-58b60032-00ee-4b4a-bfea-cf9900509d4c.png)

- Penggabungan Kedelapan (Subnet I)
</br>&nbsp;&nbsp;1. Subnet G2 dan H1 menghasilkan I1 dengan netmask /17 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /18 dari G2.

![image](https://user-images.githubusercontent.com/67154280/203822776-4b69f685-19b2-4a36-984f-810c31ea6098.png)

- Penggabungan Kesembilan (Subnet J)
</br>&nbsp;&nbsp;1. Subnet G1 dan I1 menghasilkan J1 dengan netmask /16 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /17 dari I1.

![image](https://user-images.githubusercontent.com/67154280/203822575-b2f83376-14a9-466f-8bd2-6a28ad3047dd.png)

## CIDR-Tree
Setelah mendapatkan penggabungan subnet, kita membuat tree yang terdapat pada topologi. Pada paling atas (parent) memiliki subnet dengan NID 10.8.0.0 dengan netmask /16.

![image](https://user-images.githubusercontent.com/67154280/203804063-b79872d7-7a69-431b-abdb-485fa2790634.png)

## Pembagian IP
Kemudian kita bagi dengan tetap menggunakan ip perfix `10.8`. Hasil pembagian seperti berikut :

![image](https://user-images.githubusercontent.com/67154280/203805313-a03f5578-da23-4060-a4a2-2fae4fd4117a.png)

## Eth Configuration
Pada masing-masing node akan dilakukan network configuration, kita melakukan assignment dengan IP yang telah ditetapkan sesuai dengan subnet

- The Reference
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet dhcp

  auto eth1
  iface eth1 inet static
  address 10.8.68.1
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 10.8.66.1
  netmask 255.255.255.252

  auto eth3
  iface eth3 inet static
  address 10.8.32.1
  netmask 255.255.255.252

  auto eth4
  iface eth4 inet static
  address 10.8.160.1
  netmask 255.255.255.252
  ```

- The Order
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.160.2
  netmask 255.255.255.252
  gateway 10.8.160.1

  auto eth1
  iface eth1 inet static
  address 10.8.136.1
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 10.8.144.1
  netmask 255.255.255.192
  ```
  
- Ashaf
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.144.2
  netmask 255.255.255.192
  gateway 10.8.144.1
  ```
  
- The Minister
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.136.2
  netmask 255.255.255.252
  gateway 10.8.136.1

  auto eth1
  iface eth1 inet static
  address 10.8.133.1
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 10.8.128.1
  netmask 255.255.252.0
  ```
  
- Guidessu
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.128.2
  netmask 255.255.252.0
  gateway 10.8.128.1
  ```
  
- The Daundless
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.133.2
  netmask 255.255.255.252
  gateway 10.8.133.1

  auto eth1
  iface eth1 inet static
  address 10.8.132.1
  netmask 255.255.255.0
  ```
  
- Phanora
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.132.2
  netmask 255.255.255.0
  gateway 10.8.132.1
  ```
  
- Johan
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.132.3
  netmask 255.255.255.0
  gateway 10.8.132.1
  ```
  
- The Beast
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.68.2
  netmask 255.255.255.252
  gateway 10.8.68.1
  ```
  
- The Magical
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.66.2
  netmask 255.255.255.252
  gateway 10.8.66.1

  auto eth1
  iface eth1 inet static
  address 10.8.64.1
  netmask 255.255.254.0
  ```
  
- Haines
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.64.2
  netmask 255.255.254.0
  gateway 10.8.64.1
  ```
  
- Corvekt
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.64.3
  netmask 255.255.254.0
  gateway 10.8.64.1
  ```
  
- The Instrument
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.32.2
  netmask 255.255.255.252
  gateway 10.8.32.1

  auto eth1
  iface eth1 inet static
  address 10.8.17.1
  netmask 255.255.255.252

  auto eth2
  iface eth2 inet static
  address 10.8.4.1
  netmask 255.255.255.252

  auto eth3
  iface eth3 inet static
  address 10.8.8.1
  netmask 255.255.255.128
  ```
  
- Matt Cugat
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.8.2
  netmask 255.255.255.128
  gateway 10.8.8.1
  ```
  
- The Profound
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.17.2
  netmask 255.255.255.252
  gateway 10.8.17.1

  auto eth1
  iface eth1 inet static
  address 10.8.16.1
  netmask 255.255.255.128

  auto eth2
  iface eth2 inet static
  address 10.8.16.129
  netmask 255.255.255.128
  ```
  
- Spendrow
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.16.2
  netmask 255.255.255.128
  gateway 10.8.16.1
  ```
  
- Helga
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.16.130
  netmask 255.255.255.128
  gateway 10.8.16.129
  ```
  
- The Firefist
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.4.2
  netmask 255.255.255.252
  gateway 10.8.4.1

  auto eth1
  iface eth1 inet static
  address 10.8.2.1
  netmask 255.255.254.0

  auto eth2
  iface eth2 inet static
  address 10.8.0.1
  netmask 255.255.255.0
  ```
  
- Oakleave
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.2.2
  netmask 255.255.254.0
  gateway 10.8.2.1
  ```
  
- Keith
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.0.3
  netmask 255.255.255.0
  gateway 10.8.0.1
  ```
  
- The Queen
  ```shell
  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet static
  address 10.8.0.2
  netmask 255.255.255.0
  gateway 10.8.0.1

  auto eth1
  iface eth1 inet static
  address 10.8.1.1
  netmask 255.255.255.252
  ```
  
- The Witch
  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.1.2
  netmask 255.255.255.252
  gateway 10.8.1.1
  ```

## Routing
Setelah itu akan dilakukan routing pada GNS3 agar semua router, server, dan client akan saling terhubung.

- The Reference
  ```shell
  route add -net 10.8.144.0 netmask 255.255.255.192 gw 10.8.160.2
  route add -net 10.8.136.0 netmask 255.255.255.252 gw 10.8.160.2
  route add -net 10.8.128.0 netmask 255.255.252.0 gw 10.8.160.2
  route add -net 10.8.133.0 netmask 255.255.255.252 gw 10.8.160.2
  route add -net 10.8.132.0 netmask 255.255.255.0 gw 10.8.160.2

  route add -net 10.8.64.0 netmask 255.255.254.0 gw 10.8.66.2

  route add -net 10.8.8.0 netmask 255.255.255.128 gw 10.8.32.2
  route add -net 10.8.17.0 netmask 255.255.255.252 gw 10.8.32.2
  route add -net 10.8.16.0 netmask 255.255.255.128 gw 10.8.32.2
  route add -net 10.8.16.128 netmask 255.255.255.128 gw 10.8.32.2
  route add -net 10.8.4.0 netmask 255.255.255.252 gw 10.8.32.2
  route add -net 10.8.2.0 netmask 255.255.254.0 gw 10.8.32.2
  route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.32.2
  route add -net 10.8.1.0 netmask 255.255.255.252 gw 10.8.32.2
  ```
  
- The Order
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.160.1

  route add -net 10.8.128.0 netmask 255.255.252.0 gw 10.8.136.2
  route add -net 10.8.133.0 netmask 255.255.255.252 gw 10.8.136.2
  route add -net 10.8.132.0 netmask 255.255.255.0 gw 10.8.136.2
  ```
  
- The Minister
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.136.1

  route add -net 10.8.132.0 netmask 255.255.255.0 gw 10.8.133.2
  ```
  
- The Daundless
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.133.1
  ```
  
- The Magical
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.66.1
  ```
  
- The Instrument
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.32.1

  route add -net 10.8.16.0 netmask 255.255.255.128 gw 10.8.17.2
  route add -net 10.8.16.128 netmask 255.255.255.128 gw 10.8.17.2

  route add -net 10.8.2.0 netmask 255.255.254.0 gw 10.8.4.2
  route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.4.2
  route add -net 10.8.1.0 netmask 255.255.255.252 gw 10.8.4.2
  ```
  
- The Profound
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.17.1
  ```
  
- The Firefist
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.4.1

  route add -net 10.8.1.0 netmask 255.255.255.252 gw 10.8.0.2
  ```
  
- The Queen
  ```shell
  route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.8.0.1
  ```
  
## Testing
Testing dilakukan pada masing-masing client dan dikatakan berhasil jika client yang berjarak jauh dari router/server/client lain dapat melakukan ping pada router/server/client tersebut.

![image](https://user-images.githubusercontent.com/67154280/203810610-01cf476c-c090-4674-bdd7-9b223bfb9ba2.png)

![image](https://user-images.githubusercontent.com/67154280/203811201-a71d374c-e477-4b48-a272-1cc4dbec6a0f.png)

![image](https://user-images.githubusercontent.com/67154280/203811313-6afaf95d-b1f4-44fc-9f07-97c6304df6cf.png)


## Kendala
- Saat melakukan ping di cpt, ada yang harus dilakukan 2-3x tidak bisa langsung 1x karena failed, nemun setelah dicoba lagi menjadi succesful


