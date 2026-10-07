# EMG Aktiflik Tespiti

**Araştırma Sorusu:** 8 kanallı kol EMG verilerinden, kasın aktif olduğu anlar makine öğrenmesi kullanılmadan, basit eşikleme yöntemleriyle tespit edilebilir mi?

**Proje Özeti:**
Kodumuz UCI veri setinden indirdiğimiz klasörün içindeki '01' adlı klasörden '1_raw_data_13-12_22.03.16.txt' dosyasını okuyor. Sütun olarak da time, channel1'den channel8'e 
kadar olan 8 adet sensör kanalı ve class (etiket) sütunlarını kullanıyor.

Baseline F1 skoru, sadece 1. kanalın mutlak değerini alıp belirlediğimiz bir eşik değeriyle karşılaştırarak bulduğumuz tahminlerin, gerçek class etiketleriyle kıyaslanmasıyla 
hesaplanıyor. Eşik değeri ise, verideki sadece dinlenme durumunu ifade eden (class 1) kısımların ortalamasına, standart sapmasının 3 katı eklenerek bulunuyor. Baseline skorumuz, 
'hep aktif' skorumuzdan daha düşük çıktı; bu da 1. kanaldaki bu basit eşikleme yönteminin, sürekli 'kasılma var' tahmininde bulunmaktan bile daha kötü ve yetersiz bir sonuç verdiğini gösteriyor.

Şekil 1, üst üste dizilmiş 9 farklı grafikten oluşuyor. Üstteki 8 grafik, koldan alınan 8 ayrı EMG kanalının (channel1'den channel8'e kadar) saniye cinsinden zamana karşı sinyal değişimlerini gösteriyor. 
En alttaki 9. grafik ise 'class' etiketini, yani o an hangi hareketin yapıldığını (dinlenme veya aktif olma durumunu) zaman çizgisinde gösteriyor. Bu şekil sayesinde kaslardaki sinyal patlamalarının, 
en alttaki etiket kutularıyla aynı anda başlayıp başlamadığını görsel olarak inceleyebiliyoruz.

## Veri Seti
* **Adı:** EMG data for gestures
* **Bağlantı:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/481/emg+data+for+gestures)
* **Not:** Veri seti, kod çalıştığında otomatik olarak UCI sunucularından indirilmektedir. Veri boyutu ve lisans kuralları gereği veri dosyaları bu depoya dahil edilmemiştir.

## Nasıl Çalıştırılır?
1. Bu depoyu (repository) bilgisayarınıza indirin.
2. Depodaki not defterini (`.ipynb` veya `.py`) Google Colab'a yükleyin.
3. Colab üst menüsünden `Çalışma zamanı (Runtime)` -> `Yeniden başlat ve tümünü çalıştır (Restart and run all)` seçeneğine tıklayın.

## Sonuçlar

| Değerlendirme Metriği | F1 Skoru |
| :--- | :--- |
| Baseline (Sadece Kanal 1 Eşikleme) | 0.781 |
| Sürekli Aktif (Kıyaslama Amacıyla) | 0.906 |
| **Geliştirilmiş Yöntem (8 Kanal RMS)** | **1.000** |

## Atıf
Bu projede kullanılan veri seti için orijinal makale atıfı:
Krilova, N., Kastalskiy, I., Kazantsev, V., Makarov, V., & Lobov, S. (2018). EMG Data for Gestures [Dataset]. 
UCI Machine Learning Repository. https://doi.org/10.24432/C5ZP5C.

## Lisans
Bu depodaki analiz kodları **MIT Lisansı** ile açık kaynak olarak paylaşılmıştır.
