[# Python_-devim](https://colab.research.google.com/drive/1fXg3tj9KufPE-Nd-Wirh06ptVI6kQQdP?usp=sharing)
[446764_450657.zip](https://github.com/user-attachments/files/27656805/446764_450657.zip)

<img width="806" height="643" alt="image" src="https://github.com/user-attachments/assets/5ed95279-b4cb-4421-a3b2-c9f02a1a7a61" />



📱 Akıllı Müşteri Yönetim ve Analiz Sistemi
Telco (Telekomünikasyon) Senaryosu | Python

Proje Nedir?
Bu proje, bir telekomünikasyon şirketinin müşterilerini Python ile yönetmek ve analiz etmek için yazılmış bir simülasyon sistemidir. Tek bir müşterinin verilerini tanımlamaktan başlayıp birden fazla müşteriyi otomatik olarak işlemeye, fatura hesaplamaya ve ayrılma (churn) riski taşıyan müşterileri tespit etmeye kadar uzanan iki aşamalı bir yapıya sahiptir.

Nasıl Çalışır?
1. Kısım — Tek Müşteri Temsili:
   
İlk aşamada sistemin temel taşları kurulur. Bir müşteriye ait ad, aylık ücret, sadakat süresi ve hesap durumu bilgileri Python değişkenleriyle tanımlanır. Bu bilgiler bir sözlük (dictionary) yapısına aktarılır; böylece her alana musteri["ad_soyad"] gibi anlamlı bir isimle erişilebilir.
Ardından müşteri, aylık ücreti ve sadakat süresi baz alınarak sınıflandırılır:

Aylık ücreti 500 TL'yi geçiyorsa veya 24 aydan fazla süredir müşteriyse → VIP
Bu koşulların hiçbiri sağlanmıyorsa → Standart

Son olarak müşterinin adı büyük harfe çevrilir ve IST-2026-XXXX formatında benzersiz bir müşteri kimliği (customerID) otomatik olarak üretilir.

<img width="611" height="631" alt="image" src="https://github.com/user-attachments/assets/291e13dc-fc4b-4c6a-8a34-21eed33b591e" />



2. Kısım — Çoklu Müşteri Yönetimi ve Analiz:

İkinci aşamada sistem gerçekçi bir boyut kazanır; tek müşteri yerine 5 müşteriden oluşan bir liste üzerinde çalışılır.

Fatura Hesaplama:

Her müşterinin aylık ücreti tutar_hesapla() fonksiyonuna gönderilir. Fonksiyon üzerine %20 KDV ekler ve sonucu geri döndürür. Dönen değer math.ceil() ile yukarı yuvarlanır; böylece faturada hiçbir zaman ondalıklı bir tutar görünmez.

Benzersiz Hizmet Listesi:

Şirkette sunulan hizmetler tekrarlı olarak listeye girilmiş olsa bile set() yapısı bu tekrarları otomatik temizler ve yalnızca benzersiz hizmetleri gösterir.

Churn (Ayrılma Riski) Tespiti,

Döngü her müşteriyi gezerken üç sinyal kontrol edilir:

SinyalAnlamHesap pasifAyrılma süreci başlamış olabilirSadakat < 12 ayBağlılık henüz oluşmamıştırÜcret < 250 TLAz hizmet kullanıyor, vazgeçmesi kolaydır
Bu üç koşuldan herhangi biri sağlandığında müşteri CHURN RİSKİ olarak işaretlenir.

Fatura Tarihi:

Tüm işlemler tamamlandıktan sonra datetime kütüphanesi ile o anın tarihi ve saati otomatik olarak faturanın altına eklenir.

