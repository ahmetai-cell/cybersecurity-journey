# Subnetting

> Tarih: 2026-02-21
> Not: Bu konu Network+ ve CCNA'nın en kritik konusu. Zaman harca!

---

## Subnet Mask Nedir?

IP adresinin hangi kısmının ağ, hangi kısmının host olduğunu belirtir.

```
IP:   192.168.1.10
Mask: 255.255.255.0  (/24)

Ağ kısmı:  192.168.1    (değişmez)
Host kısmı:          10 (değişir)
```

---

## CIDR Notasyonu

```
/24 = 255.255.255.0    → 256 adres, 254 kullanılabilir host
/25 = 255.255.255.128  → 128 adres, 126 kullanılabilir host
/26 = 255.255.255.192  →  64 adres,  62 kullanılabilir host
/27 = 255.255.255.224  →  32 adres,  30 kullanılabilir host
/28 = 255.255.255.240  →  16 adres,  14 kullanılabilir host
/29 = 255.255.255.248  →   8 adres,   6 kullanılabilir host
/30 = 255.255.255.252  →   4 adres,   2 kullanılabilir host (point-to-point)
```

**Formül:** Kullanılabilir host = 2^(32-prefix) - 2
(-2: ağ adresi ve broadcast adresi kullanılamaz)

---

## Örnek: 192.168.1.0/24

```
Ağ adresi:      192.168.1.0    (ilk adres - kullanılamaz)
İlk host:       192.168.1.1
...
Son host:       192.168.1.254
Broadcast:      192.168.1.255  (son adres - kullanılamaz)

Toplam:         256 adres
Kullanılabilir: 254 host
```

---

## Örnek: 192.168.1.0/26

```
4 subnet oluşur:
Subnet 1: 192.168.1.0   - 192.168.1.63   (host: .1-.62)
Subnet 2: 192.168.1.64  - 192.168.1.127  (host: .65-.126)
Subnet 3: 192.168.1.128 - 192.168.1.191  (host: .129-.190)
Subnet 4: 192.168.1.192 - 192.168.1.255  (host: .193-.254)
```

---

## Hızlı Hesaplama Tablosu

| CIDR | Mask | Subnet | Hostlar |
|---|---|---|---|
| /24 | 255.255.255.0 | 1 | 254 |
| /25 | 255.255.255.128 | 2 | 126 |
| /26 | 255.255.255.192 | 4 | 62 |
| /27 | 255.255.255.224 | 8 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 32 | 6 |
| /30 | 255.255.255.252 | 64 | 2 |

---

## Pratik Alıştırmalar

**Soru 1:** 10.0.0.0/8 ağında kaç host olabilir?
**Cevap:** 2^24 - 2 = 16,777,214 host

**Soru 2:** 172.16.0.0/16 için broadcast adresi nedir?
**Cevap:** 172.16.255.255

**Soru 3:** 192.168.10.45/28 hangi subnettte?
```
/28 = her subnet 16 adres
45 / 16 = 2 tam, 13 kalan
Subnet: 192.168.10.32 - 192.168.10.47
Network: 192.168.10.32
Broadcast: 192.168.10.47
```

---

## Pratik Araçlar

```bash
# Linux'ta ip komutu
ip addr show
ip route show

# Subnet hesaplama
ipcalc 192.168.1.0/26
```

**Online araç:** ipcalc.net

---

## Sonraki Konu
→ [Protokoller](protocols.md)
