# Gün 2 - Defensive Security Detay
> Tarih: 21 Şubat 2026

---

## Threat Intelligence (Tehdit İstihbaratı)

```
Amaç: Saldırganları önceden tanı, hazırlan

Veri toplama:
→ İç kaynaklar: kendi ağ logların
→ Dış kaynaklar: forumlar, haber siteleri

Süreç:
1. Veri topla (collect)
2. İşle/düzenle (process)
3. Analiz et (analyze)
4. Aksiyon al

Sonuç:
→ Saldırganın taktiklerini öğrenirsin (TTPs)
→ Saldırıyı tahmin edersin
→ Önlem alırsın
```

---

## Digital Forensics (Dijital Adli Bilişim)

```
Gerçek hayat: Cinayet soruşturması → parmak izi, DNA
Dijital dünya: Siber saldırı soruşturması → log, dosya, ram

Ne inceler?

1. File System (Dosya Sistemi)
   → Hangi programlar kurulmuş?
   → Silinen dosyalar (kurtarılabilir!)
   → Oluşturulan/değiştirilen dosyalar

2. System Memory (RAM)
   → Saldırgan programı RAM'de çalıştırdı, diske kaydetmedi
   → RAM görüntüsü al, analiz et

3. System Logs (Sistem Logları)
   → Kim ne zaman giriş yaptı?
   → Saldırgan izlerini silse de iz kalır

4. Network Logs (Ağ Logları)
   → Hangi IP'den bağlandı?
   → Ne kadar veri çıktı?
```

---

## Incident Response (Olay Müdahalesi)

```
Incident = Siber saldırı, veri ihlali, kural ihlali

4 Aşama:

1. Preparation (Hazırlık)
   → Ekibi eğit
   → Plan hazırla
   → Saldırı olmadan önce hazır ol

2. Detection & Analysis (Tespit & Analiz)
   → Saldırı var mı? Tespit et
   → Ne kadar ciddi? Analiz et

3. Containment, Eradication & Recovery (Durdur, Temizle, Kurtar)
   → Containment: Yayılmasını durdur
     (virüslü bilgisayarı ağdan kopar)
   → Eradication: Temizle
     (virüsü sil)
   → Recovery: Kurtar
     (sistemi normale döndür)

4. Post-Incident Activity (Sonrası)
   → Rapor yaz
   → Ne öğrendik? Paylaş
   → Bir daha olmaması için önlem al
```

---

## Malware Türleri

```
Malware = Malicious Software = Zararlı Yazılım

1. Virus (Virüs)
   → Programa yapışır, yayılır
   → Dosyaları bozar/siler
   → Bilgisayarı yavaşlatır

2. Trojan Horse (Truva Atı)
   → İyi program gibi görünür
   → İçinde zararlı kod var
   Örnek: "Ücretsiz video player" indir
           → saldırgana tam erişim ver

3. Ransomware (Fidye Yazılımı)
   → Dosyalarını şifreler
   → "Para öde, şifreyi ver" der
   → Hastaneler, şirketler hedef alınır
```

---

## Malware Analizi

```
1. Static Analysis (Statik Analiz)
   → Programı ÇALIŞTIRMADAN incele
   → Assembly dili bilgisi gerekir
   → Güvenli ama zor

2. Dynamic Analysis (Dinamik Analiz)
   → Programı kontrollü ortamda ÇALIŞTIR
   → Ne yapıyor? İzle
   → Hangi dosyalara dokunuyor?
   → Hangi IP'lere bağlanıyor?
   → Sandbox ortamında yapılır (sanal makine)
```

---

## Özet - Defensive Security Tam Tablo

```
SOC          → 7/24 izleme, tehdit tespiti
Threat Intel → Saldırganı önceden tanı
Forensics    → Saldırı sonrası iz sür
IR           → Saldırıya müdahale et (4 aşama)
Malware      → Virüs, Trojan, Ransomware
```
