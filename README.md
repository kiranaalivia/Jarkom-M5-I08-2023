# Jarkom-Modul-5-I08-2023

Nama Anggota | NRP
------------------- | --------------		
Mardhatillah Shevy Ananti | 5025211070
Kirana Alivia Enrico | 5025211190

## List of Contents
- [List of Contents](#List-of-Contents)
- [Task A (Topology)](#topology)
- [Task B (VLSM)](#vlsm)
- [Task C (Routing)](#routing)
- [Task D (DHCP)](#dhcp)

## Task A (Topology)
> Tugas pertama, buatlah peta wilayah sesuai berikut ini:
>
> <img src="./img/Topology.png" width="500">
>
> Keterangan: Richter adalah DNS Server, Revolte adalah DHCP Server, Sein dan Stark adalah Web Server, Jumlah Host pada SchwerMountain adalah 64, Jumlah Host pada LaubHills adalah 255, Jumlah Host pada TurkRegion adalah 1022, Jumlah Host pada GrobeForest adalah 512

### GNS Topology
<img src="./img/GNS Topology.png" width="500">

## NetWork Configuration

- Aura
```
#A8
auto eth0
iface eth0 inet dhcp

#A9
auto eth1
iface eth1 inet static
	address 192.232.1.25
	netmask 255.255.255.252

#A7
auto eth2
iface eth2 inet static
	address 192.232.1.7
	netmask 255.255.255.252

```

- Heiter
```
#A8
auto lo
iface lo inet loopback

#A9
auto eth0
iface eth0 inet static
	address 192.232.1.26
	netmask 255.255.255.252
	gateway 192.232.1.25

#A10
auto eth1
iface eth1 inet static
	address 192.232.8.1	
	netmask 255.255.248.0

#A11
auto eth2
iface eth2 inet static
	address 192.232.4.1
	netmask 255.255.252.0

```

- Frieren
```
auto lo
iface lo inet loopback

#A7
auto eth0
iface eth0 inet static
	address 192.232.1.8
	netmask 255.255.255.252
	gateway 192.232.1.7

#A6
auto eth1
iface eth1 inet static
	address 192.232.1.13
	netmask 255.255.255.252

#A5
auto eth2
iface eth2 inet static
	address 192.232.1.9
	netmask 255.255.255.252

```

- Himmel
```
auto lo
iface lo inet loopback

#A5
auto eth2
iface eth2 inet static
	address 192.232.1.10
	netmask 255.255.255.252
	gateway 192.232.1.9

#A4
auto eth0
iface eth0 inet static
	address 192.232.2.1
	netmask 255.255.254.0

#A3
auto eth1
iface eth1 inet static
	address 192.232.1.129
	netmask 255.255.255.128

```

- Fern
```
auto lo
iface lo inet loopback

#A3
auto eth2
iface eth2 inet static
	address 192.232.1.130
	netmask 255.255.252.128
	gateway 191.232.1.129

#A2
auto eth0
iface eth0 inet static
	address 192.232.1.5
	netmask 255.255.255.252

#A1
auto eth1
iface eth1 inet static
	address 192.232.1.1
	netmask 255.255.255.252

```

- Revolte
```
auto eth0
iface eth0 inet static
address 192.232.1.2
netmask 255.255.255.252
gateway 192.232.1.1

```

- Richter
```
auto eth0
iface eth0 inet static
address 192.232.1.6
netmask 255.255.255.252
gateway 192.232.1.5

```

- Stark
```
auto eth0
iface eth0 inet static
address 192.232.1.14
netmask 255.255.255.252
gateway 192.232.1.13

```

- Sein
```
auto eth0
iface eth0 inet static
address 192.232.4.2
netmask 255.255.252.0
gateway 192.232.4.1

```

- Client
```
auto eth0
iface eth0 inet dhcp

```

## Task B (VLSM)
> Untuk menghitung rute-rute yang diperlukan, gunakan perhitungan dengan metode VLSM. Buat juga pohonnya, dan lingkari subnet yang dilewati.

### Subnetting Process
<img src="./img/VLSM.png" width="500">

### Classless method to determine the length of the netmask to be used
<img src="./img/1.png" width="500">

### VLSM tree diagram 
<img src="./img/VLSM TREE.jpg" width="500">

### The division of IP addresses resulting from the VLSM tree
<img src="./img/2.png" width="500">

## Task C (Routing)
> Kemudian buatlah rute sesuai dengan pembagian IP yang kalian lakukan.

- Aura
```
#Heiter
up route add -net 192.233.4.0 netmask 255.255.252.0 gw 192.233.1.126
up route add -net 192.233.8.0 netmask 255.255.248.0 gw 192.233.1.126

#Frieren
up route add -net 192.232.1.0 netmask 255.255.255.252 gw 192.232.1.8
up route add -net 192.232.1.4 netmask 255.255.255.252 gw 192.232.1.8
up route add -net 192.232.1.128 netmask 255.255.255.128 gw 192.232.1.8
up route add -net 192.232.2.0 netmask 255.255.254.0 gw 192.232.1.8
up route add -net 192.232.1.8 netmask 255.255.255.252 gw 192.232.1.8
up route add -net 192.232.1.12 netmask 255.255.255.252 gw 192.232.1.8
up route add -net 192.232.1.6 netmask 255.255.255.252 gw 192.232.1.8

```

- Heiter
```
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.232.1.125
```

- Frieren
```
up route add -net 192.232.1.0 netmask 255.255.255.252 gw 192.232.1.10
up route add -net 192.232.1.4 netmask 255.255.255.252 gw 192.232.1.10
up route add -net 192.232.1.128 netmask 255.255.255.128 gw 192.232.1.10
up route add -net 192.232.2.0 netmask 255.255.254.0 gw 192.232.1.10
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.232.1.7

```

- himmel
```
up route add -net 192.232.1.0 netmask 255.255.255.252 gw 192.232.1.130
up route add -net 192.232.1.4 netmask 255.255.255.252 gw 192.232.1.130
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.232.1.9

```

- Fern
```
up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.232.1.129
```

## Task D (DHCP)
> Tugas berikutnya adalah memberikan ip pada subnet SchwerMountain, LaubHills, TurkRegion, dan GrobeForest menggunakan bantuan DHCP.



