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

Tabel subnetting ada di [file ini](Pembagian%20IP.xlsx)  
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

2. **Verifikasi Antarmuka & IP Address**  
   Jalankan perintah berikut di router untuk memastikan IP terpasang dengan benar:
   ```bash
   ip -br a
   ```

3. **Verifikasi DHCP NAT1 pada Router Gendou**  
   Jalankan di node **Gendou** untuk memastikan antarmuka `eth0` memperoleh IP otomatis:
   ```bash
   ip -br a show eth0
   ```

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

Pengujian konektivitas routing antar-cabang dilakukan langsung dari terminal node **Armisael**:

1. Menampilkan konfigurasi IP antarmuka dan default route pada Armisael:
   ```bash
   ip -br a
   ip route
   ```

2. Menguji ping ke gateway lokal Shigeru:
   ```bash
   ping -c 2 10.93.4.81
   ```

3. Menguji ping ke **Lilith** (Switch-Dogma, cabang Fuyutsuki):
   ```bash
   ping -c 2 10.93.4.74
   ```

4. Menguji ping ke **Sachiel** (Switch-Bunker, cabang Asuka):
   ```bash
   ping -c 2 10.93.3.130
   ```

5. Menguji ping ke **Comm-Net** (Switch-Comm, cabang Hikari):
   ```bash
   ping -c 2 10.93.2.2
   ```


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

   - **Langkah 3 (Kondisi Akhir / Bukti Counter Bertambah):**  
     Jalankan kembali di node **Gendou**:
     ```bash
     iptables -t nat -nvL POSTROUTING
     ```
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
   *Output tcpdump pada Lilith menampilkan `IP 10.93.4.83 > 10.93.4.74: ICMP echo request`, membuktikan bahwa paket tiba dengan source IP asli Armisael (`10.93.4.83`) dan bukan IP router atau IP NAT.*

3. **Pengujian Konektivitas Internet dan Domain (DNS) dari Node Armisael**  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 8.8.8.8
   ping -c 2 deb.debian.org
   ```

4. **Pengujian Konektivitas Internet dan Domain (DNS) dari Node Lilith**  
   Jalankan di node **Lilith**:
   ```bash
   ping -c 2 8.8.8.8
   ping -c 2 deb.debian.org
   ```
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
   *Hasil: Berhasil (2 packets transmitted, 2 received, 0% packet loss).*

4. **Membuktikan Akses Internet dari Jaringan Internal dan Koneksi Balasan Berjalan**  
   *Membuktikan: Rule FORWARD internal ke internet dan koneksi balasan (`ESTABLISHED,RELATED`) bekerja (karena tanpa aturan balasan, reply paket dari 8.8.8.8 akan di-drop oleh policy FORWARD DROP).*  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 8.8.8.8
   ```
   *Hasil: Berhasil (2 packets transmitted, 2 received, 0% packet loss, rtt avg ~20ms).*

5. **Membuktikan Komunikasi Antar-LAN Berhasil**  
   *Membuktikan: Paket antar-subnet `10.93.0.0/21` dapat melintasi router Gendou secara aman.*  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 10.93.4.74
   ```
   *Hasil: Berhasil ping ke Lilith di Switch-Dogma (0% packet loss).*

6. **Membuktikan Jaringan Internal Bisa Mengakses Gendou**  
   *Membuktikan: Paket dari subnet internal menuju IP interface Gendou diizinkan masuk ke chain INPUT.*  
   Jalankan di node **Armisael**:
   ```bash
   ping -c 2 10.93.4.157
   ```
   *Hasil: Berhasil ping ke IP Gendou (0% packet loss).*

7. **Membuktikan Koneksi Baru dari NAT1 Tidak Bisa Masuk**  
   *Penjelasan & Pembuktian: Policy default INPUT dan FORWARD adalah DROP. Pada interface eth0 (arah NAT1), hanya paket berstatus `ESTABLISHED,RELATED` atau DHCP (UDP 68) yang diizinkan. Paket baru (`state NEW`) yang datang dari arah NAT1 tidak memiliki rule kecocokan sehingga otomatis dibuang (DROP) oleh kernel.*

---

## Soal 6
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

## Soal 7
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

## Soal 8
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

## Soal 9
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

## Soal 10
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

## Soal 11
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

## Soal 12
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
