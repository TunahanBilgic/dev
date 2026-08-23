---
layout: post
title: MATLAB Excel’e Veri Aktarma
date: 2020-12-07 21:51:00
description: matlab-veri-islemleri
categories: matlab-veri-islemleri
tags:  
    - veri aktarma 
    - veri oluşturma
    - matlab
---

Bu yazımızda MATLAB’da veri oluşturup, oluşturduğumuz verileri Excel’e aktaracağız. Excel dosyasını yazdığımız kod ile oluşturacağız. Son olarak da MATLAB ile Excel dosyamıza, Excel formülü yazdıracağız. Veri oluşturmak için öncelikle bir senaryo belirleyelim. Senaryomuz ürünler üzerine olsun. Programa rastgele miktarda ürün, ürün stoku ve fiyat oluşturtalım. Ürün miktarları ile fiyatlarını çarpıp, getirilerini hesaplatalım ve Excel dosyasına yazdıralım. Lafı daha fazla uzatmadan kodlamaya geçelim:


```matlab
%kodlamaogreniyorum.com, 2020
clear all
urun_cesidi = randi([4,8]); %ürünler
urun_isimleri = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H'];
urun_stok=[]; %Stoklar
urun_fiyat=[]; %Fiyatlar
for i=1:urun_cesidi %rastgele urun bilgileri
    urun_stok(i) = randi([10,90]);
    urun_fiyat(i) = randi([1, 20]);
end
getiri = urun_stok .* urun_fiyat;
```

“randi([4, 8])” komutu ile 4 ile 8 arasında ürün çeşidi belirlemiş olduk. En fazla 8 tane ürün olabileceği için ürün isimlerini temsilen 8 adet harf tanımladık. Stokları 10 ile 90 arasında ve fiyatları da 1 ile 20 arasında rastgele oluşturduk. Son satırda da getirilerini hesaplamış olduk. Kodun çıktısı:

![](/assets/kod/matlab/matlab63.webp)

```matlab
excel = 'veriler.xlsx'; %excel dosyası
%Excel dosyasını oluşturma 2. yöntem:
%fopen('veriler.xlsx','w'); ->fclose unutulmamalı
%İlk satıra başlıkları yazdıralım.
xlswrite(excel,cellstr('Ürünler'),'Ürünler','A1');
xlswrite(excel,cellstr('Stoklar'),'Ürünler','B1');
xlswrite(excel,cellstr('Birim Fiyat'),'Ürünler','C1');
xlswrite(excel,cellstr('Toplam Getiri'),'Ürünler','D1');
```

“excel = ‘veriler.xlsx’;” komutu ile MATLAB’a “veriler” isminde bir Excel dosyası oluşturmasını söylemiş olduk. “veriler” isminde bir Excel dosyası yoksa oluşturulacaktır ancak aynı isim ve uzantıya sahip bir dosya varsa bilgiler üstüne yazılacaktır. Bu nedenle dosyanın olmadığına dikkat edelim.

“xlswrite()” fonksiyonunun kullanımı: “xlswrite(dosya_adi, yazdirilacak_veriler, calisma_sayfasi, hucreler)” şeklindedir. “Ürünler” isminde bir çalışma sayfası oluşturup, ilk satırlara başlıkları yazdırmış olduk.

```matlab
%Döngü ile hücrelere yazdırma:
for i=1:urun_cesidi
    hucreA=sprintf( 'A%s',num2str(i+1));
    xlswrite(excel,cellstr(sprintf('Ürün_%s',urun_isimleri(i))),'Ürünler',hucreA);  %
    hucreB=sprintf( 'B%s',num2str(i+1));
    xlswrite(excel,cellstr(sprintf('%d',urun_stok(i))),'Ürünler',hucreB);
    hucreC=sprintf( 'C%s',num2str(i+1));
    xlswrite(excel,cellstr(sprintf('%d',urun_fiyat(i))),'Ürünler',hucreC);
end
```

“sprintf()” fonksiyonu sayesinde, döngü ile hücreler arasında gezebiliyoruz. “xlswrite()” fonksiyonu, Excel dosyasında bir hücreye bir karakter/sayı gelecek şekilde yazma yapar. “cellstr()” fonksiyonu sayesinde bir hücreye bütün olarak yazdırma yapabiliyoruz.

```matlab
%Döngüsüz tek komut ile vektörü hücrelere yazdırma:
xlswrite(excel,num2cell(getiri),'Ürünler','D2');     %num2cell()
xlswrite(excel,cellstr('Stok >50 Ürün Sayısı:'),'Ürünler','F1');
formul = sprintf('=EĞERSAY(B2:B%d;">50")',urun_cesidi+1);   %formül örnek 1
xlswrite(excel,cellstr(formul),'Ürünler','F2');
formul2 = sprintf('=TOPLA(B2:B%d)',urun_cesidi+1);               %formül örnek 2
xlswrite(excel,cellstr('Toplam Stok:'),'Ürünler','F3');
xlswrite(excel,cellstr(formul2),'Ürünler','F4');
```

“num2cell()” fonksiyonu, sayısal ifadeyi hücreye çevirmeye yarar. “getiri” isimli satır vektöründe kayıt altında tuttuğumuz sayıları hücre yapısına çevirip, tersçaprazını(transpose) alıyoruz. Böylelikle; döngüye ihtiyaç duymadan, tek bir komut ile tüm verileri hücrelere yazdırabiliyoruz.

“sprintf()” fonksiyonu ile Excel formülünü bir değişkene tanımlayabiliyoruz. Örnek olması açısından, “formul” ve “formul2” isimli  iki değişkene, iki tane formül tanımladık. Programı çalıştıralım ve oluşan Excel dosyamızı inceleyelim:

![](/assets/kod/matlab/matlab64.webp)

“F2” ve “F4” hücrelerinde tanımladığımız formüllerin çalıştığını görüyoruz. Bu hesaplamaları, formül yerine MATLAB’a da yaptırabilirdik ancak örnek olması açısından böyle bir yol izledik. Bunu dışında, tüm verilerimizin istediğimiz gibi Excel dosyasına kayıt edildiğini görüyoruz.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)