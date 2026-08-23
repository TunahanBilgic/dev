---
layout: post
title: MATLAB Gantt Grafiği Oluşturma
date: 2020-12-06 10:58:00
description: matlab-ornek-uygulamalar
categories: matlab-ornek-uygulamalar
tags:  
    - matlab grafikler
    - matlab veri aktarma
    - matlab
---

Bu yazımızda MATLAB kullanarak bir Gantt grafiği oluşturacağız. Gantt grafiği; planlama, proje yönetimi gibi alanlarda sürecin nasıl gittiği hakkında bilgi sahibi olmamızda yardımcı olan bir grafiktir. Gantt grafiği, verileri görselleştirerek daha anlaşılır hale getirmektedir. Biz bu uygulamada bir proje yönetim sürecini ele alacağız. Verilerimiz, proje yönetim süreçlerinin planlanan ve gerçekleşen zamanları olacak. Ayrıca Excel dosyasındaki metinleri de grafik üzerinde isimlendirmede kullanacağız. Verilerimiz bir Excel dosyasında kayıt halinde olacak. [MATLAB’a Excel’den veri aktarma](https://www.kodlamaogreniyorum.com/matlab-excelden-veri-aktarma/) yazımızı inceleyerek, veri aktarımı hakkında detaylı bilgiye sahip olabilirsiniz.

Öncelikle, Excel dosyasını inceleyelim:

![](/assets/kod/matlab/matlab71.png)

Excel dosyasında bulunan sayılar hafta cinsinden zamanları ifade ediyor. Bununla birlikte, toplamda altı tane olan proje yönetim süreçlerinin isimleri de veri dosyamızın içerisinde yer alıyor. Gantt grafiğini oluşturma mantığımız: “Fikir Belirleme süreci üç hafta sürmüş, ardından üç hafta boyunca da Fikir Analizi süreci yer almış” şeklinde olacak. Kısacası zamanları üst üste ekleyerek grafiği oluşturacağız. Excel dosyasını, kullanıcının kendisinin seçeceği şekilde programımızı kodlamaya başlayalım:

```matlab
excel=uigetfile('*xls*');
assignin('base','excel',excel);
[veri,metin,hepsi] = xlsread(excel);
```
![](/assets/kod/matlab/matlab72.webp)

“uigetfile()” fonksiyonu kullanıcının dosya seçmesi için bir pencere açar. Yazdığımız “*xls*” uzantısı sayesinde, kullanıcının Excel dosyalarını görmesinde kolaylık sağlıyoruz. “assignin()” fonksiyonu ile Excel dosyamızın “excel” isimli değişkende çalışma alanına kaydedilmesini sağlıyoruz. “xlsread()” fonksiyonu Excel dosyasındaki metinleri hücre olarak değişkene tanımlıyor. Bununla birlikte, Excel dosyasındaki sayısal ifadelerin olduğu yerleri de hücre olarak değişkene tanımlıyor. Metinleri kullanırken zorlanmamak için aşağıdaki kodları ekleyelim:

```matlab
[satir,sutun] = size(metin);
proje_asama=[]; %proje aşamaları için
sure_tipi=[];
for i=1:satir %proje aşamalarını kaydetme
    if strlength(metin{i,1}) > 0
        proje_asama=[proje_asama; string(metin{i,1})];
    end
end
for i =1:sutun
    if strlength(metin{1,i}) > 0
        sure_tipi = [sure_tipi string(metin{1,i})];
    end
end
```

Grafiğin boyut, isim gibi temel ayarlarını yapalım:

```matlab
ekran_boyutu=get(0, 'ScreenSize');
ekran_boyutu = ekran_boyutu * 0.8;
fig=figure('Name','Proje Gantt Grafiği',...
    'Innerposition',[0 0 ekran_boyutu(3) ekran_boyutu(4)],...
       'NumberTitle','off','Resize','off','MenuBar','none','ToolBar','figure');
```

Gantt grafiğindeki barların uzunluğu süreyi ifade etmekte ve X ekseni ile ilişkilidir. Barların kalınlığı ise Y ekseni ile ilişkilidir. Barların kalınlığını biz belirliyoruz. Ayrıca Y ekseni, proje yönetim aşamalarını temsil etmektedir.

Planlanan ve gerçekleşen zamanlar farklı olduğundan ve dolayısıyla farklı koordinatlarda olacağı için ayrı ayrı değişkenlere tanımlama yapmamız gerekiyor:

```matlab
bar = 20;    %bar kalınlık
x_p = 0;      %başlangıç konumları
x_g = 0;
y_p = ekran_boyutu(4) - bar;
y_g = y_p - bar * 2;
```

Gantt grafiğinin barlarını “rectangle()” fonksiyonu ile oluşturacağız. “rectangle()” fonksiyonu, kendisine girilen koordinat ve kenar boyutları bilgisine göre dikdörtgen oluşturmaktadır. Grafiğin barını oluşturduktan sonra, “text()” fonksiyonu ile bara, “planlanan” veya “gerçekleşen” yazacağız. Böylelikle zaman ayrımını daha kolay hale getirmiş olacağız. Gerekli kodları ekleyelim:

```matlab
rectangle('Position',[x_p y_p veri(1,1) bar],'Facecolor','g')
hold on
rectangle('Position',[x_g y_g veri(1,2) bar],'Facecolor','r')
y_lab{1} = proje_asama(1);
text(x_p+veri(1,1)/2,y_p+bar/2,sprintf('%s',sure_tipi(1)),'HorizontalAlignment','center','FontSize',8)
text(x_g+veri(1,2)/2,y_g+bar/2,sprintf('%s',sure_tipi(2)),'HorizontalAlignment','center','FontSize',8)
```

Bu aşamaya kadar; kullanıcının verileri seçmesini sağladık, grafiğin ayarlarını yaptık ve proje yönetiminin ilk sürecini grafiğe döktük. 

![](/assets/kod/matlab/matlab73.webp)

Diğer süreçleri döngü ile grafiğe dökeceğiz. X ve Y eksenindeki gerekli hesaplamaları da dahil ederek kodlamaya devam edelim:

```matlab
for i=2:length(veri)
    y_p = y_g - bar*2;
    y_g = y_p - bar * 2;
    x_p = x_p + veri(i-1,1);
    x_g = x_g + veri(i-1,2);
    %planlanan değerler
    rectangle('Position',[x_p y_p veri(i,1) bar],'Facecolor','g')
    %gerçekleşen değerler
    rectangle('Position',[x_g y_g veri(i,2) bar],'Facecolor','r')
    y_lab{i} = proje_asama(i);
    plot([x_g x_g],[y_g+bar y_g+bar*4],'--','Color','b')
    text(x_p+veri(i,1)/2,y_p+bar/2,sprintf('%s',sure_tipi(1)),'HorizontalAlignment','center','FontSize',8)
    text(x_g+veri(i,2)/2,y_g+bar/2,sprintf('%s',sure_tipi(2)),'HorizontalAlignment','center','FontSize',8)
end
```

Artık son aşamaya geldik. Grafiğin; Y eksenine proje aşamalarını, X eksenine ise haftaları yazdıracağız. Bununla birlikte, grafiğe bir başlık ve renklerin neyi ifade ettiğini anlatan bir bilgi kutusu ekleyelim:

```matlab
set(gca,'XTick',[0:max(sum(veri))],'YTick',[y_g+bar+bar/2:bar*4:ekran_boyutu(4) - bar]);
xlabel('Haftalar','FontSize',14,'FontWeight','bold','Color','r')
set(gca,'YTickLabel',flip(y_lab),'Fontsize',12);
ylabel('Aşamalar','FontSize',14,'FontWeight','bold','Color','r')
set(gca, 'YGrid', 'off', 'XGrid', 'on')
planlanan = line(NaN,NaN,'LineWidth',4,'Color','g');
gerceklesen = line(NaN,NaN,'LineWidth',4,'Color','r');
legend([planlanan gerceklesen],sure_tipi(1),sure_tipi(2))
title([num2str(max(sum(veri))),' Haftalık Proje Süreci'],'Color','b','FontAngle','italic')
```

Programımızın son hali:

![](/assets/kod/matlab/matlab74.webp)

Bir başka veri dosyası ile programımızı çalıştıralım:

![](/assets/kod/matlab/matlab75.png)

![](/assets/kod/matlab/matlab76.png)

Bir yazının daha sonuna geldik. Yeni içerikler için sitemizi takip etmeyi unutmayın.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)