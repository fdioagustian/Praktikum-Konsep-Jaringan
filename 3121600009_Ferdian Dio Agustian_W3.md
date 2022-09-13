# Laporan Konsep Jaringan
##### Ferdian Dio Agustian
###### 3121600009/2 D4 IT A

#
> Praktikum kali ini merupakan hasil praktikum CISCO untuk mengamati bagaimana sebuah jaringan dapat berjalan dalam komputer dengan kasus 3 skenario
1. PC 0 terhadap PC 1
2. PC 0 melakukan PING terhadap PC 1 (apakah terjadi broadcast?)
3. PC 1 melakukan PING terhadap PC 0 (apakah terjadi broadcast lagi?)



# Skenario 1

1. Setiap komputer diberi IP address. (Pada PC 0 diberi IP 192.168.1.1), (Pada PC 1 diberi IP 192.168.1.2), (Pada PC 2 diberi IP 192.168.1.3). Sebelum melakukan PING dari PC 0 ke PC 1 perlu dilakukan pemeriksaan arp dengan cara **arp -a**. Jika arp memiliki isi maka PING tidak dapat dilakukan, dan jika arp tidak ada maka PING dapat dilakukan seperti pada gambar di bawah ini.

>![](https://i.postimg.cc/fRLTprDV/Screenshot-2022-09-11-202337.png)
Keterangan: arp pada PC 0 kosong/tidak ada

# Skenario 2
2. Setelah pemeriksaan arp pada PC 0, maka dapat dipastikan PING dapat dilakukan dari PC 0 ke PC 1 dengan cara melakukan IP dengan diikuti IP address PC 1 (**ping 192.168.1.2**).
>![](https://i.postimg.cc/rpGVrX9Y/Screenshot-2022-09-11-203217.png)
Keterangan: melakukan ping dari PC 0 ke PC 1

Ketika PC 0 akan melakukan ping, ping tersebut akan dihold terlebih dahulu pada hub. Hal itu karena PC 0 perlu melakukan broadcast terlebih dahulu untuk mencari tahu lokasi PC 1 yang memiliki address 192.168.1.2.
>![](https://i.postimg.cc/g2tzyH93/Screenshot-2022-09-11-204003.png)
Keterangan: PC 1 dapat menerima broadcast tersebut yang dikirimkan dari PC 0, tetapi PC 2 tidak dapat menerima karena lokasi yang dituju dari PC 0 yaitu PC 1 bukan kepada PC 2. Kemudian PC 1 akan mengirimkan respon kepada PC 0 jika lokasi yang dituju sudah ditemukan.

**Sehingga proses PING dari PC 0 ke PC 1 terjadi broadcast**

# Skenario 3
3. Melakukan PING dari PC 0 ke PC 1 sudah dilakukan dengan melalui proses broadcast. Bagaimana jika dilakukan sebaliknya dari PC 1 melakukan PING terhadap PC 0, apakah tetap memerlukan broadcast?. Terjadinya PING dari PC 1 terhadap PC 0 **tidak lagi membutuhkan broadcast**, karena IP yang sebelumnya dilakukan dari PC 0 ke PC 1 sudah tersimpan dalam **ARP**.
>![](https://i.postimg.cc/Cx8ZK2nz/Screenshot-2022-09-11-205148.png)
Keterangan: Melakukan cek arp kembali untuk memastikan apakah IP address tersimpan dalam arp.

Sehingga jika PC 1 melakukan PING terhadap PC 0 tidak membutuhkan lagi broadcast karena sudah diketahui lokasi alamat yang ingin dituju.
>![](https://i.postimg.cc/wTdQHDG5/Screenshot-2022-09-11-204633.png)

