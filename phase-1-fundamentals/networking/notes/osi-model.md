# OSI Modeli

> Tarih: 2026-02-21
> Durum: Çalışılıyor

---

## OSI Nedir?

Open Systems Interconnection - Ağ iletişimini 7 katmana böler.
Her cihaz ve protokol bu modelin bir katmanında çalışır.
Sorun giderme (troubleshooting) için şart.

---

## 7 Katman (Ezber: "Please Do Not Throw Sausage Pizza Away")

```
7 - Application   (Uygulama)    → HTTP, FTP, DNS, SMTP
6 - Presentation  (Sunum)       → SSL/TLS, şifreleme, sıkıştırma
5 - Session       (Oturum)      → NetBIOS, RPC, oturum yönetimi
4 - Transport     (Taşıma)      → TCP, UDP, port numaraları
3 - Network       (Ağ)          → IP, ICMP, Router
2 - Data Link     (Veri Bağı)   → MAC adresi, Switch, Ethernet, Frame
1 - Physical      (Fiziksel)    → Kablo, bit, Hub, NIC
```

**Aşağıdan yukarıya ezber:** "Please Do Not Throw Sausage Pizza Away"
- **P**hysical
- **D**ata Link
- **N**etwork
- **T**ransport
- **S**ession
- **P**resentation
- **A**pplication

---

## Her Katmanı Detaylı Anla

### Katman 1 - Physical (Fiziksel)
- Ham bit transfer (0 ve 1)
- **Cihazlar:** Hub, kablo, NIC (network kartı), tekrarlayıcı
- **Sorun:** Kablo kopuk mu? NIC çalışıyor mu?

### Katman 2 - Data Link (Veri Bağı)
- Fiziksel adresleme: **MAC adresi** (48-bit, örn: AA:BB:CC:DD:EE:FF)
- **Cihazlar:** Switch, Bridge
- **Veri birimi:** Frame
- ARP burada çalışır (IP → MAC çözümleme)
- **Sorun:** Switch portunu kontrol et, MAC tablosuna bak

### Katman 3 - Network (Ağ)
- Mantıksal adresleme: **IP adresi**
- **Cihazlar:** Router
- **Veri birimi:** Packet
- Routing (yönlendirme) burada olur
- **Protokoller:** IP, ICMP (ping), OSPF, BGP
- **Sorun:** IP yanlış mı? Route var mı? (traceroute)

### Katman 4 - Transport (Taşıma)
- **Port numaraları** burada devreye girer
- **TCP:** Güvenilir, bağlantı tabanlı, 3-way handshake
- **UDP:** Hızlı, güvenilmez, bağlantısız (video stream, DNS)
- **Veri birimi:** Segment (TCP) / Datagram (UDP)
- **Sorun:** Port açık mı? (netstat, nmap)

### Katman 5 - Session (Oturum)
- Oturum başlatma, yönetme, sonlandırma
- **Protokoller:** NetBIOS, RPC, SQL oturumları
- Çok katman 7 ile karıştırılır

### Katman 6 - Presentation (Sunum)
- Veri formatı: şifreleme, sıkıştırma, kodlama
- **Protokoller:** SSL/TLS, JPEG, ASCII, MPEG
- HTTPS burada şifrelenir

### Katman 7 - Application (Uygulama)
- Kullanıcının gördüğü katman
- **Protokoller:** HTTP/HTTPS, FTP, DNS, SMTP, SSH, Telnet
- **Sorun:** Uygulama çalışıyor mu? Doğru port mu?

---

## Güvenlik Açısından OSI

| Katman | Saldırı Türü | Savunma |
|---|---|---|
| 1 - Physical | Fiziksel erişim, kablo dinleme | Fiziksel güvenlik |
| 2 - Data Link | ARP Spoofing, MAC flooding | Port security, DAI |
| 3 - Network | IP Spoofing, Route manipulation | ACL, firewall |
| 4 - Transport | SYN flood, port scanning | Firewall, IPS |
| 5-6 - Session/Presentation | Session hijacking, SSL strip | TLS, sertifika |
| 7 - Application | SQL injection, XSS, phishing | WAF, uygulama güvenliği |

---

## Troubleshooting Yaklaşımı

**Bottom-up (aşağıdan yukarı) → En yaygın yöntem:**
```
1. Kablo/fiziksel bağlantı var mı?
2. Switch portu çalışıyor mu? (LED?)
3. IP/Gateway doğru mu? (ping gateway)
4. Route var mı? (traceroute)
5. Port açık mı? (telnet/nc)
6. Uygulama çalışıyor mu?
```

---

## Pratik Sorular (Kendini Test Et)

1. HTTP hangi katmanda çalışır?
2. Switch hangi katmanda çalışır?
3. Router hangi katmanda çalışır?
4. MAC adresi hangi katmanda kullanılır?
5. TCP ile UDP farkı nedir?
6. ARP nedir ve hangi katmanda çalışır?

> Cevaplar: 1)L7, 2)L2, 3)L3, 4)L2, 5)TCP güvenilir/bağlantılı - UDP hızlı/bağlantısız, 6)IP→MAC çözümleme/L2-L3 arası

---

## Sonraki Konu
→ [TCP/IP Modeli](tcp-ip.md)
