---
layout: post
title: MATLAB Switch – Case Yapısı
date: 2020-12-26 18:06:00
description: matlab-kosul-ve-donguler
categories: matlab-kosul-ve-donguler
tags: 
    - case 
    - switch 
    - matlab
---

Bu yazımızda, MATLAB’da bulunan “switch – case” yapısına değineceğiz. Bir değişkenin farklı değerleri için işlem yapılacaksa, “switch – case” yapısı bize bu konuda yardım eder. “switch – case” yapısının temel amacı; “if – elseif” koşul deyimlerinde yazılan uzun koşulların yerine, kısa hatta tek karakter yazımı ile aynı işlevi görmektir. Örneğin; “x” isminde bir değişkenin, “-1“,”0“, “1” ve “2” olmak üzere dört tane alabileceği değer olsun. Biz bu değerlere göre farklı işlemler yaptırmak isteyelim. Bu durumu, “if-elseif” kullanarak yazalım:

```matlab
if x == -1
    %işlemler
elseif x == 0
    %işlemler
elseif x == 1
    %işlemler
else %veya "elseif x == 2"
    %işlemler
end
```


Aynı durumu “switch – case” yapısı ile yazalım:

```matlab
%syntax:
switch degisken
    case deger 1
        %işlemler
    case deger n
        %işlemler
    otherwise
        %işlemler
end
```
```matlab
switch x
    case -1
        %işlemler
    case 0
        %işlemler
    case 1
        %işlemler
    otherwise %veya "case 2"
        %işlemler
end
```

Eğer “-1” ile “0” değerlerinde aynı işlemleri, diğer değerlerinde de farklı işlemler yaptırmak istersek: 

```matlab
if x == -1 || x == 0
        %işlemler
elseif x == 1
        %işlemler
else %veya x == 2
        %işlemler
end
```
```matlab
switch x
    case {-1, 0}
        %işlemler
    case 1
        %işlemler
    otherwise %veya "case 2"
        %işlemler
end
```

Gördüğünüz üzere; “switch – case” yapısı bir değişkenin farklı değerleri için farklı işlemler yapılacaksa, bize kolaylık sağlar. Bir başka örnek ile konuyu pekiştirelim. Kullanıcının seçmiş olduğu bir ayın kaç günden oluştuğunu bildiren bir program oluşturalım. Kullanıcı açılan bir pencere yoluyla isteği ayı seçsin. Sonucu yine açılan bir pencere ile kullanıcıya bildirelim. Kullanıcı hatalı bir giriş yaparsa, ekrana hata bildiren bir pencere oluşturalım. “if-elseif” koşul deyimi ile “switch-case” yapısı arasındaki farkı anlamak için, kodumuzu iki türlü de yazalım: 

```matlab
%kodlamaogreniyorum.com, 2020
clear all
clc
ay = inputdlg('Ay numarası: ','Giriş');
if ay{1} == "2"
        msgbox('Girdiğiniz ay 28 günden oluşur.');
elseif ay{1} == "1" || ay{1} == "3" || ay{1} == "5" || ay{1} == "7" ...
      || ay{1} == "8" || ay{1} == "10" || ay{1} == "12"
        msgbox('Girdiğiniz ay 31 günden oluşur.');
elseif ay{1} == "4" || ay{1} == "6" || ay{1} == "9" || ay{1} == "11"
        msgbox('Girdiğiniz ay 30 günden oluşur.');
else
        warndlg('Hatalı giriş yaptınız.','HATA');
end
```
```matlab
%kodlamaogreniyorum.com, 2020
clear all
clc
ay = inputdlg('Ay numarası: ','Giriş');
switch ay{1}
    case '2'
        msgbox('Girdiğiniz ay 28 günden oluşur.');
    case {'1','3','5','7','8','10','12'}
        msgbox('Girdiğiniz ay 31 günden oluşur.');
    case {'4','6','9','11'}
        msgbox('Girdiğiniz ay 30 günden oluşur.');
    otherwise
        warndlg('Hatalı giriş yaptınız.','HATA');
end
```

![](/assets/kod/matlab/matlab35.PNG)

“switch – case – otherwise” mantığının iyice kavranması için akış diyagramları:

<div style="display: flex; justify-content: center; gap: 10px;">
    <img src="{{ site.baseurl }}/assets/kod/matlab/matlab36.webp" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/matlab/matlab37.webp" alt="If-ElseIf-Else Yapısı">
</div>

Bu yazımızda “switch – case” yapısına değinmiş olduk. Bir sonraki yazımızda, “switch – case” yapısını kullanarak hesap makinesi programı oluşturacağız.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)