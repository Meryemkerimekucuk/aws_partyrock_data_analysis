# Pima Indians Diabetes Dataset - Detaylı Veri Analizi Raporu
### AWS AI & ML Scholars Programı — 2. Proje Çalışması

Bu depo (repository), **AWS AI & ML Scholars** programı kapsamında tamamladığım **2. Proje** ödevine ait analitik çalışmaları içermektedir. Projenin temel amacı; tıp literatüründe kronik hastalıkların ve biyomedikal risk faktörlerinin incelenmesinde önemli bir kaynak kabul edilen *Pima Indians Diabetes* veri kümesini incelemek ve veri madenciliği yöntemleriyle klinik çıkarımlar elde etmektir.

---

## 🚀 Proje Hakkında ve Kullanılan Araçlar
Bu çalışmadaki tüm veri analitiği süreçleri, Amazon Bedrock altyapısı üzerinde çalışan bulut tabanlı üretken yapay zeka ve akıllı asistan modülü **PartyRock Data Analysis** platformu kullanılarak yürütülmüştür. Platformun fonksiyonel yetenekleri vasıtasıyla ham veri kümesinde yer alan 13 farklı analitik katman tek tek taranmış, istatistiksel dağılımlar çıkarılmış ve klinik eşik değer segmentasyonları gerçekleştirilmiştir.

---

## 📊 Analiz Edilen Tablolar ve Klinik Çıkarımlar

### Tablo 1: Genel Veri Seti Yapısı ve Değişken Tanımları
Veri seti, 21 yaş ve üzeri Pima Indian kadınlarına ait 8 bağımsız klinik öznitelik ve diyabet durumunu belirten 1 ikili bağımlı değişkenden (`Outcome`) oluşmaktadır. Tüm verilerin nümerik yapıda olması, PartyRock veri analiz motorunun istatistiksel modellemeleri kayıpsız yapmasını sağlamaktadır.

### Tablo 2: Merkezi Eğilim ve Dağılım İstatistikleri
Ortalama, medyan ve standart sapma değerleri incelenmiştir. Özellikle `Insulin` ve `SkinThickness` değişkenlerindeki yüksek varyans ve sağa çarpıklık, uç değerlerin (outliers) varlığını kanıtlamaktadır. Ayrıca Glikoz, Kan Basıncı ve BMI gibi değişkenlerde tıbben imkansız olan "0" değerleri saptanmıştır.

### Tablo 3: Eksik ve Hatalı Değer Analizi (Sıfır Değerleri Kontrolü)
Yaşayan bir insanda 0 olması imkansız olan klinik değerler "gizli eksik veri (NaN)" olarak tanımlanmıştır. `Insulin` değişkeninde bu oran %48.70, `SkinThickness` değişkeninde ise %29.56 olarak bulunmuştur. İstatistiksel gücü korumak adına bu eksiklikler popülasyon medyanı ile ikame (imputation) edilmiştir.

### Tablo 4: Özniteliklerin Hedef Değişken (Outcome) ile Korelasyonu
Diyabet hastalığının ortaya çıkışında en yüksek doğrusal korelasyona sahip tekil değişkenin **Glucose** ($r = 0.467$) olduğu saptanmıştır. İkinci en güçlü faktör ise obezite göstergesi olan **BMI** ($r = 0.293$) değişkenidir. Tüm anlamlı ilişkiler pozitif yönlüdür.

### Tablo 5: Hamilelik Sayısı (Pregnancies) ve Diyabet Riski Dağılımı
Gebelik sayısı arttıkça kümülatif riskin arttığı görülmüştür. 0-2 kez hamilelik geçirmiş grupta diyabet oranı %21.3 iken, 7 ve daha fazla hamilelik geçiren kadınlarda bu oran %58.7'ye yükselmektedir.

### Tablo 6: Glikoz Seviyesi Aralıklarına Göre Diyabet Dağılımı
Glikoz değeri 100 mg/dL'nin altında olan grupta diyabet oranı %6.1 iken, kritik klinik eşik olan 140 mg/dL aşıldığında risk katlanarak %72.0'ye ulaşmaktadır. Bu, glikozun eşik değer sonrası adımsal/logaritmik bir risk tetiklediğini gösterir.

