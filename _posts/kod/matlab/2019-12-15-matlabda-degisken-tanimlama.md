---
title: MATLAB’da Değişken Tanımlama
date: 2019-12-15 11:31:00
description: Matlab Temel Bilgiler
categories: matlab-temel-bilgiler
tags: 
    - değişken tanımlama 
    - fprintf 
    - disp
    - swap
    - matlab
    - variable
---

Bir program oluştururken bazı bilgileri saklamak, üzerlerinde işlem yapmak ve bu bilgileri güncellemek ihtiyacı duyarız. Bunun için, değişken(variable) kullanmamız gerekir. Kısacası değişkenler, bizim isimlendirdiğimiz ve bilgisayarda geçici süreyle saklı kalan tanımlamalardır. Bir değişken tanımlama:

```matlab
%DEĞİŞKEN İSMİ = ATANAN DEĞER
```
şeklinde yapılır. Örnek olarak, “yil” isimli bir değişken tanımlayalım ve ona “2019” değerini atayalım. Sonrasında, “disp()” komutu ile ekrana yazdıralım.

```matlab
yil = 2019;
disp(yil);
```
![](/assets/kod/matlab/matlab6.png)

> Değişken isimleri; boşluk, önce sayı sonra harf(6x), özel ifade olmayacak ve Türkçe karakter içermeyecek şekilde belirlenmelidir. Aşağıdaki atamaları yapmayı denerseniz bir hata uyarısı ile karşılaşacaksınız.
```matlab
6x = 15; %önce sayı olmamalı
end = 21; %özel ifade olmamalı
yıl = 2019; %Türkçe karakter olmamalı
bu yil = 2019; %Boşluk olmamalı
```
<h1>Değişkenler Aracılığı ile Ekrana Bilgi Yazdıralım!</h1>
Sözel bir ifadeyi değişkene atamak istiyorsak tek tırnak(‘ ‘) içinde yazmamız gerekir. Örnek olarak; “ulke” isimli bir değişken oluşturup, “Türkiye” ifadesini atayalım. Sonrasında, “disp()” komutu ile ekrana yazdıralım. “disp()” komutunun içine çift tırnak kullanmadan değişkenin ismini yazarsak, yazdığımız değişkenin değerini ekrana yazdırır.  
```matlab
ulke = 'Türkiye';
disp(ulke);
```
![](/assets/kod/matlab/matlab7.png)
Birinci yazımızda “disp()” ve “fprintf()” komutlarından bahsetmiştik. Eğer ekrana bir sözel ifade ile bir sayısal değer yazdırılmak istenirse bu iki komut arasında farklılıklar bulunmaktadır. Bunu bir örnek ile açıklayalım. Ekrana, “Bugün günlerden pazar. Hava 15 derece ve saat 10.35 .” yazısını yazdıralım. “pazar”, “15” ve “10.35” bilgileri; “gun”, “hava” ve “saat” isimli değişkenlerden gelsin. 
```matlab
gun = 'pazar';
hava = 15;
saat = 10.35;
disp(['Bugün günlerden ' gun '. Hava ' num2str(hava) ' derece ve saat ' num2str(saat) '.']);
fprintf('Bugün günlerden %s. Hava %d derece ve saat %g.\n',gun,hava,saat);
```
![](/assets/kod/matlab/matlab8.webp)

Görüldüğü üzere “disp()” komutunda, değişkenlerden gelen bir sayısal değer ile sözel bir ifadeyi birlikte yazdırırken “num2str()” komutunu kullanmamız gerekiyor. “num2str()” komutu, sayısal bir değeri karakter dizisine çevirmeye yarar. Böyle durumlarda “disp()” komutu, “fprintf()” komutuna göre daha uzun yazım gerektirmektedir.

“fprintf()” komutunu inceleyecek olursak, “%” ile başlayan ifadeler dikkat çekmektedir. Tıpkı kaçış operatörü(“\“) gibi, “%” operatörü de “fprintf()” komutu için özel anlam taşımaktadır. “%” ifadesinin yanında yer alan karaktere göre “fprintf()” ekrana bilgi yazdırmaktadır. Bu bilgiler değişkenlerden gelmektedir. Bilgi sağlayan değişkenler ise çift tırnağın dışında, sırasıyla ve birbirlerinden virgülle ayrılarak yazılır.
```matlab
%c : Değişkeni tek bir karakter olarak yazdırma.
%s : Değişkeni karakter dizisi olarak yazdırma.
%d : Değişkeni tam sayı olarak yazdırma.
%f : Değişkeni ondalıklı sayı olarak yazdırma.
%g : Değişkeni en uygun formda yazdırma. (Tam sayı, ondalıklı sayı)
```
![](/assets/kod/matlab/matlab9.png)
> Eğer sizde sayılarda daha fazla veya daha az sıfır varsa “format” ayarlarını gözden geçirin.

> İki değişkenin değerlerini, birbirleriyle değiştirmek istiyorsanız “deal()” komutunu kullanabilirsiniz. Örnek kullanım: [a,b] = deal(b,a)
Tanımladığımız bir değişkeni silmek istiyorsak “clear” komutunu kullanırız.
![](/assets/kod/matlab/matlab10.png)

```matlab
clc        %Komut penceresini temizler.
clf        %Mevcut şekil(figure) ekranını temizler. İlerleyen konularda göreceğiz.
clear x    %X değişkenini siler.
clear all  %Bütün değişkenleri siler.
who        %Mevcut değişkenleri gösterir.
what       %MATLAB'ın çalıştığı klasördeki MATLAB dosyalarını gösterir.
dir        %MATLAB'ın çalıştığı klasördeki bütün dosyaları gösterir.
```

Bir sonraki yazımız [*“MATLAB Komut Dosyaları”*](https://www.kodlamaogreniyorum.com/matlab-script-files/) hakkında olacak.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)