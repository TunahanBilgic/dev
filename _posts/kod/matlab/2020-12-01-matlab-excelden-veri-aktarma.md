---
layout: post
title: MATLAB Excel’den Veri Aktarma
date: 2020-12-01 20:59:00
description: matlab-veri-islemleri
categories: matlab-veri-islemleri
tags: 
    - matlab grafikler 
    - veri aktarma 
    - veri çekme
    - matlab
---

Bu yazımızda MATLAB’da veri işlemlerine temel bir giriş yapacağız. MATLAB kullanarak Excel’den veri çekip, çektiğimiz verileri grafiğe dökeceğiz. Veri olarak son bir aylık döviz kurlarını kullanacağız. Veri kaynağı olarak [T.C.M.B](https://evds2.tcmb.gov.tr/index.php?/evds/serieMarket/#collapse_2)‘nı kullanacağız. İndirdiğimiz Excel dosyasında Euro alış ve satış ile Dolar alış ve satış verileri olacak. Bununla birlikte dosyanın içinde sayısal olmayan veriler ve hafta sonlarına denk gelen boşluklar olacaktır. Bunları Excel dosyası ile düzenlemek yerine yazacağımız kodla programa düzenleteceğiz. Excel dosyasının **linkini** yazının sonunda bulabilirsiniz. Öncelikle Excel dosyamızı inceleyerek başlayalım:

![](/assets/kod/matlab/matlab57.png)

Gördüğünüz üzere Excel dosyamızın içinde, sütun başlıkları ve açıklamalar gibi sayısal olmayan ifadeler bulunmaktadır. Buna ek olarak, hafta sonlarına gelen günlerin verisi bulunmamaktadır. Verisi olmayan satıları(hafta sonları) da grafiğimize dahil edersek, grafiğimiz kesikli bir görüntü alacaktır. Program içinde yapacağımız birkaç ekleme ile verilerimizi istediğimiz gibi düzenleme imkanına sahip olacağız.  

MATLAB’a, Excel’den veri aktarmak için “xlsread()” fonksiyonunu kullanacağız. MATLAB, “2019a” sürümü itibariyle bu fonksiyonu tavsiye etmiyor. Ancak eski sürümleri kullanan kullanıcıları da göz önünde bulundurarak bu fonksiyon ile programımızı oluşturacağız. Excel dosyasını programımıza aktararak kodlamaya başlayalım:

```matlab
[kurlar, metin, hepsi] = xlsread('kur.xlsx');
```

Aslında, “xlsread()” fonksiyonunun temel kullanımı degisken = xlsread('dosyaadi'); şeklindedir. Ancak bir Excel dosyasında bulunan metin ve sayısal ifadelerin ayrılması isteniyorsa, “xlsread()” fonksiyonunu özel olarak tanımlanması gerekiyor. Yukarıdaki tanımlama ile kur değerleri olan sayısal ifadeleri “kurlar” adlı değişkene, tarih ve açıklamalar gibi olan metinleri de “metin” adlı değişkene kaydetmiş olduk.

![](/assets/kod/matlab/matlab58.png)

“kurlar” değişkenini incelediğimiz zaman, her satır bir günü, sütunlar ise sırasıyla; Dolar alış, Dolar satış, Euro alış ve Euro satışı ifade etmektedir. Öncelikle hafta sonlarına denk gelen, “NaN(Not a Number)” olan ifadeleri eleyelim ve sonrasında kullanım kolaylığı olması açısından döviz kurları ile alış-satış değerlerini farklı değişkenlere kaydedelim:

```matlab
kurlar(~any(~isnan(kurlar), 2),:) = [];
dolar_alis =kurlar(:,1);     %1.sütun $ alış
dolar_satis =kurlar(:,2);   %2.sütun $ satış
euro_alis=kurlar(:,3);       %3.sütun € alış
euro_satis=kurlar(:,4);     %4.sütun € satış
```

1.satırda bulunan kod matristeki “NaN(Not a Number)” olan ifadeleri silmeye yarıyor. “isnan()” fonksiyonu, kendisine girilen veride “NaN” olan ifade varsa “True” değerini döndürür. Başına eklediğimiz “~” değilse operatörü ile saklamak istediğimiz “NaN” ifade olmayan değerler “1“, “NaN” olan ifadeler “0” değerini almış oluyor. “any()” fonksiyonu, kendisine girilen veride  “0” olup olmadığını kontrol etmeye yarar. “any()” fonksiyonu, kendisine girilen veride “0” varsa “0“, diğer değerler için ise “1” değerini üretir. Başına koyduğumuz “~” değilse operatörü ile bu durumu tam tersine çevirmiş oluyoruz. Verimiz matris olduğu için “,2” ifadesini yazmamız gerekiyor. Böylelikle yazmış olduğumuz ~any(~isnan(kurlar), 2) ifadesi matristeki “NaN” olan ifadeleri bulmuş oluyor. Ancak bu ifade tek bir sütun için geçerlidir. Diğer sütunları da dahil etmek için “,:” operatörünü ifadeye ekliyoruz.

Sonuç olarak, kurlar(~any(~isnan(kurlar), 2),:)ifadesi “kurlar” değişkenindeki “NaN” olan ifadeleri bulmaya yarıyor. Bu ifadeleri çıkardıktan sonra döviz isimlerinde değişkenler tanımlayıp, değerlerini atıyoruz. Düzenlediğimiz değerleri grafiğe dökelim:

```matlab
plot(dolar_alis)
hold on
plot(dolar_satis)
plot(euro_alis)
plot(euro_satis)
```

![](/assets/kod/matlab/matlab59.webp)

Herhangi bir düzenleme yapmadan grafiğe döktüğümüz zaman görseldeki gibi bir görüntü ile karşılaşıyoruz. MATLAB’ın oluşturduğu pencere boyutu bana küçük geliyor. Yeniden boyutlandırma yaparken bir konuya dikkat etmemiz gerekiyor. Yazdığımız kod bize özel değilse veya programı başka ekranlarda da kullanıyorsak, ekran boyutlarının farklı olacağını unutmamız gerekiyor. Bunun için vereceğimiz yeni boyut, kullanıcının ekran boyutunun “0.6” katı olacak şekilde ayarlama yapalım. Bununla birlikte oluşturulan figür penceresine isim verme, “Figure 1” yazısını silme ve boyutunu sabitleme gibi özellikler için aşağıdaki kodları ekleyelim:

```matlab
ekran_boyutu=get(0, 'ScreenSize');
ekran_boyutu = ekran_boyutu * 0.6;
fig=figure('Name','Döviz Kuru Grafiği',...
    'outerposition',[0 0 ekran_boyutu(3) ekran_boyutu(4)],...
       'NumberTitle','off','Resize','off','MenuBar','none','ToolBar','figure');
```

![](/assets/kod/matlab/matlab60.webp)


Son olarak; eksen boylarını ayarlama, arka fonda ızgaraları gösterme gibi birkaç minik düzenleme yapalım. Kodumuzun son hali:

```matlab
%kodlamaogreniyorum.com, 2020
[kurlar, metin, hepsi] = xlsread('kur.xlsx');
kurlar(~any(~isnan(kurlar), 2),:) = [];
dolar_alis =kurlar(:,1);     %1.sütun $ alış
dolar_satis =kurlar(:,2);   %2.sütun $ satış
euro_alis=kurlar(:,3);       %3.sütun € alış
euro_satis=kurlar(:,4);     %4.sütun € satış
ekran_boyutu=get(0, 'ScreenSize');
ekran_boyutu = ekran_boyutu * 0.6;
fig=figure('Name','Döviz Kuru Grafiği',...
    'Innerposition',[0 0 ekran_boyutu(3) ekran_boyutu(4)],...
       'NumberTitle','off','Resize','off','MenuBar','none','ToolBar','figure');
plot(dolar_alis,'g')
hold on
plot(dolar_satis,'r')
plot(euro_alis,'b')
plot(euro_satis,'y')
eksen_poz = get(gca,'position');
eksen_poz(1) = eksen_poz(1) *0.5;
eksen_poz(3) = eksen_poz(3) * 1.15;
set(gca,'XTick',[1:length(dolar_alis)],'position',eksen_poz);
ylabel('Türk Lirası');
grid on %Izgara açmak için
x_max = length(dolar_alis); %X ekseni boy
y_min = min(min([dolar_alis dolar_satis euro_alis euro_satis])) - 0.1;
y_max = max(max([dolar_alis dolar_satis euro_alis euro_satis])) + 0.1;
axis ([1 x_max y_min y_max])
```
![](/assets/kod/matlab/matlab61.webp)

![](/assets/kod/matlab/matlab62.webp)

Bu yazımızda MATLAB’da veri işlemlerine temel bir giriş yapmış olduk. MATLAB’a Excel’den veri çekip, bir grafik çizdirdik. Bununla birlikte, grafiğimizde ufak düzenlemeler yaptık. Bu yazının bu kadarıyla yeterli olacağını düşünüyorum.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)