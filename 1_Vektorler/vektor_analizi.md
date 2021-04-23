# Vektör Veriler ile Çalışma 

Bu uygulamada açık veri platformlarından edinilen mekansal veri setleri ile vektör veriler üzerinde temel işlemlerin yapılması amaçlanmıştır.


## Veri Seti
![](./img/01.PNG)
Veri seti olarak [Humanitarian Data Exchange](https://data.humdata.org/) web sayfasında paylaşılan:

- [Türkiye'deki Eğitim Tesisleri (Çokgen geometri tipinde)](https://data.humdata.org/dataset/hotosm_tur_education_facilities)

- [Türkiye'deki Yollar (Çizgi geometri tipinde)](https://data.humdata.org/dataset/roads-in-turkey)
- [Türkiye İdari Sınırlar ve Merkez Noktalar (Çokgen ve nokta geometri tipinde)](https://data.humdata.org/dataset/turkey-administrative-boundaries-levels-0-1-2)

veri setleri kullanılmıştır.


<br>
<br>


## Vektör Verilerin Projeye Aktarılması

'Shapefile (.shp)' dosya formatında indirilen verilerin içeri aktarılması için, açılan projede, üst menüden;

> Katman -> Katman Ekle -> Vektör Katmanı Ekle

yolu izlenerek katman ekleme penceresine ulaşılır.

<br>

![](./img/02.PNG)

<br>

Açılan pencerede, eklenecek '.shp' uzantılı dosyanın konumu gösterilir. 'Ekle' butonuyla projeye eklenir.

<br>

![](./img/03.PNG)

<br>

Okullar, yollar ve ikinci seviye idari sınırlar katmanları projeye eklendikten sonra harita üzerindeki görünümleri şu şekildedir:

<br>

<img src="./img/04.PNG" width="80%">

<br>
<br>

## Projenin Koordinat Referans Sisteminin Ayarlanması

Çalışılacak koordinat sisteminin seçilmesi için;
> Proje -> Özellikler 

sekmesine tıklanır.

<br>

![](./img/05.PNG)

<br>

Açılan pencerede 'CRS' yani 'Koordinat Referans Sistemi' sekmesinden çalışılacak koordinat sistemi seçilir. Bu uygulamada 'TUREF (Türkiye Ulusal Referans Çerçevesi) – 2B Lambert Konform Konik
Projeksiyon Koordinat Sistemi' [EPSG:5637 - TUREF / LCC Europe](https://epsg.io/5637) kullanılmıştır. 

<br>

![](./img/06.PNG)

<br>

![](./img/07.PNG)

<br>
<br>

## Katmanlarda Filtreleme ve Sorgu İşlemleri

Nesnelerin özniteliklerini gözlemleyebilmek için öznitelik tablosunu kullanırız. Bu tabloya ulaşmak için ilgili katmana sağ tıklanır, açılan menüde "Öznitelik Tablosu" butonu tıklanır. 

<br>

![](./img/08.PNG)

<br>

İdari sınırları içeren "tur_polbna_adm2" katmanın öznitelik tablosu açıldığında "İlçe, İl, Ülke" ismi gibi alanların olduğu görülebilir. 

<br>

![](./img/09.PNG)

<br>

Çalışmada "İstanbul'un ilçeleri" kullanılacaktır. Bu sebeple il alanı 'İSTANBUL' olan öznitelikler seçilmelidir. "İfadeye göre seçim" butonu ile sorgu penceresi açılır. 

<br>

![](./img/10.PNG)

<br>

Açılan pencerede il isimlerini içeren "adm1_tr" alanına göre ifade tanımlanmalıdır.

> "adm1_tr" = 'İSTANBUL' 

ifadesiyle ilçeler seçilir.

<br>

![](./img/11.PNG)

<br>

Seçilen varlıkların haritada sarı renk ile gösterildiği görülebilir.

<br>

![](./img/12.PNG)

<br>

Seçilen ilçeleri farklı bir katman olarak kaydetmek için "tur_polbna_adm2" katmanına sağ tıklanır, menüden;
> Dışa Aktar -> Seçili Öznitelikleri Kaydet

yolu ile ilgili pencereye ulaşılır. 

<br>

![](./img/13.PNG)

<br>

Açılan pencerede; dosya formatı, dosya ismi ve kaydedilecek konum, CRS gibi bilgiler seçilir. 'Tamam' butonu ile kaydetme tamamlanır ve projeye eklenir.

<br>

![](./img/14.PNG)

<br>

Diğer katmanların görünürlük tikleri kaldırıldığında, eklenen katmanın harita üzerindeki görünümü şekildeki gibidir. 

<br>

![](./img/15.PNG)

<br>

## CSV Dosyalarının İçe Aktarılması

Türkiye İstatistik Kurumu (TÜİK) web sayfasından 2015 - 2019 yıllarına ait İstanbul ilçe nüfus verileri, "istanbul_ilce_nufus.csv" dosya adıyla kaydedilmiştir. Bu dosyayı içeri aktarmak için üst menüden:
> Katman -> Katman Ekle -> Ayrılmış Metin Katmanı Ekle

yolu izlenerek ilgili pencereye ulaşılır. 

<br>

![](./img/16.PNG)

<br>

".csv" dosya formatı, genellikle virgülle ayrılmış değerlerden oluşur ve yine genellikle ilk satırı sütun isimlerini içerir. Bu sebeple dosya formatı "CSV" seçilmelidir. Eklenecek dosya yalnızca ilçe isimleri ve nüfus bilgisinden oluştuğu için, geometri tanımlama menüsünde “geometri yok” seçeneği işaretlenir ve çalışmaya eklenir.

<br>

![](./img/17.PNG)

<br>
<br>

## Tablo Birleştirme İşlemleri 

Eklenen nüfus verisi katmanı ile ilçeler katmanını birleştirmek için üst menüde yer alan veya 'CTRL+ALT+T' tuş kombinasyonu ile ulaşılabilen “Araçlar” menüsünden “alan değerlerine göre öznitelikleri birleştir” penceresine ulaşılır.

<br>

![](./img/18.PNG)

<br>

Birleştirme işlemi için, ulaşılan pencerede girdi katmanlar ve birleşme referansı olan tablo alanları seçilmelidir. Değerlerin eşleşebilmesi için tabloların aynı formatta (büyük harf, küçük harf, Türkçe karakter vb.) doldurulduğundan emin olunmalıdır. Sonuç katmanının kaydedileceği konum ve isim belirlenir, işlem başlatılır.

<br>

![](./img/19.PNG)

<br>

Aşağıdaki şekilde, işlem tamamlandıktan sonra nüfus bilgilerinin tabloya eklendiği görülebilir.



<br>

![](./img/20.png)

<br>

## Katman Sembolojisi Ayarlama

Katman sembolojisi tablo alanlarına, değerlere bağlı olarak kurallara ve koşullara göre belirlenebilir. Bu çalışmada 2019 yılı nüfus verilerine göre sınıflar oluşturulmuş ve uygun görülen renk paletiyle gösterim yapılmıştır. Katman özelliklerinden “semboloji” sekmesine ulaşılır, “derecelendirilmiş” seçeneği seçilir, sonrasında sınıflandırmanın yapılacağı tablo alanı, renk paleti seçilir. “Sınıflandır” butonuyla işlem tamamlanır. Oluşan sınıfların taban, tavan değerleri uygun şekilde normalize edilir.

<br>

![](./img/21.PNG)

<br>

Katman özelliklerini kullanarak varlıklar üzerinde etiket üretmek de mümkündür. Etiketler bölümünde, etiket üretilecek alan seçilir, ilgili düzenlemeler yapılır ve işlem gerçekleştirilir. Bu çalışmada ilçe isimlerine göre etiket üretilmiştir.

<br>

![](./img/22.PNG)

<br>

İşlemlerin sonucu şekilde gösterilmiştir.

<br>

![](./img/23.PNG)

<br>
<br>

## Nüfus Verisine Göre Sorgular

Örnek olarak 2018 - 2019 yılları arasında nüfusu yüzde 5'in üzerinde artan ilçeler sorgulanmak istenmiştir. İfade şu şekildedir:

> (("2019_pop" - "2018_pop")/( "2018_pop" ) ) * 100 > 5

İfade ve sonuçları şekildeki gibidir. 5 ilçenin yüzde 5'in üzerinde nüfus artışı yaşadığı görülebilir.

<br>

![](./img/24.PNG)

<br>
<br>

## Basılabilir Harita Oluşturma

QGIS ortamında yapılan çalışmayı basılabilir hale getirmek için “Proje” menüsünden “Yeni Baskı Düzeni Oluştur” sekmesi tıklanır.

<br>

![](./img/25.PNG)

<br>

Açılan pencerede “Öge Ekle” menüsünden “Harita Ekle” sekmesi açılır. Haritanın ekleneceği alan seçilerek harita eklenir.

<br>

![](./img/26.PNG)

<br>

“Öge özellikleri” kısmından çalışmaya uygun ölçek belirlenir. Solda bulunan araç çubuğunda bulunan araçlarla ilgili düzenlemeler yapılır.

<br>

![](./img/27.PNG)

<br>

Harita başlığı eklemek için aynı menüden “Etiket Ekle” seçeneği seçilir ve çokgen çizerek istenilen yere yerleştirilir. Öge özellikleri kısmından yazılacak metin ve başlığın konumu, görünüşü belirlenir.

<br>

![](./img/28.PNG)

<br>

Aynı şekilde kuzey oku, lejant ve ölçek ögeleri de haritaya yerleştirilir. Öge özelliklerinden istenilen görünüme ulaşmak adına düzenlemeler yapılabilir. Oluşan ürün aşağıdaki gibidir.

<br>

![](./img/29.PNG)

<br>
<br>

İstenilen formatta (PDF, PNG v.b.) kaydedilerek dışa aktarma işlemi yapılabilir.

<br>
<br>

## Vektör Analiz Araçları

Daha önce projeye eklenen ve görünürlük tiki kaldırılmış ilçe merkezleri ('tur_pntcntr_adm2') katmanı tekrar görünür hale getirilir. İstanbul ilçe idari sınırları için yapılan seçim ve farklı kaydetme işlemi bu katman için de uygulanır. Kaydederken **hedef CRS**, projede kullanılan sistem olan **"TUREF /LCC Europe (EPSG:5637)"** olmalıdır. 

<br>

![](./img/30.PNG)

<br>

Daha sonra "CTRL + ALT + T" tuş kombinasyonuyla ya da araç çubuğunda bulunan **"Dişli"** simgesiyle araç kutusuna ulaşılır. Burada arama çubuğuna "Buffer vectors" yazılarak GDAL kütüphanesinin tampon oluşturma aracı bulunur ve çift tıklayarak araç açılır. İstanbul ilçe merkezleri katmanı, girdi katman olarak seçilir. Oluşturulacak tamponun noktadan uzaklığı 1000 metre olarak girilir. Dosya kaydedilecekse, konumu ve ismi girilir. Geçici dosya olarak da tutulabilir.

<br>

![](./img/31.PNG)

<br>

Sonuç şekildeki gibidir. 

<br>

![](./img/32.PNG)

<br>

Bu katman, ilçe merkezlerine '1 km' uzaklıkta bulunan okulların seçilmesi için kullanılacaktır. Yine araç kutusundan, "Vector Selection" başlığı altındaki "Extract by Location" aracı seçilerek buffer katmanı ile kesişen okullar ayıklanacaktır.

<br>

![](./img/33.PNG)

<br>

Varlıkların ayıklanacağı katman, okulların bulunduğu katman olmalıdır. Karşılaştırma yapılacak katman ise oluşturulan 'buffer' katmanı olarak seçilir. İşlem gerçekleştirilir.

<br>

![](./img/34.PNG)

<br>

Şekilde görüleceği üzere, tamponlar ile kesişen okullar yeni oluşan katmana eklenerek yeşil renkle gösterilmiştir.

<br>

![](./img/35.PNG)

<br>

Bir başka vektör analiz aracı olarak, ağ analiz aracı olan 'En kısa yol' algoritması kullanılabilir. Araç kutusundan "Shortest path (point to point)" aracı seçilir.

<br>

![](./img/36.PNG)

<br>

Yollar katmanı girdi katman olarak seçilir. Başlangıç ve bitiş noktaları, kutucukların yanında bulunan '...' üç nokta butonu ile harita üzerinde işaretlenir. Hesaplama işlemi başlatılır.

<br>

![](./img/37.PNG)

<br>

Örnek olarak, Ankara - Gebze arasındaki en kısa yol hesaplanmıştır.

<br>

![](./img/38.PNG)

<br>

