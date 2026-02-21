# Linux Ağ Komutları

> Tarih: 2026-02-21
> Güvenlik uzmanının en çok kullandığı komutlar

---

## Temel Ağ Komutları

```bash
# Ağ arayüzleri
ip addr show          # IP adreslerini göster
ip addr show eth0     # belirli arayüz
ifconfig              # eski yöntem (hala yaygın)

# Routing tablosu
ip route show
route -n              # eski yöntem

# Bağlantı testi
ping 8.8.8.8          # Google DNS'e ping
ping -c 4 google.com  # 4 paket gönder

# Yol takibi
traceroute google.com
tracepath google.com
```

---

## Port ve Bağlantı Kontrolü

```bash
# Açık portları listele
ss -tulpn             # modern yöntem (ÖNERİLEN)
netstat -tulpn        # eski yöntem

# Açıklama:
# -t = TCP
# -u = UDP
# -l = listening (dinleyen)
# -p = process (hangi program)
# -n = sayısal (ip ve port numarası)

# Belirli porta bak
ss -tulpn | grep 80
ss -tulpn | grep 443

# Uzak porta bağlan/test et
nc -zv 192.168.1.1 22     # port 22 açık mı?
nc -zv 192.168.1.1 1-100  # port tarama
telnet 192.168.1.1 80     # HTTP port testi
```

---

## DNS

```bash
# DNS sorgusu
nslookup google.com
dig google.com
dig google.com A        # A kaydı (IP)
dig google.com MX       # mail sunucusu
dig google.com NS       # name server
dig @8.8.8.8 google.com # belirli DNS sunucusuna sor

# Reverse DNS
nslookup 8.8.8.8
dig -x 8.8.8.8
```

---

## Nmap - Port Tarama (Çok Önemli!)

```bash
# Kurulum
sudo apt install nmap

# Temel tarama
nmap 192.168.1.1              # tek host
nmap 192.168.1.0/24           # tüm subnet
nmap 192.168.1.1-50           # IP aralığı

# Tarama türleri
nmap -sS 192.168.1.1          # SYN scan (stealth, root gerekir)
nmap -sT 192.168.1.1          # TCP connect scan
nmap -sU 192.168.1.1          # UDP scan
nmap -sV 192.168.1.1          # versiyon tespiti
nmap -O  192.168.1.1          # OS tespiti
nmap -A  192.168.1.1          # agresif (hepsini yap)

# Hız ayarı (T1=yavaş/gizli, T5=hızlı/gürültülü)
nmap -T4 192.168.1.0/24

# Port belirt
nmap -p 80,443 192.168.1.1
nmap -p 1-1000 192.168.1.1
nmap -p- 192.168.1.1          # tüm 65535 port

# Çıktıyı kaydet
nmap -oN tarama.txt 192.168.1.1   # normal format
nmap -oX tarama.xml 192.168.1.1   # XML format
```

---

## Wireshark / tcpdump

```bash
# tcpdump - terminal tabanlı paket yakalama
sudo tcpdump -i eth0                    # tüm trafik
sudo tcpdump -i eth0 port 80            # HTTP trafik
sudo tcpdump -i eth0 host 192.168.1.1  # belirli host
sudo tcpdump -i eth0 -w kayit.pcap     # dosyaya kaydet
sudo tcpdump -r kayit.pcap             # dosyadan oku

# Wireshark
# sudo apt install wireshark
# GUI tabanlı, .pcap dosyaları açar
```

---

## Firewall (UFW)

```bash
# UFW durumu
sudo ufw status
sudo ufw status verbose

# Kurallar ekle
sudo ufw allow 22           # SSH izin ver
sudo ufw allow 80/tcp       # HTTP izin ver
sudo ufw deny 23            # Telnet engelle
sudo ufw allow from 192.168.1.0/24 to any port 22  # IP'den SSH

# UFW aç/kapat
sudo ufw enable
sudo ufw disable
```

---

## Pratik Senaryo

```bash
# Bir Linux sunucuya bağlandın, ne yaparsın?

# 1. Ağ durumunu kontrol et
ip addr show
ip route show

# 2. Hangi servisler çalışıyor?
ss -tulpn

# 3. Dışarıya bağlantı var mı?
ss -tnp | grep ESTABLISHED

# 4. Firewall kuralları neler?
sudo iptables -L -n
sudo ufw status

# 5. Son başarısız giriş denemeleri
sudo grep "Failed" /var/log/auth.log | tail -20
```
