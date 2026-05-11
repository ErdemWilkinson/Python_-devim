[# Python_-devim](https://colab.research.google.com/drive/1fXg3tj9KufPE-Nd-Wirh06ptVI6kQQdP?usp=sharing)
#bu linke ulaşılamazsa eğer:

# PYTHON DÖNEM ÖDEVİ - Müşteri Yönetim Sistemi

import random  # random sayı için
import math
from datetime import datetime

# ===================== 1. KISIM =====================

# değişkenler tanımlandı
ad_soyad = "Ahmet Yılmaz"  # string
aylik_ucret = 550.0  # float
sadakat_ayi = 26  # int
aktif_mi = True  # boolean

# şirketin hizmetleri - liste kullandık
hizmetler = ["İnternet", "Özel TV", "Mobil Ayrıcalık", "Cihaz İndirimi", "Bulut"]

# müşteri bilgilerini sözlükte tuttuk çünkü sözlükte verilere
# ismiyle ulaşabiliyoruz (musteri["ad_soyad"] gibi), listede sadece
# indeksle ulaşılıyor bu da karışıklığa yol açar
musteri = {
    "ad_soyad": ad_soyad,
    "aylik_ucret": aylik_ucret,
    "sadakat_ayi": sadakat_ayi,
    "aktif_mi": aktif_mi
}

# if-else koşulu - VIP kontrolü
if musteri["aylik_ucret"] > 500 or musteri["sadakat_ayi"] > 24:  # iki koşuldan biri yeterliyse
    print("VIP Müşteri: İndirim Tanımla")
else:
    print("Standart Müşteri")

# string işlemleri
buyuk_ad = musteri["ad_soyad"].upper()  # büyük harfe çevirilmiş
rastgele_sayi = random.randint(1000, 9999)
customerID = f"IST-2026-{rastgele_sayi}"  # f-string ile id oluşturulmuş

print(f"Müşteri: {buyuk_ad} | ID: {customerID}")

# ===================== 2. KISIM =====================

# 5 müşteriden oluşan ana liste - liste içinde sözlük kullanıldı
musteriler_listesi = [
    {"ad": "Erdem",   "ucret": 400, "sadakat": 10, "aktif": True},
    {"ad": "Ali",     "ucret": 600, "sadakat": 30, "aktif": False},
    {"ad": "İbrahim", "ucret": 300, "sadakat": 5,  "aktif": True},
    {"ad": "Deniz",   "ucret": 750, "sadakat": 12, "aktif": True},
    {"ad": "Ece",     "ucret": 200, "sadakat": 48, "aktif": False}
]

# %20 KDV ekleyen fonksiyon
def tutar_hesapla(ucret):  # fonksiyon tanımı
    kdvli = ucret * 1.20  # KDV hesaplama
    return kdvli  # değeri döndür

# hizmet listesi - tekrarlı olabilir diye set kullanılmış
alinan_hizmetler = ["İnternet", "TV", "İnternet", "Mobil", "TV", "Bulut"]
benzersiz_hizmetler = set(alinan_hizmetler)  # set ile tekrarları attılmış
print(f"\nBenzersiz Hizmetler: {benzersiz_hizmetler}")

print("\n--- MÜŞTERİ FATURA RAPORU ---")

# for döngüsü ile müşterileri gezdik
for m in musteriler_listesi:  # döngü başlangıcı
    ham_tutar = tutar_hesapla(m["ucret"])  # fonksiyonu çağırdık
    final_fatura = math.ceil(ham_tutar)  # math.ceil ile yukarı yuvarladık

    # churn tespiti - aktif değilse, sadakati 12 aydan azsa veya
    # 250 TL altında ödüyorsa churn riski var diye değerlendirdik
    durum = "Normal"
    if not m["aktif"] or m["sadakat"] < 12 or m["ucret"] < 250:  # churn koşulları
        durum = "CHURN RİSKİ"

    print(f"Müşteri: {m['ad']} | Fatura: {final_fatura} TL | Durum: {durum}")

# datetime ile fatura tarihi
bugun = datetime.now().strftime("%d/%m/%Y %H:%M")  # tarih fortmatlanmış
print(f"\nFatura Tarihi: {bugun}")
