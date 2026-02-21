# Linux Temel Komutlar

> Tarih: 2026-02-21

---

## Dosya/Dizin İşlemleri

```bash
# Neredesin?
pwd

# Dizin listele
ls
ls -la          # gizli dosyalar dahil, detaylı
ls -lh          # boyutları okunabilir göster

# Dizin değiştir
cd /etc
cd ..           # bir üst dizin
cd ~            # home dizinine git
cd -            # önceki dizine dön

# Dosya/dizin oluştur
touch dosya.txt
mkdir klasor
mkdir -p a/b/c  # iç içe oluştur

# Kopyala/Taşı/Sil
cp kaynak hedef
cp -r klasor/ hedef/    # klasörü kopyala
mv eski yeni            # taşı veya yeniden adlandır
rm dosya.txt
rm -rf klasor/          # klasörü sil (dikkatli!)

# İçerik görüntüle
cat dosya.txt
less dosya.txt   # sayfa sayfa (q ile çık)
head -20 dosya   # ilk 20 satır
tail -20 dosya   # son 20 satır
tail -f /var/log/syslog   # canlı log takip
```

---

## Arama

```bash
# Dosya ara
find / -name "passwd"
find /etc -name "*.conf"

# İçerik ara
grep "hata" dosya.txt
grep -r "password" /etc/    # klasörde recursive ara
grep -i "error" log.txt     # büyük/küçük harf duyarsız

# grep + pipe
cat /etc/passwd | grep root
```

---

## Dosya İzinleri

```bash
# İzinleri görüntüle
ls -la
# Örnek: -rwxr-xr-x 1 root root 8192 Jan 1 dosya

# rwxr-xr-x açıklaması:
# - = dosya türü (d=dizin, - =dosya, l=link)
# rwx = sahibi (read, write, execute)
# r-x = grup (read, execute)
# r-x = diğerleri (read, execute)

# İzin değiştir
chmod 755 dosya.sh    # rwxr-xr-x
chmod 644 dosya.txt   # rw-r--r--
chmod +x script.sh    # execute izni ekle

# Sahip değiştir
chown kullanici:grup dosya
chown -R www-data:www-data /var/www/
```

---

## Sistem Bilgisi

```bash
# Kullanıcı bilgisi
whoami
id
who

# Sistem bilgisi
uname -a
hostname
uptime

# Disk/RAM
df -h           # disk kullanımı
free -h         # RAM kullanımı
top             # canlı süreç monitörü
htop            # daha iyi top

# Süreçler
ps aux
ps aux | grep nginx
kill PID
kill -9 PID     # zorla sonlandır
```

---

## Servis Yönetimi

```bash
# Servis durumu
systemctl status nginx
systemctl status ssh

# Başlat/Durdur/Yeniden başlat
systemctl start nginx
systemctl stop nginx
systemctl restart nginx

# Otomatik başlatma
systemctl enable nginx
systemctl disable nginx

# Tüm servisleri listele
systemctl list-units --type=service
```

---

## Log Dosyaları (Önemli!)

```bash
/var/log/syslog        # genel sistem logları
/var/log/auth.log      # kimlik doğrulama (ssh giriş vs)
/var/log/apache2/      # web server logları
/var/log/nginx/        # nginx logları
/var/log/ufw.log       # firewall logları

# Canlı log takip
tail -f /var/log/auth.log

# Başarısız SSH girişleri
grep "Failed" /var/log/auth.log
grep "Invalid user" /var/log/auth.log
```

---

## Sonraki Konu
→ [Ağ Komutları](network-commands.md)
