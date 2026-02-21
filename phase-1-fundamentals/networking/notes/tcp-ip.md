# TCP/IP Modeli & Protokoller

> Tarih: 2026-02-21

---

## TCP/IP vs OSI

```
OSI (7 katman)          TCP/IP (4 katman)
─────────────────────────────────────────
7 - Application    ┐
6 - Presentation   ├──→  Application
5 - Session        ┘
4 - Transport      ────→  Transport
3 - Network        ────→  Internet
2 - Data Link      ┐
1 - Physical       ├──→  Network Access
```

TCP/IP pratikte kullanılan model, OSI teorik referans.

---

## TCP - 3 Way Handshake

```
Client          Server
  │──── SYN ────→│   "Bağlanabilir miyim?"
  │←── SYN-ACK ──│   "Evet, gel"
  │──── ACK ────→│   "Tamam, başlayalım"
  │                │
  │  [Veri akışı] │
  │                │
  │──── FIN ────→│   "Bitirdim"
  │←─── ACK ─────│
  │←─── FIN ─────│
  │──── ACK ────→│   Bağlantı kapandı
```

---

## Önemli Port Numaraları (Ezberle!)

| Port | Protokol | Açıklama |
|---|---|---|
| 21 | FTP | Dosya transferi (şifresiz) |
| 22 | SSH | Güvenli uzak bağlantı |
| 23 | Telnet | Uzak bağlantı (şifresiz - kullanma!) |
| 25 | SMTP | E-posta gönderme |
| 53 | DNS | Alan adı çözümleme |
| 67/68 | DHCP | IP adresi dağıtımı |
| 80 | HTTP | Web (şifresiz) |
| 110 | POP3 | E-posta alma |
| 143 | IMAP | E-posta alma (gelişmiş) |
| 443 | HTTPS | Web (şifreli) |
| 3389 | RDP | Windows uzak masaüstü |
| 8080 | HTTP-alt | Web proxy / alternatif |

**Güvenlik notu:** 23 (Telnet) ve 21 (FTP) şifresiz - asla production'da kullanma!

---

## IP Adresleme Temelleri

### IPv4
- 32-bit adres: `192.168.1.1`
- 4 octet, her biri 0-255

### Adres Sınıfları
```
A: 1.0.0.0   - 126.255.255.255  (Büyük kurumlar)
B: 128.0.0.0 - 191.255.255.255  (Orta kurumlar)
C: 192.0.0.0 - 223.255.255.255  (Küçük ağlar)
```

### Özel (Private) IP Aralıkları
```
10.0.0.0    - 10.255.255.255   (Sınıf A özel)
172.16.0.0  - 172.31.255.255   (Sınıf B özel)
192.168.0.0 - 192.168.255.255  (Sınıf C özel)
127.0.0.1                      (Loopback - kendi bilgisayarın)
```

---

## Sonraki Konu
→ [Subnetting](subnetting.md)
