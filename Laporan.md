# Laporan Resmi Praktikum Komdat-Jarkom Modul 1

> **Kelompok K-59**
> * Salsabila Rafa Syafira (5027251059)
> * Fiorellin Ilona (5027251082)

Prefix IP : 10.93.x.x  
IP Address Host : 10.4.89.250

---

## Daftar Isi

* [Soal 1](#soal-1)
* [Soal 2](#soal-2)
* [Soal 3](#soal-3)
* [Soal 4](#soal-4)
* [Soal 5](#soal-5)
* [Soal 6](#soal-6)
* [Soal 7](#soal-7)
* [Soal 8](#soal-8)
* [Soal 9](#soal-9)
* [Soal 10](#soal-10)
* [Soal 11](#soal-11)
* [Soal 12](#soal-12)
* [Soal 13](#soal-13)
* [Soal 14](#soal-14)
* [Soal 15](#soal-15)
* [Soal 16](#soal-16)
* [Soal 17](#soal-17)
* [Soal 18](#soal-18)
* [Soal 19](#soal-19)
* [Soal 20](#soal-20)

---

# Pembahasan

## Soal 1

* Membagi alamat IP untuk 17 LAN dan 16 link antar-router menggunakan VLSM  
* Membuat tabel berisi Network, Prefix, Gateway, Broadcast, IP Terpakai, dan Sisa  
* Menggambar pohon pembagian IP dan melingkari subnet jalur Dummy-Plug ke Armisael  
* Menjelaskan perhitungan salah satu subnet  

Di soal ini, satu container mewakili satu grup host. Jadi angka 500 bukan berarti kita harus membuat 500 container sungguhan  
- Rei : router gateway untuk Switch-Quarters
- Hikari : router gateway untuk Switch-Comm
- Yui : router gateway untuk Switch-Hangar
- Comm-Net : container yang mewakili 200 host di Switch-Comm
- Quarters : container yang mewakili 500 host di Switch-Quarters
- Hangar-Crew : container yang mewakili 100 host di Switch-Hangar

### Penjelasan

| Node Asal | Interface Node Asal | Interface Node Tujuan | Node Tujuan |
| :--- | :--- | :--- | :--- |
| Gendou | `eth0` | `nat0` | NAT1 |
| Gendou | `eth1` | `eth0` | Yui |
| Gendou | `eth2` | `eth0` | Hikari |
| Gendou | `eth3` | `eth0` | Asuka |
| Gendou | `eth4` | `eth0` | Kaji |
| Gendou | `eth5` | `eth0` | Misato |
| Gendou | `eth6` | `eth0` | Shigeru |
| Gendou | `eth7` | `eth0` | Fuyutsuki |
| Gendou | `eth8` | `e0` | Switch-Cmd |
| Switch-Cmd | `e1` | `eth0` | Tokyo3-Core |
| Yui | `eth1` | `eth0` | Shinji |
| Yui | `eth2` | `eth0` | Mari |
| Yui | `eth3` | `eth0` | Rei |
| Yui | `eth4` | `e0` | Switch-Hangar |
| Switch-Hangar | `e1` | `eth0` | Hangar-Crew |
| Shinji | `eth1` | `e0` | Switch-Garden |
| Switch-Garden | `e1` | `eth0` | Garden-Staff |
| Rei | `eth1` | `e0` | Switch-Quarters |
| Switch-Quarters | `e1` | `eth0` | Quarters |
| Mari | `eth1` | `e0` | Switch-Dock |
| Switch-Dock | `e1` | `eth0` | Dock-Crew |
| Hikari | `eth1` | `eth0` | Kaworu |
| Kaworu | `eth1` | `e0` | Switch-Relay |
| Switch-Relay | `e1` | `eth0` | Relay-Node |
| Hikari | `eth2` | `e0` | Switch-Comm |
| Switch-Comm | `e1` | `eth0` | Comm-Net |
| Asuka | `eth1` | `eth0` | Kensuke |
| Kensuke | `eth1` | `e0` | Switch-Bunker |
| Switch-Bunker | `e1` | `eth0` | Sachiel |
| Asuka | `eth2` | `eth0` | Ritsuko |
| Ritsuko | `eth1` | `e0` | Switch-Lab |
| Switch-Lab | `e1` | `eth0` | Entry-Plug |
| Switch-Lab | `e2` | `eth0` | Dummy-Plug |
| Asuka | `eth3` | `e0` | Switch-Archive |
| Switch-Archive | `e1` | `eth0` | Archive-Vault |
| Kaji | `eth1` | `e0` | Switch-Intel |
| Switch-Intel | `e1` | `eth0` | Spy |
| Misato | `eth1` | `e0` | Switch-Cage |
| Switch-Cage | `e1` | `eth0` | Unit-01 |
| Switch-Cage | `e2` | `eth0` | Unit-02 |
| Switch-Cage | `e3` | `eth0` | Unit-00 |
| Shigeru | `eth1` | `eth0` | Makoto |
| Makoto | `eth1` | `e0` | Switch-Radar |
| Switch-Radar | `e1` | `eth0` | Radar-Array |
| Shigeru | `eth2` | `e0` | Switch-Monolith |
| Switch-Monolith | `e1` | `eth0` | Zeruel |
| Switch-Monolith | `e2` | `eth0` | Armisael |
| Fuyutsuki | `eth1` | `eth0` | Toji |
| Toji | `eth1` | `e0` | Switch-Dogma |
| Switch-Dogma | `e1` | `eth0` | Lilith |
| Switch-Dogma | `e2` | `eth0` | Adam |
| Fuyutsuki | `eth2` | `eth0` | Maya |
| Maya | `eth1` | `e0` | Switch-Medic |
| Switch-Medic | `e1` | `eth0` | Medic-Bay |
| Switch-Medic | `e2` | `eth0` | Pen-Pen |
| Fuyutsuki | `eth3` | `e0` | Switch-Terminal |
| Switch-Terminal | `e1` | `eth0` | Magi-Casper |
| Switch-Terminal | `e2` | `eth0` | Magi-Balthasar |
| Switch-Terminal | `e3` | `eth0` | Magi-Melchior |

Tabel subnetting ada di [file ini](Pembagian-IP.pdf)  
Tree VLSM ada di [file ini](TREE.png)  
  
Perhitungan Subnet Kedua — A2 (`10.93.2.0/24`)
> **Comm-Net:** 200 host   
> **Router Hikari (Gateway):** 1 IP  
> **Total Kebutuhan:** $200 + 1 = 201$ IP  
  
Mencari ukuran blok alamat yang mencukupi untuk 201 IP  
- $2^7 = 128$ (tidak mencukupi)
- $2^8 = 256$ (mencukupi)
Maka, dibutuhkan blok dengan total **256 alamat**  
  
$$\text{Prefix} = 32 - 8 = \mathbf{/24}$$
  
Dengan Network Address awal **`10.93.2.0`**, rincian rentang alamatnya adalah:
- **Network Address:** `10.93.2.0`
- **Gateway (Hikari):** `10.93.2.1`
- **Alokasi Host (Comm-Net):** `10.93.2.2` s.d. `10.93.2.201`
- **IP Usable Terakhir:** `10.93.2.254`
- **Broadcast Address:** `10.93.2.255`
- **Total Alamat:**
  $$2^8 = 256$$
- **IP Usable** (Total Alamat dikurangi Network dan Broadcast):
  $$256 - 2 = \mathbf{254\text{ IP}}$$
- **Sisa IP Usable** (IP Usable dikurangi kebutuhan):
  $$254 - 201 = \mathbf{53\text{ IP}}$$

---

## Soal 2

* Membuat seluruh node di GNS3 sesuai topologi
* Memberikan IP ke setiap interface router berdasarkan hasil subnet soal 1
* Mengaktifkan IP forwarding di semua router
* Mengatur Gendo agar mendapat IP otomatis dari NAT1 melalui DHCP
* Memastikan setiap link antar-router bisa saling ping
* Menampilkan hasil ip -br dari setiap router
  
> Pada soal ini, seluruh router pada topologi Geofront (17 router) harus dikonfigurasi pengalamatan IP-nya sesuai dengan hasil perhitungan VLSM Soal 1 dan pemetaan interface topologi. Selain itu, fitur IP forwarding harus diaktifkan pada semua router agar dapat meneruskan paket data, router Gendou harus mendapatkan IP otomatis dari NAT1 melalui DHCP, dan konektivitas dasar link point-to-point antar-router diuji menggunakan ping.

### Langkah Pengerjaan

#### 1. Edit Network Configuration

Langkah konfigurasi manual ini dilakukan di antarmuka GNS3 Web:
**Klik kanan pada node router > Configure > Edit Network Configuration**, lalu masukkan konfigurasi interface sesuai pembagian IP, kemudian simpan (Save / Apply).

<details>
<summary>1. Pada node <b>Gendou</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 10.93.4.117
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.93.4.113
    netmask 255.255.255.252

auto eth3
iface eth3 inet static
    address 10.93.4.165
    netmask 255.255.255.252

auto eth4
iface eth4 inet static
    address 10.93.4.169
    netmask 255.255.255.252

auto eth5
iface eth5 inet static
    address 10.93.4.149
    netmask 255.255.255.252

auto eth6
iface eth6 inet static
    address 10.93.4.157
    netmask 255.255.255.252

auto eth7
iface eth7 inet static
    address 10.93.4.145
    netmask 255.255.255.252

auto eth8
iface eth8 inet static
    address 10.93.4.105
    netmask 255.255.255.252
```
</details>

<details>
<summary>2. Pada node <b>Yui</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.118
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.133
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.93.4.137
    netmask 255.255.255.252

auto eth3
iface eth3 inet static
    address 10.93.4.109
    netmask 255.255.255.252

auto eth4
iface eth4 inet static
    address 10.93.3.1
    netmask 255.255.255.128
```
</details>

<details>
<summary>3. Pada node <b>Shinji</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.134
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.1
    netmask 255.255.255.224
```
</details>

<details>
<summary>4. Pada node <b>Mari</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.138
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.33
    netmask 255.255.255.240
```
</details>

<details>
<summary>5. Pada node <b>Rei</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.110
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.0.1
    netmask 255.255.254.0
```
</details>

<details>
<summary>6. Pada node <b>Hikari</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.114
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.129
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.93.2.1
    netmask 255.255.255.0
```
</details>

<details>
<summary>7. Pada node <b>Kaworu</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.130
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.3.225
    netmask 255.255.255.224
```
</details>

<details>
<summary>8. Pada node <b>Asuka</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.166
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.121
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.93.4.141
    netmask 255.255.255.252

auto eth3
iface eth3 inet static
    address 10.93.4.97
    netmask 255.255.255.252
```
</details>

<details>
<summary>9. Pada node <b>Kensuke</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.122
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.3.129
    netmask 255.255.255.192
```
</details>

<details>
<summary>10. Pada node <b>Ritsuko</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.142
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.49
    netmask 255.255.255.248
```
</details>

<details>
<summary>11. Pada node <b>Kaji</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.170
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.101
    netmask 255.255.255.252
```
</details>

<details>
<summary>12. Pada node <b>Misato</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.150
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.65
    netmask 255.255.255.248
```
</details>

<details>
<summary>13. Pada node <b>Shigeru</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.158
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.161
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.93.4.81
    netmask 255.255.255.248
```
</details>

<details>
<summary>14. Pada node <b>Makoto</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.162
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.89
    netmask 255.255.255.248
```
</details>

<details>
<summary>15. Pada node <b>Fuyutsuki</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.146
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.153
    netmask 255.255.255.252

auto eth2
iface eth2 inet static
    address 10.93.4.125
    netmask 255.255.255.252

auto eth3
iface eth3 inet static
    address 10.93.4.57
    netmask 255.255.255.248
```
</details>

<details>
<summary>16. Pada node <b>Toji</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.154
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.4.73
    netmask 255.255.255.248
```
</details>

<details>
<summary>17. Pada node <b>Maya</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.4.126
    netmask 255.255.255.252

auto eth1
iface eth1 inet static
    address 10.93.3.193
    netmask 255.255.255.224
```
</details>

---

#### 2. Config Terminal

Setelah mengedit network configuration, buka terminal (konsol) pada masing-masing router dan buat skrip `/root/soal2.sh` untuk mengaktifkan IP forwarding serta memuat konfigurasi interface:

<details>
<summary>1. Pada node <b>Gendou</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
# Aktifkan IP Forwarding
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf

# Reload konfigurasi interface dan minta DHCP dari NAT1
/gns3/bin/busybox ifup -a
/gns3/bin/udhcpc -i eth0 2>/dev/null || true
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>2. Pada node <b>Yui</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>3. Pada node <b>Shinji</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>4. Pada node <b>Mari</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>5. Pada node <b>Rei</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>6. Pada node <b>Hikari</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>7. Pada node <b>Kaworu</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>8. Pada node <b>Asuka</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>9. Pada node <b>Kensuke</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>10. Pada node <b>Ritsuko</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>11. Pada node <b>Kaji</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>12. Pada node <b>Misato</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>13. Pada node <b>Shigeru</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>14. Pada node <b>Makoto</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>15. Pada node <b>Fuyutsuki</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>16. Pada node <b>Toji</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

<details>
<summary>17. Pada node <b>Maya</b></summary>

Jalankan perintah `nano /root/soal2.sh`:
```bash
#!/bin/sh
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "net.ipv4.ip_forward = 1" >> /etc/sysctl.conf
/gns3/bin/busybox ifup -a
```
Jalankan perintah untuk memberi izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal2.sh
/root/soal2.sh
```
</details>

---

### Testing
Untuk membuktikan seluruh persyaratan Soal 2 telah terpenuhi:

1. **Verifikasi IP Forwarding**  
   Jalankan perintah berikut di sembarang router (hasil harus `1`):
   ```bash
   cat /proc/sys/net/ipv4/ip_forward
   ```
   <br><img width="538" height="50" alt="image" src="https://github.com/user-attachments/assets/4844f1bf-b9f7-4c02-90d5-7f7390a4a539" /><br>

2. **Verifikasi Antarmuka & IP Address**  
   Jalankan perintah berikut di router untuk memastikan IP terpasang dengan benar:
   ```bash
   ip -br a
   ```
   <br><img width="1078" height="377" alt="image" src="https://github.com/user-attachments/assets/a736968a-c7f6-4166-a030-5afccc1be4f9" /><br>

3. **Verifikasi DHCP NAT1 pada Router Gendou**  
   Jalankan di node **Gendou** untuk memastikan antarmuka `eth0` memperoleh IP otomatis:
   ```bash
   ip -br a show eth0
   ```
   <br><img width="577" height="51" alt="image" src="https://github.com/user-attachments/assets/54171397-397d-4373-b6d8-96af6f75c1c0" /><br>

4. **Tabel Link Point-to-Point Antar-Router**

    | Link | Router 1 (IP) | Router 2 (IP) |
    | :--- | :--- | :--- |
    | B1 | Yui (10.93.4.109) | Rei (10.93.4.110) |
    | B2 | Gendou (10.93.4.113) | Hikari (10.93.4.114) |
    | B3 | Gendou (10.93.4.117) | Yui (10.93.4.118) |
    | B4 | Asuka (10.93.4.121) | Kensuke (10.93.4.122) |
    | B5 | Fuyutsuki (10.93.4.125) | Maya (10.93.4.126) |
    | B6 | Hikari (10.93.4.129) | Kaworu (10.93.4.130) |
    | B7 | Yui (10.93.4.133) | Shinji (10.93.4.134) |
    | B8 | Yui (10.93.4.137) | Mari (10.93.4.138) |
    | B9 | Asuka (10.93.4.141) | Ritsuko (10.93.4.142) |
    | B10 | Gendou (10.93.4.145) | Fuyutsuki (10.93.4.146) |
    | B11 | Gendou (10.93.4.149) | Misato (10.93.4.150) |
    | B12 | Fuyutsuki (10.93.4.153) | Toji (10.93.4.154) |
    | B13 | Gendou (10.93.4.157) | Shigeru (10.93.4.158) |
    | B14 | Shigeru (10.93.4.161) | Makoto (10.93.4.162) |
    | B15 | Gendou (10.93.4.165) | Asuka (10.93.4.166) |
    | B16 | Gendou (10.93.4.169) | Kaji (10.93.4.170) |

5. **Perintah Pengujian Ping Antar-Router Langsung**

Untuk menguji bahwa setiap link point-to-point telah terhubung dan dapat saling ping:

- **Pada node Gendou** (menguji link B3, B2, B15, B16, B11, B10, B13):
  ```bash
  ping -c 2 10.93.4.118  # Link B3 ke Yui
  ping -c 2 10.93.4.114  # Link B2 ke Hikari
  ping -c 2 10.93.4.166  # Link B15 ke Asuka
  ping -c 2 10.93.4.170  # Link B16 ke Kaji
  ping -c 2 10.93.4.150  # Link B11 ke Misato
  ping -c 2 10.93.4.146  # Link B10 ke Fuyutsuki
  ping -c 2 10.93.4.158  # Link B13 ke Shigeru
  ```

- **Pada node Yui** (menguji link B3, B1, B7, B8):
  ```bash
  ping -c 2 10.93.4.117  # Link B3 ke Gendou
  ping -c 2 10.93.4.110  # Link B1 ke Rei
  ping -c 2 10.93.4.134  # Link B7 ke Shinji
  ping -c 2 10.93.4.138  # Link B8 ke Mari
  ```
  <br><img width="698" height="716" alt="image" src="https://github.com/user-attachments/assets/6a07c67d-573c-4d43-b0bb-052876bb4c90" /><br>

- **Pada node Hikari** (menguji link B2, B6):
  ```bash
  ping -c 2 10.93.4.113  # Link B2 ke Gendou
  ping -c 2 10.93.4.130  # Link B6 ke Kaworu
  ```

- **Pada node Asuka** (menguji link B15, B4, B9):
  ```bash
  ping -c 2 10.93.4.165  # Link B15 ke Gendou
  ping -c 2 10.93.4.122  # Link B4 ke Kensuke
  ping -c 2 10.93.4.142  # Link B9 ke Ritsuko
  ```

- **Pada node Fuyutsuki** (menguji link B10, B5, B12):
  ```bash
  ping -c 2 10.93.4.145  # Link B10 ke Gendou
  ping -c 2 10.93.4.126  # Link B5 ke Maya
  ping -c 2 10.93.4.154  # Link B12 ke Toji
  ```

- **Pada node Shigeru** (menguji link B13, B14):
  ```bash
  ping -c 2 10.93.4.157  # Link B13 ke Gendou
  ping -c 2 10.93.4.162  # Link B14 ke Makoto
  ```

- **Pada node router cabang (Leaf Routers)**:
  - **Rei**: `ping -c 2 10.93.4.109` (Link B1 ke Yui)
  - **Shinji**: `ping -c 2 10.93.4.133` (Link B7 ke Yui)
  - **Mari**: `ping -c 2 10.93.4.137` (Link B8 ke Yui)
  - **Kaworu**: `ping -c 2 10.93.4.129` (Link B6 ke Hikari)
  - **Kensuke**: `ping -c 2 10.93.4.121` (Link B4 ke Asuka)
  - **Ritsuko**: `ping -c 2 10.93.4.141` (Link B9 ke Asuka)
  - **Kaji**: `ping -c 2 10.93.4.169` (Link B16 ke Gendou)
  - **Misato**: `ping -c 2 10.93.4.149` (Link B11 ke Gendou)
  - **Makoto**: `ping -c 2 10.93.4.161` (Link B14 ke Shigeru)
  - **Maya**: `ping -c 2 10.93.4.125` (Link B5 ke Fuyutsuki)
  - **Toji**: `ping -c 2 10.93.4.153` (Link B12 ke Fuyutsuki)

---

## Soal 3

* Menghubungkan seluruh subnet menggunakan static routing 
* Menyusun rute dari Gendo ke router-router di bawahnya
* Menggunakan satu default route [rute tujuan cadangan] ke router atas untuk router selain Gendo
* Menggabungkan subnet cabang yang berurutan dan bisa diringkas menjadi satu CIDR
* Memberikan IP dan gateway sementara pada node untuk pengujian
* Membuktikan Armisael bisa ping ke Lilith, Sachiel, dan Comm-Net
  
> Pada soal ini, seluruh segmen jaringan yang sebelumnya terisolasi dihubungkan menggunakan routing statis hierarkis. Router Gendou berada di posisi root dengan default route mengarah ke NAT1, serta memiliki entri routing ke seluruh cabang di bawahnya. Pada cabang router Shigeru, subnet Switch-Monolith (A13: `10.93.4.80/29`) dan Switch-Radar (A14: `10.93.4.88/29`) digabungkan (*route summarization*) menjadi satu CIDR `10.93.4.80/28`. Semua router selain Gendou hanya memerlukan satu *default route* menuju router induk di atasnya serta rute spesifik ke cabang di bawahnya (bila ada). Selain itu, 4 node uji (Armisael, Lilith, Sachiel, dan Comm-Net) diberikan konfigurasi IP dan gateway sementara untuk menguji konektivitas end-to-end antar-cabang.
>
> **Catatan Penggunaan `ip route replace`:**  
> Seluruh skrip routing menggunakan perintah `ip route replace` alih-alih `ip route add`. Perintah `add` akan menghasilkan pesan kesalahan `RTNETLINK answers: File exists` jika rute sudah pernah dibuat sebelumnya (misalnya saat pengujian atau demonstrasi ulang). Sebaliknya, perintah `replace` bersifat idempoten (*upsert*), yaitu menambahkan jika rute belum ada atau memperbarui rute tanpa memunculkan error jika sudah ada, sehingga skrip dapat dieksekusi berulang kali secara aman.

### Langkah Pengerjaan

#### 1. Konfigurasi Routing di Router Pusat (Gendou)
Router Gendou bertindak sebagai gerbang sentral yang menghubungkan 7 cabang router Geofront. Subnet A13 dan A14 di bawah router Shigeru diringkas menjadi satu subnet `10.93.4.80/28`.

<details>
<summary>1. Pada node <b>Gendou</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
# Routing ke Cabang Yui
ip route replace 10.93.0.0/23 via 10.93.4.118 dev eth1
ip route replace 10.93.3.0/25 via 10.93.4.118 dev eth1
ip route replace 10.93.4.0/27 via 10.93.4.118 dev eth1
ip route replace 10.93.4.32/28 via 10.93.4.118 dev eth1
ip route replace 10.93.4.108/30 via 10.93.4.118 dev eth1
ip route replace 10.93.4.132/30 via 10.93.4.118 dev eth1
ip route replace 10.93.4.136/30 via 10.93.4.118 dev eth1

# Routing ke Cabang Hikari
ip route replace 10.93.2.0/24 via 10.93.4.114 dev eth2
ip route replace 10.93.3.224/27 via 10.93.4.114 dev eth2
ip route replace 10.93.4.128/30 via 10.93.4.114 dev eth2

# Routing ke Cabang Asuka
ip route replace 10.93.3.128/26 via 10.93.4.166 dev eth3
ip route replace 10.93.4.48/29 via 10.93.4.166 dev eth3
ip route replace 10.93.4.96/30 via 10.93.4.166 dev eth3
ip route replace 10.93.4.120/30 via 10.93.4.166 dev eth3
ip route replace 10.93.4.140/30 via 10.93.4.166 dev eth3

# Routing ke Cabang Kaji
ip route replace 10.93.4.100/30 via 10.93.4.170 dev eth4

# Routing ke Cabang Misato
ip route replace 10.93.4.64/29 via 10.93.4.150 dev eth5

# Routing ke Cabang Shigeru (A13 dan A14 diringkas menjadi 10.93.4.80/28)
ip route replace 10.93.4.80/28 via 10.93.4.158 dev eth6
ip route replace 10.93.4.160/30 via 10.93.4.158 dev eth6

# Routing ke Cabang Fuyutsuki
ip route replace 10.93.3.192/27 via 10.93.4.146 dev eth7
ip route replace 10.93.4.56/29 via 10.93.4.146 dev eth7
ip route replace 10.93.4.72/29 via 10.93.4.146 dev eth7
ip route replace 10.93.4.124/30 via 10.93.4.146 dev eth7
ip route replace 10.93.4.152/30 via 10.93.4.146 dev eth7
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

#### 2. Konfigurasi Routing di Router Percabangan (Intermediate Routers)
Router percabangan memiliki router turunan di bawahnya, sehingga membutuhkan default route ke router induk (Gendou) dan rute spesifik menuju cabang di bawahnya.

<details>
<summary>2. Pada node <b>Yui</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.117 dev eth0
ip route replace 10.93.4.0/27 via 10.93.4.134 dev eth1
ip route replace 10.93.4.32/28 via 10.93.4.138 dev eth2
ip route replace 10.93.0.0/23 via 10.93.4.110 dev eth3
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>3. Pada node <b>Hikari</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.113 dev eth0
ip route replace 10.93.3.224/27 via 10.93.4.130 dev eth1
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>4. Pada node <b>Asuka</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.165 dev eth0
ip route replace 10.93.3.128/26 via 10.93.4.122 dev eth1
ip route replace 10.93.4.48/29 via 10.93.4.142 dev eth2
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>5. Pada node <b>Shigeru</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.157 dev eth0
ip route replace 10.93.4.88/29 via 10.93.4.162 dev eth1
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>6. Pada node <b>Fuyutsuki</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.145 dev eth0
ip route replace 10.93.4.72/29 via 10.93.4.154 dev eth1
ip route replace 10.93.3.192/27 via 10.93.4.126 dev eth2
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

#### 3. Konfigurasi Routing di Router Daun (Leaf Routers)
Router daun tidak memiliki router turunan di bawahnya (hanya terhubung langsung ke switch LAN masing-masing), sehingga cukup memerlukan 1 *default route* menuju router induknya.

<details>
<summary>7. Pada node <b>Rei</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.109 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>8. Pada node <b>Shinji</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.133 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>9. Pada node <b>Mari</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.137 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>10. Pada node <b>Kaworu</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.129 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>11. Pada node <b>Kensuke</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.121 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>12. Pada node <b>Ritsuko</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.141 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>13. Pada node <b>Kaji</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.169 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>14. Pada node <b>Misato</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.149 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>15. Pada node <b>Makoto</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.161 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>16. Pada node <b>Maya</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.125 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>17. Pada node <b>Toji</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip route replace default via 10.93.4.153 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

#### 4. Konfigurasi IP dan Gateway Sementara pada Node Uji
Sesuai glosarium soal, gateway adalah IP usable pertama subnet, dan node uji diberi IP usable berikutnya:
- **Armisael** (Switch-Monolith, Subnet A13): IP `10.93.4.83/29`, Gateway `10.93.4.81`
- **Lilith** (Switch-Dogma, Subnet A12): IP `10.93.4.74/29`, Gateway `10.93.4.73`
- **Sachiel** (Switch-Bunker, Subnet A4): IP `10.93.3.130/26`, Gateway `10.93.3.129`
- **Comm-Net** (Switch-Comm, Subnet A2): IP `10.93.2.2/24`, Gateway `10.93.2.1`

<details>
<summary>18. Pada node <b>Armisael</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip addr flush dev eth0 2>/dev/null || true
ip addr add 10.93.4.83/29 dev eth0
ip link set eth0 up
ip route replace default via 10.93.4.81 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>19. Pada node <b>Lilith</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip addr flush dev eth0 2>/dev/null || true
ip addr add 10.93.4.74/29 dev eth0
ip link set eth0 up
ip route replace default via 10.93.4.73 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>20. Pada node <b>Sachiel</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip addr flush dev eth0 2>/dev/null || true
ip addr add 10.93.3.130/26 dev eth0
ip link set eth0 up
ip route replace default via 10.93.3.129 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

<details>
<summary>21. Pada node <b>Comm-Net</b></summary>

Jalankan perintah `nano /root/soal3.sh`:
```bash
#!/bin/sh
ip addr flush dev eth0 2>/dev/null || true
ip addr add 10.93.2.2/24 dev eth0
ip link set eth0 up
ip route replace default via 10.93.2.1 dev eth0
```
Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal3.sh
/root/soal3.sh
```
</details>

### Testing

Pengujian Soal 3 dilakukan untuk membuktikan seluruh 6 poin persyaratan yang diminta pada soal:

1. **Menghubungkan Seluruh Subnet Menggunakan Static Routing**  
   *Membuktikan: Seluruh router dikonfigurasi menggunakan static route tanpa ketergantungan protokol dinamis.*  
   Jalankan di salah satu router perantara, misalnya node **Yui**:
   ```bash
   ip route
   ```
   <br><img width="594" height="169" alt="image" src="https://github.com/user-attachments/assets/a3c20bbe-dbed-4d6b-8163-1991b9b98541" /><br>

   *Output verifikasi:*
   ```text
   default via 10.93.4.117 dev eth0 
   10.93.0.0/23 via 10.93.4.110 dev eth3 
   10.93.3.0/25 dev eth4 proto kernel scope link src 10.93.3.1 
   10.93.4.0/27 via 10.93.4.134 dev eth1 
   10.93.4.32/28 via 10.93.4.138 dev eth2 
   10.93.4.108/30 dev eth3 proto kernel scope link src 10.93.4.109 
   10.93.4.116/30 dev eth0 proto kernel scope link src 10.93.4.118 
   10.93.4.132/30 dev eth1 proto kernel scope link src 10.93.4.133 
   10.93.4.136/30 dev eth2 proto kernel scope link src 10.93.4.137
   ```
   *Hasil: Terlihat seluruh subnet terhubung dengan rute statis menuju cabang masing-masing.*

2. **Menyusun Rute dari Gendo ke Router-Router di Bawahnya**  
   *Membuktikan: Router Gendou memiliki rute lengkap ke 7 cabang anak (Yui, Hikari, Asuka, Kaji, Misato, Shigeru, Fuyutsuki).*  
   Jalankan di node **Gendou**:
   ```bash
   ip route
   ```
   <br><img width="643" height="595" alt="image" src="https://github.com/user-attachments/assets/32db6b7f-8472-4bcd-9767-35ae12b78452" /><br>

   *Output verifikasi rute cabang:*
   ```text
   # Cabang Yui
   10.93.0.0/23 via 10.93.4.118 dev eth1
   10.93.3.0/25 via 10.93.4.118 dev eth1
   10.93.4.0/27 via 10.93.4.118 dev eth1
   10.93.4.32/28 via 10.93.4.118 dev eth1
   10.93.4.108/30 via 10.93.4.118 dev eth1
   10.93.4.132/30 via 10.93.4.118 dev eth1
   10.93.4.136/30 via 10.93.4.118 dev eth1
   # Cabang Hikari
   10.93.2.0/24 via 10.93.4.114 dev eth2
   10.93.3.224/27 via 10.93.4.114 dev eth2
   10.93.4.128/30 via 10.93.4.114 dev eth2
   # Cabang Asuka
   10.93.3.128/26 via 10.93.4.166 dev eth3
   10.93.4.48/29 via 10.93.4.166 dev eth3
   10.93.4.96/30 via 10.93.4.166 dev eth3
   10.93.4.120/30 via 10.93.4.166 dev eth3
   10.93.4.140/30 via 10.93.4.166 dev eth3
   # Cabang Kaji
   10.93.4.100/30 via 10.93.4.170 dev eth4
   # Cabang Misato
   10.93.4.64/29 via 10.93.4.150 dev eth5
   # Cabang Shigeru (Summarized CIDR)
   10.93.4.80/28 via 10.93.4.158 dev eth6
   10.93.4.160/30 via 10.93.4.158 dev eth6
   # Cabang Fuyutsuki
   10.93.3.192/27 via 10.93.4.146 dev eth7
   10.93.4.56/29 via 10.93.4.146 dev eth7
   10.93.4.72/29 via 10.93.4.146 dev eth7
   10.93.4.124/30 via 10.93.4.146 dev eth7
   10.93.4.152/30 via 10.93.4.146 dev eth7
   ```
   *Hasil: Gendou memiliki pemetaan rute lengkap untuk mengarahkan lalu lintas ke setiap cabang di bawahnya.*

3. **Menggunakan Satu Default Route ke Router Atas untuk Router Selain Gendo**  
   *Membuktikan: Setiap router anak hanya membutuhkan satu rute default (`default via ...`) menuju router atasnya untuk semua tujuan di luar cabangnya.*  
   Jalankan di router daun (misal **Shinji**) dan router perantara (misal **Shigeru**):
   ```bash
   # Di node Shinji:
   ip route show default
   # Di node Shigeru:
   ip route show default
   ```
   <br><img width="339" height="38" alt="image" src="https://github.com/user-attachments/assets/905bfb09-1223-4805-8256-ff1efbad7299" /><br>
   <br><img width="348" height="40" alt="image" src="https://github.com/user-attachments/assets/a5d538db-9f6e-4011-877d-c1fdc924da55" <br>
   *Output verifikasi:*
   * Pada **Shinji**: `default via 10.93.4.133 dev eth0` (mengarah ke induknya, Yui).
   * Pada **Shigeru**: `default via 10.93.4.157 dev eth0` (mengarah ke induknya, Gendou).
   *Hasil: Tepat hanya terdapat satu baris default route pada setiap router selain Gendou.*

4. **Menggabungkan Subnet Cabang yang Berurutan Menjadi Satu CIDR (Route Summarization)**  
   *Membuktikan: Subnet Switch-Monolith (A13: `10.93.4.80/29`) dan Switch-Radar (A14: `10.93.4.88/29`) diringkas menjadi satu CIDR `10.93.4.80/28`.*  
   
   a. **Verifikasi Tabel Routing Gendou:**  
   Jalankan di node **Gendou**:
   ```bash
   ip route | grep 10.93.4.80
   ```
   <br><img width="387" height="33" alt="image" src="https://github.com/user-attachments/assets/64fc5bb4-d899-43e1-aa00-54068fd82b1e" /><br>

   *Output:*
   ```text
   10.93.4.80/28 via 10.93.4.158 dev eth6
   ```
   *(Terbukti hanya terdapat 1 entri agregat `/28` untuk kedua subnet, bukan 2 entri terpisah `/29`).*

   b. **Verifikasi FIB Lookup (`ip route get`) pada Gendou:**  
   Jalankan di node **Gendou**:
   ```bash
   # Uji lookup ke host di Switch-Monolith (Armisael 10.93.4.83):
   ip route get 10.93.4.83
   # Uji lookup ke host di Switch-Radar (10.93.4.89):
   ip route get 10.93.4.89
   ```
   <br><img width="551" height="95" alt="image" src="https://github.com/user-attachments/assets/9c06ce9f-5548-4753-9224-ad9dcbc3d578" /><br>
   *Hasil: Kedua IP dari dua subnet berbeda tersebut sama-sama dipetakan ke rute summary `10.93.4.80/28 via 10.93.4.158 dev eth6`.*

5. **Memberikan IP dan Gateway Sementara pada Node untuk Pengujian**  
   *Membuktikan: Node uji memiliki konfigurasi IP antarmuka dan default route yang terpasang dengan benar.*  
   Periksa konfigurasi pada masing-masing node uji:
   * Di node **Armisael**:
     ```bash
     ip -br a show eth0; ip route show default
     ```
     <br><img width="583" height="60" alt="image" src="https://github.com/user-attachments/assets/ac6aba2c-d36e-4fde-a59b-a2fcff98ffbe" /><br>
     *Hasil: IP `10.93.4.83/29`, default gateway `10.93.4.81`.*
   * Di node **Lilith**:
     ```bash
     ip -br a show eth0; ip route show default
     ```
     <br><img width="555" height="61" alt="image" src="https://github.com/user-attachments/assets/8d8b13c4-eb4b-488f-a4eb-41185bd0cffd" /><br>

     *Hasil: IP `10.93.4.74/29`, default gateway `10.93.4.73`.*
   * Di node **Sachiel**:
     ```bash
     ip -br a show eth0; ip route show default
     ```
     <br><img width="552" height="68" alt="image" src="https://github.com/user-attachments/assets/1af4c06c-f7e6-48dd-b175-60cc5ab0578d" /><br>
     *Hasil: IP `10.93.3.130/26`, default gateway `10.93.3.129`.*
   * Di node **Comm-Net**:
     ```bash
     ip -br a show eth0; ip route show default
     ```
     <br><img width="586" height="62" alt="image" src="https://github.com/user-attachments/assets/a4c1edc3-bbe6-4d54-b65a-5f0817ddaf6a" /><br>
     *Hasil: IP `10.93.2.2/24`, default gateway `10.93.2.1`.*

6. **Membuktikan Armisael Bisa Ping ke Lilith, Sachiel, dan Comm-Net**  
   *Membuktikan: Konektivitas end-to-end antar-cabang melintasi router Gendou berjalan 100% tanpa hambatan.*  
   Jalankan seluruh pengujian dari node **Armisael**:
   ```bash
   # 1. Ping ke Lilith (Switch-Dogma, cabang Fuyutsuki/Makoto)
   ping -c 2 10.93.4.74

   # 2. Ping ke Sachiel (Switch-Bunker, cabang Asuka/Kensuke)
   ping -c 2 10.93.3.130

   # 3. Ping ke Comm-Net (Switch-Comm, cabang Hikari)
   ping -c 2 10.93.2.2
   ```
   <br><img width="738" height="579" alt="image" src="https://github.com/user-attachments/assets/826ffaad-5811-4b53-8968-b895d0521679" /><br>
   *Hasil Pengujian:*
   * Ping ke Lilith: **2 packets transmitted, 2 received, 0% packet loss**.
   * Ping ke Sachiel: **2 packets transmitted, 2 received, 0% packet loss**.
   * Ping ke Comm-Net: **2 packets transmitted, 2 received, 0% packet loss**.
---

## Soal 4

* Seluruh jaringan internal bisa akses internet lewat Gendo
* NAT tetap berfungsi meskipun IP NAT1 berubah
* Hanya menerjemahkan alamat IP traffic dari jaringan internal yang menuju internet
* Memastikan komunikasi antar-LAN tidak terkena NAT
* Mengaktifkan kemampuan DNS 
* Membuktikan koneksi dengan ping 8.8.8.8, ping deb.debian.org, dan counter rule NAT
  
> Pada soal ini, seluruh jaringan Geofront diberikan akses keluar menuju internet melalui router Gendou yang terhubung ke NAT1. Karena IP yang diberikan NAT1 bersifat dinamis (DHCP) dan dapat berganti sewaktu-waktu, konfigurasi NAT menggunakan target `MASQUERADE` pada interface `eth0`. Agar traffic antar-LAN internal tidak ikut tertranslasi alamatnya, aturan NAT dibatasi secara spesifik hanya untuk paket dengan sumber prefix internal (`-s 10.93.0.0/21`) yang keluar melalui antarmuka NAT1 (`-o eth0`). Selain itu, konfigurasi DNS resolver disiapkan pada node agar dapat melakukan translasi nama domain (*name resolution*) saat proses instalasi paket di soal-soal berikutnya.

### Langkah Pengerjaan

#### 1. Konfigurasi NAT MASQUERADE pada Router Gendou
Konfigurasi iptables pada router Gendou untuk mengaktifkan NAT dengan target MASQUERADE pada interface `eth0` khusus untuk paket dari prefix internal `10.93.0.0/21`.

Di Node **Gendou** `nano /root/soal4.sh`:
<details>
<summary>Lihat skrip <b>/root/soal4.sh</b> di Gendou</summary>

```bash
#!/bin/sh
iptables -t nat -F POSTROUTING
iptables -t nat -A POSTROUTING -s 10.93.0.0/21 -o eth0 -j MASQUERADE
```
</details>

Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal4.sh
/root/soal4.sh
```

#### 2. Konfigurasi DNS Resolver pada Node Uji (Armisael dan Lilith)
Menambahkan nameserver gateway NAT1 (`192.168.122.1`) dan public DNS (`8.8.8.8`) ke dalam berkas `/etc/resolv.conf` agar node dapat me-resolve domain seperti `deb.debian.org`.

Di Node **Armisael** `nano /root/soal4.sh`:
<details>
<summary>Lihat skrip <b>/root/soal4.sh</b> di Armisael</summary>

```bash
#!/bin/sh
echo "nameserver 192.168.122.1" > /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```
</details>

Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal4.sh
/root/soal4.sh
```

Di Node **Lilith** `nano /root/soal4.sh`:
<details>
<summary>Lihat skrip <b>/root/soal4.sh</b> di Lilith</summary>

```bash
#!/bin/sh
echo "nameserver 192.168.122.1" > /etc/resolv.conf
echo "nameserver 8.8.8.8" >> /etc/resolv.conf
```
</details>

Beri izin eksekusi dan jalankan skrip:
```bash
chmod +x /root/soal4.sh
/root/soal4.sh
```

### Testing

Pengujian keberhasilan konfigurasi Soal 4 dilakukan untuk membuktikan seluruh kriteria soal telah terpenuhi secara nyata:

1. **Pengujian Pertambahan Counter Rule NAT pada Router Gendou**  
   Untuk membuktikan bahwa counter rule NAT bertambah saat traffic internet melintas:
   - **Langkah 1 (Kondisi Awal / Reset Counter):**  
     Jalankan di node **Gendou** untuk me-reset counter menjadi 0:
     ```bash
     iptables -t nat -Z POSTROUTING
     iptables -t nat -nvL POSTROUTING
     ```
     *(Terlihat counter awal bernilai 0 packets, 0 bytes).*

   - **Langkah 2 (Mengirimkan Traffic Internet):**  
     Jalankan di node internal (**Armisael** dan **Lilith**):
     ```bash
     ping -c 2 8.8.8.8
     ping -c 2 deb.debian.org
     ```
     <img width="506" height="226" alt="image" src="https://github.com/user-attachments/assets/5a86c211-e263-4213-b565-0c8181d60442" />
   - **Langkah 3 (Kondisi Akhir / Bukti Counter Bertambah):**  
     Jalankan kembali di node **Gendou**:
     ```bash
     iptables -t nat -nvL POSTROUTING
     ```
     <br><img width="578" height="218" alt="image" src="https://github.com/user-attachments/assets/f9c91a8c-ab32-42f5-ba19-c05e932966d9" /><br>
     *(Counter `pkts` dan `bytes` terlihat bertambah, membuktikan bahwa traffic internet yang melintas dari jaringan internal berhasil ditranslasikan oleh rule MASQUERADE).*

2. **Memverifikasi Komunikasi Antar-LAN Tidak Terkena NAT**  
   Untuk membuktikan bahwa paket antar-LAN tetap membawa alamat IP pengirim asli (tidak tertranslasi oleh NAT):
   - Di terminal node **Lilith**, jalankan packet capture:
     ```bash
     tcpdump -i eth0 -n -c 2 icmp
     ```
   - Di terminal node **Armisael**, lakukan ping ke Lilith:
     ```bash
     ping -c 2 10.93.4.74
     ```
     <br><img width="579" height="143" alt="image" src="https://github.com/user-attachments/assets/05a5bbba-42b2-4f10-bcd3-7f0600b4ade8" /><br>

   *Output tcpdump pada Lilith menampilkan `IP 10.93.4.83 > 10.93.4.74: ICMP echo request`, membuktikan bahwa paket tiba dengan source IP asli Armisael (`10.93.4.83`) dan bukan IP router atau IP NAT.*

3. **Pengujian Konektivitas Internet dan Domain (DNS) dari Node Armisael**  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 8.8.8.8
   ping -c 2 deb.debian.org
   ```
   <br><img width="498" height="244" alt="image" src="https://github.com/user-attachments/assets/b5fc2763-b69e-4c4b-8c3a-eaecd9ae19fe" /><br>

4. **Pengujian Konektivitas Internet dan Domain (DNS) dari Node Lilith**  
   Jalankan di node **Lilith**:
   ```bash
   ping -c 2 8.8.8.8
   ping -c 2 deb.debian.org
   ```
   <br>![Uploading image.png<br>
---

## Soal 5

* Mengubah policy INPUT dan FORWARD di Gendo menjadi DROP
* Mengizinkan koneksi balasan yang sudah berjalan
* Mengizinkan jaringan internal mengakses internet
* Mengizinkan komunikasi antar-LAN
* Mengizinkan jaringan internal mengakses Gendo
* Memastikan loopback dan DHCP dari NAT1 tetap berjalan
* Memastikan koneksi baru dari NAT1 tidak bisa masuk
* Menulis seluruh konfigurasi soal 2–5 dalam gendo.sh
* Membuktikan konfigurasi dengan iptables -S dan ping 8.8.8.8 dari Armisael
  
> Pada soal ini, router Gendou difungsikan sebagai firewall penyaring paket dengan strategi *default deny* (policy `INPUT` dan `FORWARD` diset ke `DROP`). Gendou hanya mengizinkan lalu lintas yang sah: loopback, DHCP client pada `eth0`, koneksi balasan yang telah terbentuk (*stateful inspection* `ESTABLISHED,RELATED`), akses internet dari jaringan internal (`10.93.0.0/21` ke `eth0`), komunikasi antar-LAN (`10.93.0.0/21` ke `10.93.0.0/21`), serta akses dari jaringan internal ke Gendou sendiri. Koneksi baru yang diinisiasi dari arah luar (NAT1) akan otomatis ditolak. Seluruh konfigurasi dari Soal 2 sampai 5 diintegrasikan ke dalam satu skrip `/root/soal5.sh` (dan disalin ke `/root/gendo.sh`).

### Langkah Pengerjaan

#### 1. Pembuatan Skrip Master Konfigurasi di Router Gendou
Skrip ini menggabungkan konfigurasi Soal 2 (IP forwarding), Soal 3 (static routing hierarkis), Soal 4 (NAT Masquerade), dan Soal 5 (firewall filtering stateful & default DROP policy).

Di Node **Gendou** `nano /root/soal5.sh`:
<details>
<summary>Lihat skrip <b>/root/soal5.sh</b> (dan <b>/root/gendo.sh</b>) di Gendou</summary>

```bash
#!/bin/sh
# === 1. SOAL 2: IP FORWARDING ===
sysctl -w net.ipv4.ip_forward=1
echo 1 > /proc/sys/net/ipv4/ip_forward

# === 2. SOAL 3: ROUTING STATIS HIERARKIS ===
# Cabang Yui
ip route replace 10.93.0.0/23 via 10.93.4.118 dev eth1
ip route replace 10.93.3.0/25 via 10.93.4.118 dev eth1
ip route replace 10.93.4.0/27 via 10.93.4.118 dev eth1
ip route replace 10.93.4.32/28 via 10.93.4.118 dev eth1
ip route replace 10.93.4.108/30 via 10.93.4.118 dev eth1
ip route replace 10.93.4.132/30 via 10.93.4.118 dev eth1
ip route replace 10.93.4.136/30 via 10.93.4.118 dev eth1

# Cabang Hikari
ip route replace 10.93.2.0/24 via 10.93.4.114 dev eth2
ip route replace 10.93.3.224/27 via 10.93.4.114 dev eth2
ip route replace 10.93.4.128/30 via 10.93.4.114 dev eth2

# Cabang Asuka
ip route replace 10.93.3.128/26 via 10.93.4.166 dev eth3
ip route replace 10.93.4.48/29 via 10.93.4.166 dev eth3
ip route replace 10.93.4.96/30 via 10.93.4.166 dev eth3
ip route replace 10.93.4.120/30 via 10.93.4.166 dev eth3
ip route replace 10.93.4.140/30 via 10.93.4.166 dev eth3

# Cabang Kaji
ip route replace 10.93.4.100/30 via 10.93.4.170 dev eth4

# Cabang Misato
ip route replace 10.93.4.64/29 via 10.93.4.150 dev eth5

# Cabang Shigeru (Ringkasan A13 dan A14 menjadi 10.93.4.80/28)
ip route replace 10.93.4.80/28 via 10.93.4.158 dev eth6
ip route replace 10.93.4.160/30 via 10.93.4.158 dev eth6

# Cabang Fuyutsuki
ip route replace 10.93.3.192/27 via 10.93.4.146 dev eth7
ip route replace 10.93.4.56/29 via 10.93.4.146 dev eth7
ip route replace 10.93.4.72/29 via 10.93.4.146 dev eth7
ip route replace 10.93.4.124/30 via 10.93.4.146 dev eth7
ip route replace 10.93.4.152/30 via 10.93.4.146 dev eth7

# === 3. SOAL 4: NAT MASQUERADE ===
iptables -t nat -F POSTROUTING
iptables -t nat -A POSTROUTING -s 10.93.0.0/21 -o eth0 -j MASQUERADE

# === 4. SOAL 5: FIREWALL FILTERING ===
# Flush rule filter lama
iptables -F INPUT
iptables -F FORWARD
iptables -F OUTPUT

# Ubah default policy INPUT dan FORWARD menjadi DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# 1. Izinkan loopback interface
iptables -A INPUT -i lo -j ACCEPT

# 2. Izinkan paket DHCP client dari NAT1 pada eth0
iptables -A INPUT -i eth0 -p udp --dport 68 -j ACCEPT

# 3. (a) Izinkan paket balasan dari koneksi yang sudah ada (stateful)
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# 4. (b) Izinkan traffic keluar dari jaringan internal ke internet
iptables -A FORWARD -s 10.93.0.0/21 -o eth0 -j ACCEPT

# 5. (c) Izinkan traffic antar-LAN
iptables -A FORWARD -s 10.93.0.0/21 -d 10.93.0.0/21 -j ACCEPT

# 6. (d) Izinkan traffic dari jaringan internal ke Gendou sendiri
iptables -A INPUT -s 10.93.0.0/21 -j ACCEPT
```
</details>

Beri izin eksekusi, buat salinan ke `/root/gendo.sh`, dan jalankan skrip:
```bash
chmod +x /root/soal5.sh
cp /root/soal5.sh /root/gendo.sh
chmod +x /root/gendo.sh
/root/soal5.sh
```

### Testing

Pengujian Soal 5 membuktikan seluruh 9 poin persyaratan yang diminta pada soal:

1. **Memverifikasi Policy DROP dan Seluruh Aturan Firewall (`iptables -S`)**  
   *Membuktikan: Policy INPUT & FORWARD diset ke DROP, loopback & DHCP diizinkan, stateful inspection aktif, akses internet, antar-LAN, dan akses internal ke Gendou diizinkan, serta koneksi baru dari NAT1 tertolak.*  
   Jalankan di node **Gendou**:
   ```bash
   iptables -S
   ```
   *Output verifikasi:*
   ```text
   -P INPUT DROP
   -P FORWARD DROP
   -P OUTPUT ACCEPT
   -A INPUT -i lo -j ACCEPT
   -A INPUT -i eth0 -p udp -m udp --dport 68 -j ACCEPT
   -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
   -A INPUT -s 10.93.0.0/21 -j ACCEPT
   -A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
   -A FORWARD -s 10.93.0.0/21 -o eth0 -j ACCEPT
   -A FORWARD -s 10.93.0.0/21 -d 10.93.0.0/21 -j ACCEPT
   ```

2. **Memverifikasi Counter Paket dan Byte pada Tiap Aturan Firewall (`iptables -nvL`)**  
   *Membuktikan: Setiap aturan bekerja aktif dan menangkap paket secara nyata (termasuk paket balasan ESTABLISHED dan pencegahan paket liar).*  
   Jalankan di node **Gendou**:
   ```bash
   iptables -nvL
   ```
   <br><img width="1103" height="271" alt="image" src="https://github.com/user-attachments/assets/834883a8-08d8-4662-85ae-da23aa9d7591" /><br>
   *Output verifikasi:*
   ```text
   Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts bytes target     prot opt in     out     source               destination         
       4   336 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0     0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
       1    84 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       1    84 ACCEPT     all  --  *      *       10.93.0.0/21         0.0.0.0/0           

   Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts bytes target     prot opt in     out     source               destination         
       9   756 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
       2   168 ACCEPT     all  --  *      eth0    10.93.0.0/21         0.0.0.0/0           
       1    84 ACCEPT     all  --  *      *       10.93.0.0/21         10.93.0.0/21        

   Chain OUTPUT (policy ACCEPT 6 packets, 504 bytes)
   ```

3. **Membuktikan Loopback Tetap Berfungsi pada Gendou**  
   *Membuktikan: Aturan loopback `lo` mengizinkan traffic lokal meskipun policy INPUT DROP.*  
   Jalankan di node **Gendou**:
   ```bash
   ping -c 2 127.0.0.1
   ```
   <br><img width="604" height="134" alt="image" src="https://github.com/user-attachments/assets/c9b814d8-32df-4fea-b89a-743b67189651" /><br>
   *Hasil: Berhasil (2 packets transmitted, 2 received, 0% packet loss).*

4. **Membuktikan Akses Internet dari Jaringan Internal dan Koneksi Balasan Berjalan**  
   *Membuktikan: Rule FORWARD internal ke internet dan koneksi balasan (`ESTABLISHED,RELATED`) bekerja (karena tanpa aturan balasan, reply paket dari 8.8.8.8 akan di-drop oleh policy FORWARD DROP).*  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 8.8.8.8
   ```
   <br><img width="598" height="158" alt="image" src="https://github.com/user-attachments/assets/87b28864-5884-4dac-a14a-76389f129225" /><br>
   *Hasil: Berhasil (2 packets transmitted, 2 received, 0% packet loss, rtt avg ~20ms).*

5. **Membuktikan Komunikasi Antar-LAN Berhasil**  
   *Membuktikan: Paket antar-subnet `10.93.0.0/21` dapat melintasi router Gendou secara aman.*  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 10.93.4.74
   ```
   <br><img width="583" height="137" alt="image" src="https://github.com/user-attachments/assets/652a147a-1b5b-433d-a696-5231c88845dc" /><br>
   *Hasil: Berhasil ping ke Lilith di Switch-Dogma (0% packet loss).*

6. **Membuktikan Jaringan Internal Bisa Mengakses Gendou**  
   *Membuktikan: Paket dari subnet internal menuju IP interface Gendou diizinkan masuk ke chain INPUT.*  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 10.93.4.157
   ```
   <br><img width="613" height="134" alt="image" src="https://github.com/user-attachments/assets/399f4e82-2200-4aef-9315-c5ab68185a42" /><br>
   *Hasil: Berhasil ping ke IP Gendou (0% packet loss).*

7. **Membuktikan Koneksi Baru dari NAT1 Tidak Bisa Masuk**  
   *Penjelasan & Pembuktian: Policy default INPUT dan FORWARD adalah DROP. Pada interface eth0 (arah NAT1), hanya paket berstatus `ESTABLISHED,RELATED` atau DHCP (UDP 68) yang diizinkan. Paket baru (`state NEW`) yang datang dari arah NAT1 tidak memiliki rule kecocokan sehingga otomatis dibuang (DROP) oleh kernel.*

---

## Soal 6
>- Mengatur konfigurasi IP statis secara permanen pada seluruh end-device (host/node) agar tidak hilang saat node di-restart
- Menerapkan alamat IP, netmask, dan default gateway pada setiap node berdasarkan tabel VLSM Soal 1
- Melakukan pengujian persistensi konfigurasi pada node **Unit-01** setelah restart menggunakan perintah `ip -br a` dan `ping -c 3 10.93.4.65`

> Berbeda dengan konfigurasi sementara menggunakan script `/root/soal3.sh` yang akan terhapus ketika node di-restart, pada soal ini pengalamatan IP dikonfigurasi secara permanen melalui file konfigurasi jaringan (`/etc/network/interfaces`) di setiap end-device. Pengujian dilakukan dengan me-restart node **Unit-01** dan memverifikasi bahwa IP address serta konektivitas ke gateway tetap bertahan tanpa menjalankan ulang script sementara.

### Langkah Pengerjaan

#### 1. Tabel Pembagian IP Address End-Device

Berikut adalah daftar pemetaan IP statis, netmask, dan gateway untuk seluruh node berdasarkan perhitungan VLSM:

| Node | IP Address | Netmask | Gateway |
| :--- | :--- | :--- | :--- |
| **Quarters** | `10.93.0.2` | `255.255.254.0` | `10.93.0.1` |
| **Comm-Net** | `10.93.2.2` | `255.255.255.0` | `10.93.2.1` |
| **Hangar-Crew** | `10.93.3.2` | `255.255.255.128` | `10.93.3.1` |
| **Sachiel** | `10.93.3.130` | `255.255.255.192` | `10.93.3.129` |
| **Medic-Bay**|  `10.93.3.195` | `255.255.255.224` | `10.93.3.193` |
| **Pen-Pen** |  `10.93.3.194` | `255.255.255.224` | `10.93.3.193` |
| **Relay-Node** | `10.93.3.226` | `255.255.255.224` | `10.93.3.225` |
| **Garden-Staff** | `10.93.4.2` | `255.255.255.224` | `10.93.4.1` |
| **Dock-Crew** | `10.93.4.34` | `255.255.255.240` | `10.93.4.33` |
| **Entry-Plug** | `10.93.4.50` | `255.255.255.248` | `10.93.4.49` |
| **Dummy-Plug** | `10.93.4.51` | `255.255.255.248` | `10.93.4.49` |
| **Magi-Casper** | `10.93.4.58` | `255.255.255.248` | `10.93.4.57` |
| **Magi-Balthasar** | `10.93.4.59` | `255.255.255.248` | `10.93.4.57` |
| **Magi-Melchior** | `10.93.4.60` | `255.255.255.248` | `10.93.4.57` |
| **Unit-01** | `10.93.4.66` | `255.255.255.248` | `10.93.4.65` |
| **Unit-02** | `10.93.4.67` | `255.255.255.248` | `10.93.4.65` |
| **Unit-00** | `10.93.4.68` | `255.255.255.248` | `10.93.4.65` |

> **Catatan Switch-Medic:** Penentuan urutan IP pada segmen Switch-Medic (`10.93.3.192/27`) disesuaikan dengan konfirmasi asisten (mengikuti topologi gambar: **Medic-Bay** `.194` & **Pen-Pen** `.195`, atau mengikuti Tabel Host: **Pen-Pen** `.194` & **Medic-Bay** `.195`).

---
#### 2. Edit Network Configuration pada Setiap Node

Langkah konfigurasi dilakukan melalui antarmuka GNS3:
**Klik kanan pada node > Configure > Edit Network Configuration**, lalu masukkan konfigurasi berikut dan klik **Save**.

<details>
<summary>1. Pada node <b>Quarters</b></summary>

```text
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 10.93.0.2
    netmask 255.255.254.0
    gateway 10.93.0.1
```
#### 3.Pengujian Persistensi Konfigurasi pada Unit-01
<img width="1112" height="826" alt="image" src="https://github.com/user-attachments/assets/2942ff9b-8194-411e-8b78-5c00a9411460" />

---
## Soal 7
> Memasang `iptables` dan `netcat-traditional` di tiga node MAGI (Casper, Balthasar, Melchior) lewat script di `/root`, lalu menyalakan listener TCP sesuai glosarium (Casper 5000, Balthasar 5000 dan 5001, Melchior 5000). Node MAGI memakai image `debinet` karena `netcat-traditional` adalah paket Debian. Pengujian dilakukan dari Lilith.

1. Buat script di `Magi-Casper` (SCRIPT DITULIS DI ROOT SUPAYA BISA DIDEMONSTRASIKAN ULANG):
   ```bash
   cat > /root/casper.sh << 'EOF'
   #!/bin/sh
   echo "nameserver 8.8.8.8" > /etc/resolv.conf
   command -v iptables >/dev/null || { apt-get update; apt-get install -y iptables; }
   dpkg -s netcat-traditional >/dev/null 2>&1 || { apt-get update; apt-get install -y netcat-traditional; }
   update-alternatives --set nc /bin/nc.traditional 2>/dev/null
   pkill -f "nc -l -p" 2>/dev/null
   nohup sh -c 'while true; do nc -l -p 5000 >> /root/nc5000.log; done' >/dev/null 2>&1 &
   EOF
   chmod +x /root/casper.sh
   /root/casper.sh
   netstat -tln | grep 5000
   ```
2. Buat script di `Magi-Balthasar` (dua port):
   ```bash
   cat > /root/balthasar.sh << 'EOF'
   #!/bin/sh
   echo "nameserver 8.8.8.8" > /etc/resolv.conf
   command -v iptables >/dev/null || { apt-get update; apt-get install -y iptables; }
   dpkg -s netcat-traditional >/dev/null 2>&1 || { apt-get update; apt-get install -y netcat-traditional; }
   update-alternatives --set nc /bin/nc.traditional 2>/dev/null
   pkill -f "nc -l -p" 2>/dev/null
   nohup sh -c 'while true; do nc -l -p 5000 >> /root/nc5000.log; done' >/dev/null 2>&1 &
   nohup sh -c 'while true; do nc -l -p 5001 >> /root/nc5001.log; done' >/dev/null 2>&1 &
   EOF
   chmod +x /root/balthasar.sh
   /root/balthasar.sh
   netstat -tln | grep -E '5000|5001'
   ```
3. Buat script di `Magi-Melchior` (sama seperti Casper, hanya port 5000):
   ```bash
   cat > /root/melchior.sh << 'EOF'
   #!/bin/sh
   echo "nameserver 8.8.8.8" > /etc/resolv.conf
   command -v iptables >/dev/null || { apt-get update; apt-get install -y iptables; }
   dpkg -s netcat-traditional >/dev/null 2>&1 || { apt-get update; apt-get install -y netcat-traditional; }
   update-alternatives --set nc /bin/nc.traditional 2>/dev/null
   pkill -f "nc -l -p" 2>/dev/null
   nohup sh -c 'while true; do nc -l -p 5000 >> /root/nc5000.log; done' >/dev/null 2>&1 &
   EOF
   chmod +x /root/melchior.sh
   /root/melchior.sh
   netstat -tln | grep 5000
   ```
4. Dari `Lilith`, kirim pesan ke ketiga MAGI dan ke port 5001 Balthasar:
   ```bash
   echo "Halo Casper dari Lilith"          | nc -w 3 10.93.4.58 5000
   echo "Halo Balthasar 5000 dari Lilith"  | nc -w 3 10.93.4.59 5000
   echo "Halo Balthasar 5001 dari Lilith"  | nc -w 3 10.93.4.59 5001
   echo "Halo Melchior dari Lilith"        | nc -w 3 10.93.4.60 5000
   ```
5. Tampilkan pesan yang diterima di tiap node:
   ```bash
   cat /root/nc5000.log      # Casper, Balthasar, Melchior
   cat /root/nc5001.log      # Balthasar
   ```
   

---

## Soal 8
> Pen-Pen dan Tokyo3-Core melayani dulu supaya kondisi normalnya terlihat. Port 80 menjawab `Welcome to {hostname}`, port 8080 di Tokyo3-Core menjawab `syifa imutz`. Dari Lilith diuji `nc` ke ketiga port, dan port yang tidak dilayani (22) harus gagal seketika, bukan menggantung. Karena `nc` busybox tidak mencetak pesan error, bukti port tertutup memakai exit code dan durasi koneksi.

1. Buat script di `Pen-Pen`:
   ```bash
   cat > /root/penpen.sh << 'EOF'
   #!/bin/sh
   pkill -f "nc -l -p" 2>/dev/null
   nohup sh -c 'while true; do echo "Welcome to $(hostname)" | nc -l -p 80; done' >/dev/null 2>&1 &
   EOF
   chmod +x /root/penpen.sh
   /root/penpen.sh
   netstat -tln
   ```
2. Buat script di `Tokyo3-Core`:
   ```bash
   cat > /root/tokyo3.sh << 'EOF'
   #!/bin/sh
   pkill -f "nc -l -p" 2>/dev/null
   nohup sh -c 'while true; do echo "Welcome to $(hostname)" | nc -l -p 80; done' >/dev/null 2>&1 &
   nohup sh -c 'while true; do echo "syifa imutz" | nc -l -p 8080; done' >/dev/null 2>&1 &
   EOF
   chmod +x /root/tokyo3.sh
   /root/tokyo3.sh
   netstat -tln
   ```
3. Dari `Lilith`, uji ketiga port:
   ```bash
   nc -w 3 <IP-Pen-Pen> 80      # Welcome to Pen-Pen
   nc -w 3 10.93.4.106 80       # Welcome to Tokyo3-Core
   nc -w 3 10.93.4.106 8080     # syifa imutz
   ```
   
4. Buktikan port yang tidak dilayani langsung gagal:
   ```bash
   time nc -w 5 10.93.4.106 22 </dev/null; echo "exit=$?"
   time nc -w 5 <IP-Pen-Pen> 22 </dev/null; echo "exit=$?"
   ```
   Hasil: selesai dalam hitungan milidetik dengan `exit=1`, artinya ditolak seketika, bukan timeout 5 detik.
 
---

## Soal 9
> Script `break_routing.sh` dijalankan di Shigeru tanpa dibaca isinya. Gejala: Lilith tidak mendapat jawaban dari Armisael, padahal Armisael masih bisa ping gateway-nya. Kondisi acuan Shigeru: `eth0 10.93.4.158/30`, `eth1 10.93.4.161/30`, `eth2 10.93.4.81/29`, `default via 10.93.4.157 dev eth0`, `10.93.4.88/29 via 10.93.4.162 dev eth1`, `ip_forward = 1`, tanpa `ip rule` tambahan.

1. Catat kondisi sebelum di `Shigeru`, lalu jalankan script:
   ```bash
   ip route > /root/sebelum.txt
   iptables -S >> /root/sebelum.txt
   cat /proc/sys/net/ipv4/ip_forward >> /root/sebelum.txt
   chmod +x /root/break_routing.sh
   /root/break_routing.sh
   ```
2. Buktikan gejala:
   ```bash
   # Lilith
   ping -c 2 10.93.4.83      # gagal
   # Armisael
   ping -c 2 10.93.4.81      # gateway, berhasil
   ```
  
3. Diagnosis di `Shigeru`:
   ```bash
   ip -br a
   ip route
   cat /proc/sys/net/ipv4/ip_forward
   iptables -S
   ip rule
   cat /proc/sys/net/ipv4/conf/all/rp_filter
   cat /proc/sys/net/ipv4/icmp_echo_ignore_all
   ip route get 10.93.4.74
   ```


   Penyebab (ada empat):

   | Item | Kondisi acuan | Setelah script |
   | :--- | :--- | :--- |
   | `ip_forward` | `1` | `0` |
   | default route | `via 10.93.4.157 dev eth0` | `via 10.93.4.162 dev eth1` |
   | rute subnet Lilith | tidak ada (lewat default) | `blackhole 10.93.4.72/29` |
   | `ip rule` | 3 baris bawaan | tambahan `90: from all iif eth2 lookup 100` |

   `iptables`, `rp_filter`, dan `icmp_echo_ignore_all` tidak berubah.

   Kenapa gejalanya begitu: ping Armisael ke gateway `10.93.4.81` berada dalam satu subnet, jadi tidak butuh forwarding atau rute. Paket antar-subnet butuh forwarding dan rute balik yang benar. Dengan `ip_forward = 0`, Shigeru tidak meneruskan paket. Default route ke Makoto membuat paket ke luar zona salah arah. Rute `blackhole` membuang balasan ke subnet Lilith. Rule `iif eth2 lookup 100` membuat traffic dari sisi Monolith memakai tabel rute yang bukan tabel utama.
4. Perbaiki di `Shigeru`:
   ```bash
   echo 1 > /proc/sys/net/ipv4/ip_forward
   ip route del blackhole 10.93.4.72/29
   ip route replace default via 10.93.4.157 dev eth0
   ip route replace 10.93.4.88/29 via 10.93.4.162 dev eth1
   ip rule del priority 90
   ip route flush table 100
   ip route get 10.93.4.74     # via 10.93.4.157 dev eth0
   ```
5. Bukti setelah perbaikan:
   ```bash
   # Lilith
   ping -c 2 10.93.4.83      # berhasil
   # Armisael
   ping -c 2 10.93.4.74      # berhasil
   ```
  

---

## Soal 10
> Script `break_nat.sh` dijalankan di Misato dan di Gendou (file yang sama, tanpa dibaca isinya). Gejala: Unit-01, Unit-02, Unit-00 di Cage tidak bisa ping `8.8.8.8`, sementara Spy di Intel normal dan ping Cage ke Lilith normal.

1. Catat kondisi sebelum di `Gendou` dan `Misato`, lalu jalankan script di keduanya:
   ```bash
   ip route > /root/sebelum.txt
   iptables -S >> /root/sebelum.txt
   iptables -t nat -S >> /root/sebelum.txt
   cat /proc/sys/net/ipv4/ip_forward >> /root/sebelum.txt
   chmod +x /root/break_nat.sh
   /root/break_nat.sh
   ```
   Kondisi acuan: Gendou hanya punya satu rule NAT `-s 10.93.0.0/21 -o eth0 -j MASQUERADE`; Misato tidak punya rule NAT.
2. Buktikan gejala: Unit-01 `ping -c 2 8.8.8.8` gagal, Unit-01 ke Lilith (`10.93.4.74`) berhasil, Spy `ping -c 2 8.8.8.8` berhasil.
   
3. Diagnosis di `Gendou` dan `Misato`: `ip route`, `iptables -S`, `iptables -t nat -S`.

   Penyebab (dua):

   | Node | Kondisi acuan | Setelah script |
   | :--- | :--- | :--- |
   | Misato | tabel NAT kosong | `-A POSTROUTING -s 10.93.4.64/29 ! -d 10.93.0.0/16 -o eth0 -j SNAT --to-source 172.31.99.1` |
   | Gendou | hanya `MASQUERADE` | tambahan `-A POSTROUTING -s 10.93.4.64/29 -o eth0 -j RETURN` di atas `MASQUERADE` |

   Kenapa gejalanya begitu: Misato menerjemahkan sumber paket Cage menjadi `172.31.99.1` untuk tujuan di luar `10.93.0.0/16`. Di Gendou, sumber itu bukan bagian `10.93.0.0/21`, sehingga rule `FORWARD -s 10.93.0.0/21 -o eth0 -j ACCEPT` tidak cocok dan paket jatuh ke policy `FORWARD DROP`. Rule `RETURN` di Gendou juga akan melewati `MASQUERADE` untuk subnet Cage.

   Kenapa Cage terdampak tapi Intel tidak: kedua rule hanya cocok untuk subnet Cage (`10.93.4.64/29`). Spy di Intel (subnet `10.93.4.100/30`, lewat Kaji) tidak terkena sehingga tetap di-`MASQUERADE` normal. Ping Cage ke Lilith normal karena tujuannya `10.93.0.0/16`, yang dikecualikan oleh `! -d` pada rule SNAT, jadi sumbernya tidak diubah.
4. Perbaiki:
   ```bash
   # Misato
   iptables -t nat -D POSTROUTING -s 10.93.4.64/29 ! -d 10.93.0.0/16 -o eth0 -j SNAT --to-source 172.31.99.1
   # Gendou
   iptables -t nat -D POSTROUTING -s 10.93.4.64/29 -o eth0 -j RETURN
   iptables -t nat -S
   ```
5. Bukti setelah perbaikan:
   ```bash
   # Unit-01
   ping -c 2 8.8.8.8
   # Gendou
   iptables -t nat -nvL POSTROUTING
   ```
   Hasil: ping berhasil, dan counter `MASQUERADE` naik (7 paket pada pengujian).
   

   Alamat sumber diterjemahkan di **Gendou**, satu-satunya router yang terhubung ke NAT1. Misato tidak boleh menerjemahkan alamat.

---

## Soal 11
> Casper dibuat "hantu": tidak ada perangkat lain yang boleh mem-ping Casper (termasuk yang satu switch), tetapi Casper tetap boleh mem-ping siapa saja dan TCP 5000 tetap hidup. Aturan dipasang di Casper sendiri, karena tetangga satu switch tidak lewat router. Yang dibuang hanya `echo-request` (ICMP tipe 8) yang masuk. Balasan ping Casper (`echo-reply`) tidak terkena rule.

1. Buat script di `Magi-Casper`:
   ```bash
   cat > /root/casper-hantu.sh << 'EOF'
   #!/bin/sh
   iptables -C INPUT -p icmp --icmp-type echo-request -j DROP 2>/dev/null || \
   iptables -I INPUT 1 -p icmp --icmp-type echo-request -j DROP
   EOF
   chmod +x /root/casper-hantu.sh
   /root/casper-hantu.sh
   iptables -S INPUT
   ```
2. Buktikan ping ke Casper gagal dan ping dari Casper berhasil:
   ```bash
   # Balthasar dan Lilith
   ping -c 2 10.93.4.58      # gagal, 100% packet loss
   # Casper
   ping -c 2 10.93.4.59      # Balthasar, berhasil
   ping -c 2 10.93.4.74      # Lilith, berhasil
   ```
3. Tunjukkan counter rule dan TCP 5000 tetap hidup:
   ```bash
   # Casper
   iptables -nvL INPUT       # counter rule DROP naik
   cat /root/nc5000.log      # pesan dari Lilith tetap masuk
   ```
  
---

## Soal 12
> Script `break_fw.sh` dijalankan di Casper tanpa dibaca isinya. Gejala: Casper tidak bisa ping `8.8.8.8`, tidak bisa `apt-get update`, dan Unit-00 tidak bisa menyambung ke TCP 5000. Ping ke Casper tetap ditolak (memang benar). Perbaikan tidak boleh membatalkan hardening: policy `INPUT` tetap `DROP` dan semua lalu lintas masuk yang tidak diizinkan tetap ditolak.

1. Catat kondisi sebelum di `Magi-Casper`, lalu jalankan script:
   ```bash
   iptables-save > /root/casper.rules
   iptables -S > /root/sebelum.txt
   iptables -t nat -S >> /root/sebelum.txt
   ip route >> /root/sebelum.txt
   cat /etc/resolv.conf >> /root/sebelum.txt
   chmod +x /root/break_fw.sh
   /root/break_fw.sh
   ```
2. Buktikan gejala: di Casper `ping -c 2 8.8.8.8` dan `apt-get update` gagal (`Temporary failure resolving`), di Unit-00 `nc` ke `10.93.4.58 5000` gagal, ping ke Casper dari Lilith atau Balthasar tetap gagal.
   [screenshot]
3. Diagnosis di Casper: `iptables -S`, `iptables -t nat -S`, `ip route`, `cat /etc/resolv.conf`.

   Penyebab (empat):

   | Item | Sebelum | Setelah script |
   | :--- | :--- | :--- |
   | policy `INPUT` | `ACCEPT` | `DROP` (hardening, dipertahankan) |
   | rule ICMP | `-p icmp --icmp-type 8 -j DROP` | `-p icmp -j DROP` (semua ICMP, termasuk `echo-reply`) |
   | `OUTPUT` | bersih | `-p udp --dport 53 -j DROP` |
   | `ESTABLISHED,RELATED` dan ACCEPT TCP 5000 | tidak ada | tetap tidak ada |

   Kenapa gejalanya begitu:
   - `-p icmp -j DROP` membuang semua ICMP termasuk balasan ping, jadi ping Casper ke `8.8.8.8` terkirim tapi balasannya dibuang.
   - `--dport 53 -j DROP` di `OUTPUT` memblokir DNS, jadi `deb.debian.org` tidak bisa di-resolve.
   - Tanpa rule `ESTABLISHED,RELATED` di bawah `INPUT DROP`, balasan untuk koneksi yang dimulai Casper (DNS, HTTP apt) ikut dibuang walaupun DNS sudah dibuka.
   - Tanpa ACCEPT TCP 5000, Unit-00 ditolak oleh policy `INPUT DROP` walaupun listener hidup.
4. Buat script perbaikan di `Magi-Casper` (policy `INPUT` tetap `DROP`, tanpa `iptables -F`):
   ```bash
   cat > /root/casper-fix.sh << 'EOF'
   #!/bin/sh
   iptables -D INPUT -p icmp -j DROP 2>/dev/null
   iptables -D OUTPUT -p udp --dport 53 -j DROP 2>/dev/null
   iptables -C INPUT -p icmp --icmp-type echo-request -j DROP 2>/dev/null || \
   iptables -I INPUT 2 -p icmp --icmp-type echo-request -j DROP
   iptables -C INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 2>/dev/null || \
   iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
   iptables -C INPUT -p tcp --dport 5000 -j ACCEPT 2>/dev/null || \
   iptables -A INPUT -p tcp --dport 5000 -j ACCEPT
   iptables -P INPUT DROP
   EOF
   chmod +x /root/casper-fix.sh
   /root/casper-fix.sh
   iptables -S
   ```
   Hasil `iptables -S` yang diharapkan:
   ```text
   -P INPUT DROP
   -P FORWARD ACCEPT
   -P OUTPUT ACCEPT
   -A INPUT -i lo -j ACCEPT
   -A INPUT -p icmp -m icmp --icmp-type 8 -j DROP
   -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
   -A INPUT -p tcp -m tcp --dport 5000 -j ACCEPT
   ```
5. Pastikan listener TCP 5000 hidup (script rusak dapat menghentikannya), lalu simpan hasil:
   ```bash
   /root/casper.sh
   netstat -tln | grep 5000
   iptables-save > /root/casper-hardened.rules
   ```
6. Bukti setelah perbaikan:
   ```bash
   # Casper
   ping -c 2 8.8.8.8
   apt-get update            # "Get:" atau "Hit:", tanpa "Err:"
   # Unit-00
   echo "tes dari Unit-00" | nc -w 3 10.93.4.58 5000
   # Casper
   cat /root/nc5000.log      # pesan Unit-00 muncul
   # Lilith atau Balthasar
   ping -c 2 10.93.4.58      # tetap gagal
   ```
  

---
## Soal 13
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 14
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 15
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 16
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 17
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 18
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 19
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step

---

## Soal 20
> Penafsiran soal dan secara ringkas kita disuruh ngapain aja

1. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :
      ```bash
      # Contoh kode perintah
      ini kode
      ```
      
      atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
      ```
      isi script
      ```
2. Untuk [tujuan perintah/skenario], jalankan perintah berikut di `node apa` :

    ```bash
    # Contoh kode perintah
    ini kode
    ```
    
    atau semisal buat script di `node apa` untuk apa ( SCRIPT HARUS DITULIS DI ROOT SUPAYA BISA AKU DEMONSTRASIKAN ULANG! KARENA KALAU NGGAK DI ROOT BAKAL HILANG`
    ```
    isi script
    ```
dst terserah butuh berapa step
