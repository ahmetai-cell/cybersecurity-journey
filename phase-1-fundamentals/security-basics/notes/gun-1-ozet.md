# Gün 1 - Özet Notlar
> Tarih: 21 Şubat 2026

---

## OSI 7 Katman
```
1 - Physical      → Kablo, bit, fiziksel
2 - Data Link     → MAC adresi, Switch
3 - Network       → IP adresi, Router
4 - Transport     → TCP/UDP, Port numarası
5 - Session       → Oturum yönetimi
6 - Presentation  → Şifreleme, SSL/TLS
7 - Application   → HTTP, DNS, FTP
```
**Ezber:** Please Do Not Throw Sausage Pizza Away

---

## TCP vs UDP
```
TCP → Güvenli, yavaş (banka, dosya)
UDP → Hızlı, kayıp olabilir (video, DNS)
```

## 3-Way Handshake (TCP)
```
Client → SYN     → Server   "Bağlanabilir miyim?"
Client ← SYN-ACK ← Server   "Evet gel"
Client → ACK     → Server   "Tamam"
→ Bağlantı kuruldu
```

## SYN Flood (DoS Saldırısı)
```
Hacker binlerce SYN gönderir, ACK göndermez
→ Sunucu RAM'i dolar
→ Gerçek kullanıcılar bağlanamaz
→ Layer 4 saldırısı
```

---

## Client-Server vs Peer-to-Peer
```
Client-Server:
✓ Merkezi yönetim, güvenli
✗ Pahalı, server çökerse herkes etkilenir
→ 500+ kullanıcı, büyük şirket

Peer-to-Peer:
✓ Ucuz, kurulumu kolay
✗ Güvenlik zayıf, merkezi yönetim yok
→ 10 altı kullanıcı, küçük ofis
```

---

## DNS
```
→ Alan adını IP'ye çevirir
→ google.com → 142.250.185.14
→ UDP kullanır (hızlı)

Sorun tespiti:
IP ile giriyor ✓ + isimle giremiyor ✗ → DNS arızası
```

---

## DHCP
```
→ Otomatik IP dağıtır
→ Olmasa her cihaza elle IP girilir

169.254.x.x → DHCP alamadı, kendine APIPA atadı
→ İnternet yok
```

---

## Offensive vs Defensive Security
```
Red Team (Offensive):
→ Sisteme saldırır, açık arar
→ Penetration tester, hacker gibi düşünür

Blue Team (Defensive):
→ Sistemi korur, saldırı tespit eder
→ SOC, Firewall, IPS, Log analizi
```

## Blue Team Görevleri
```
1. Kullanıcı eğitimi (phishing farkındalığı)
2. Varlık yönetimi (ağdaki cihazları bil)
3. Güncelleme/yama (eski yazılım = açık)
4. Firewall & IPS kurulumu
5. Log & monitoring (7/24 takip)
```

## SOC (Security Operations Center)
```
→ 7/24 ekranları izleyen ekip
→ Alarm gelince müdahale eder
→ Blue Team'in kalbi
```
