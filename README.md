MAKİNE ÖĞRENMESİ İLE MAAŞ TAHMİN MODELİ

# İş Problemi

Maaş bilgileri ve 1986 yılına ait kariyer istatistikleri paylaşılan beyzbol oyuncularının maaş tahminleri için bir makine öğrenmesi projesi gerçekleştirilmesidir

# Veri seti hikayesi

# Bu veri seti orijinal olarak Carnegie Mellon Üniversitesi'nde bulunan StatLib kütüphanesinden alınmıştır.
# Veri seti 1988 ASA Grafik Bölümü Poster Oturumu'nda kullanılan verilerin bir parçasıdır.
# Maaş verileri orijinal olarak Sports Illustrated, 20 Nisan 1987'den alınmıştır.
# 1986 ve kariyer istatistikleri, Collier Books, Macmillan Publishing Company, New York tarafından yayınlanan1987 Beyzbol Ansiklopedisi Güncellemesinden elde edilmiştir.

Değişkenler:

# AtBat: 1986-1987 sezonunda bir beyzbol sopası ile topa yapılan vuruş sayısı
# Hits: 1986-1987 sezonundaki isabet sayısı
# HmRun: 1986-1987 sezonundaki en değerli vuruş sayısı
# Runs: 1986-1987 sezonunda takımına kazandırdığı sayı
# RBI: Bir vurucunun vuruş yaptıgında koşu yaptırdığı oyuncu sayısı
# Walks: Karşı oyuncuya yaptırılan hata sayısı
# Years: Oyuncunun major liginde oynama süresi (sene)
# CAtBat: Oyuncunun kariyeri boyunca topa vurma sayısı
# CHits: Oyuncunun kariyeri boyunca yaptığı isabetli vuruş sayısı
# CHmRun: Oyucunun kariyeri boyunca yaptığı en değerli sayısı
# CRuns: Oyuncunun kariyeri boyunca takımına kazandırdığı sayı
# CRBI: Oyuncunun kariyeri boyunca koşu yaptırdırdığı oyuncu sayısı
# CWalks: Oyuncun kariyeri boyunca karşı oyuncuya yaptırdığı hata sayısı
# League: Oyuncunun sezon sonuna kadar oynadığı ligi gösteren A ve N seviyelerine sahip bir faktör
# Division: 1986 sonunda oyuncunun oynadığı pozisyonu gösteren E ve W seviyelerine sahip bir faktör
# PutOuts: Oyun icinde takım arkadaşınla yardımlaşma
# Assits: 1986-1987 sezonunda oyuncunun yaptığı asist sayısı
# Errors: 1986-1987 sezonundaki oyuncunun hata sayısı
# Salary: Oyuncunun 1986-1987 sezonunda aldığı maaş(bin uzerinden)
# NewLeague: 1987 sezonunun başında oyuncunun ligini gösteren A ve N seviyelerine sahip bir faktör

* Veri setinde 20 değişken ve 322 gözlem sayısı bulunmaktadır.Değişkenlerin 17 tanesi nümerik , 3 tanesi kategorik değişkendir.
*grab_col_names fonksiyonu ile nümerik ,kategorik , nümerik görünümlü kategorik ve kategorik görünümlü kardinal olan değişkenlerin seçimi gerçekleştirildi.
veri setinde nümerik görünümlü kategorik ya da kategorik görünümlü kardinal değişkenin bulunmadığı görüldü.

*Threshold değerleri 0,25 ve 0,75 seçilerek aykırı değer analizi yapıldı ve AtBat ve Hits değişkenleri hariç hepsinde aykırı değerlerin olduğu görüldü.
low_limit altındaki aykırı değerler low_limit ile ve up_limit üstündeki aykırı değerler de up_limit ile değiştirilerek aykırı değer problemi çözümüne gidildi.

*Salary hedef değişkeninde 59 adet eksik değer olduğu görüldü.BU veri setinin yaklaşık %18 'ine denk gelmekedir.Bu gözlemler veri setinden çıkarılmıştır.
*Veri setinde birbiri ile ilişkili değişkenlerden yeni değişkenler türetilmiş ve çeşitlilik arttırılarak değişken sayısı 39'a çıkarılmıştır.

*kategorik değişkenlere one hot encoding işlemi uygulanarak bool tipine dönüşmüş yeni değişkenler ile  modelin kullanımına uygun hale getirilmiştir.

*nümerik değişkenlerin değerleri nedeniyle modelde birbiri üzerinde üstünlük sağlamasını ve modeli yanıltmasını engellemek amacıyla standart scaler yöntemi kullanılarak hedef değişken olan Salary hariç tüm sayısal değişkenler ölçeklendirilmiştir.

*Tüm modelleri deneyecek bir fonksiyon oluşturulmuş ve sonucunda random forest ve gradient boosting regressor modellerinin RMSE değerlerinin en düşük oluğu görülmüştür.
RMSE: 206.8681 (RF) 
RMSE: 199.0634 (GBM) 

*GridSearchCV metodu ile en uygun olacak parametreler seçildikten sonra hiperparametre optimizasyonu gerçekleştirilmiştir.
Hiperparametre sonucunda RMSE değerleri aşağıdaki şekilde görülmektedir.
RMSE: 199.6796 (GBM) 
RMSE (After): 204.4606 (GBM) 

RMSE: 203.8387 (RF)
RMSE (After): 204.4929 (RF) 