### Tablo 7: Kan Basıncı (BloodPressure) Sınıflarına Göre Durum
Normal tansiyonlu bireylerde diyabet oranı %30.4 iken, Hipertansiyon Evre 2 ($\ge 90$ mm Hg) hastalarında %53.3'e çıkmaktadır. Bu bulgu, metabolik sendrom ve kardiyovasküler yükün eş zamanlı (komorbidite) seyrini doğrular.

### Tablo 8: Cilt Kalınlığı ve İnsülin Dağıluş Sınıfları
Yüksek insülin segmentine sahip olan bireylerin ortalama cilt kalınlığı 31.4 mm olarak ölçülmüş ve bu gruptaki diyabet oranı %51.6 bulunmuştur. Periferik yağ dokusundaki artışın insülin direncini tetiklediği doğrulanmıştır.

### Tablo 9: Vücut Kitle İndeksi (BMI) Gruplarına Göre Risk
Normal kilolu grupta diyabet oranı %6.8 iken; fazla kilolularda %22.3, Evre 1 obezlerde %36.2 ve BMI değeri 35'in üzerinde olan ileri derece obez grupta %51.9'a çıkmaktadır. Obezite, tip-2 diyabetin en net katalizörüdür.

### Tablo 10: Diyabet Soyağacı Fonksiyonu (DPF) Etki Skoru
Genetik geçiş riski skoru 0.5'in altında olanlarda hastalık oranı %29.8 iken, kalıtım skoru 1.0'in üzerine çıkan yüksek riskli grupta bu oran %54.0'e ulaşmaktadır. Bu, hastalığın güçlü kalıtımsal boyutunu gösterir.

### Tablo 11: Yaş Gruplarına Göre Diyabet Dağılımı
Diyabet riskinin doğrusal sürekli yükselmediği, aksine 31-45 yaş aralığında %52.1 ile zirve yaptığı saptanmıştır. 21-30 yaş grubundaki %21.6'lık oran ise hastalık yaşının aşağı çekildiğinin bir göstergesidir.

### Tablo 12: Hedef Değişken (Outcome) Sınıf Dengesi Tablosu
Toplam 768 kaydın %65.1'i sağlıklı (0), %34.9'u ise diyabet hastalarından (1) oluşmaktadır. Bu 2:1 oranındaki dengesizlik (class imbalance), ileride kurulacak modellerde salt doğruluk yerine F1-skoruna odaklanılması gerektiğini hatırlatır.

### Tablo 13: Veri Ön İşleme Sonrası Öznitelik Değişim Özeti
PartyRock üzerinde veri analizi yapılırken; hatalı sıfırlar popülasyon medyanları ile doldurulmuş, insülin ve cilt kalınlığındaki aşırı uç değerler varyans baskılama yöntemleriyle normalize edilmiş ve Z-score standartlaştırması uygulanmıştır.

---

## ⚖️ Sorumlu Yapay Zeka ve Veri Adaleti (Responsible AI)

AWS AI & ML Scholars programının temel akademik öğretileri doğrultusunda, proje süreçlerinde veri adalet ilkeleri gözetilmiştir:
* **Veri Önyargısı Tespiti (Data Bias):** Tablo 11'de görüldüğü üzere, veri kümesinde genç popülasyon (417 kayıt) ile yaşlı popülasyon (132 kayıt) arasında ciddi bir hacimsel dengesizlik bulunmaktadır.
* **Yaş Önyargısı (Age Bias) Riski:** PartyRock Analyze Data motoru üzerinde çalışırken, bu dengesizliğin analitik çıktıların yanlı kararlar üretmesine yol açabileceği fark edilmiş ve veri analizi süreçlerinde tüm alt grupların eşit temsiliyet hakkı teorik zeminde değerlendirilmiştir.

---

## 🎯 Sonuç
Bu çalışma; bulut bilişim ve üretken yapay zeka tabanlı yenilikçi araçların, veri madenciliği ve hızlı veri keşfi (Exploratory Data Analysis) süreçlerinde ne kadar kararlı, şeffaf ve güvenilir içgörüler üretebileceğini somut verilerle ortaya koymaktadır.

---
**Hazırlayan:** Meryem Küçük  
**Program:** AWS AI & ML Scholars (AWS & Udacity)  
**Proje Tipi:** 2. Proje Ödevi - PartyRock Veri Analizi
