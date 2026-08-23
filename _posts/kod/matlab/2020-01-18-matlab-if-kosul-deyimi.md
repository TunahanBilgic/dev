---
layout: post
title: MATLAB “if” Koşul Deyimi
date: 2020-01-18 06:29:00
description: matlab-kosul-ve-donguler
categories: matlab-kosul-ve-donguler
tags: 
    - if 
    - koşul deyimi 
    - matlab
---

Oluşturduğumuz programlarda bir koşula bağlı olarak gerçekleşmesini istediğimiz durumlar olabilir. Programımızda bir koşula veya kontrole bağlı olarak işlemler gerçekleştirmek istiyorsak, “if” koşul deyimini kullanmamız gerekir.

“if” koşul deyimi, “True” / “False” Boolean mantığı üzerine çalışır.(True = 1, False = 0) “if” ‘in yanına yazılan koşul incelenir. Bu koşulun doğruluğuna göre “True” veya “False” değeri üretilir. Eğer sonuç “True” ise koşul gerçekleşmiş olur ve koşula bağlı olarak gerçekleşecek durumlara izin verilir. “if” koşul deyiminin kullanımı şu şekildedir:

İlk olarak “if” yazıp yanına istediğimiz koşulu, altına( “if” ‘ e göre girintili olacak şekilde ) koşula bağlı gerçekleşecek durumları ve en son olarak da son/bitti anlamına gelen “end” yazıyoruz.

```matlab
if istenilen kosul
   %koşula bağlı gerçekleşecek durum
end
```

Koşul deyiminin kullanımını basit bir sayı tahmin uygulaması ile açıklayalım:

Önceden kendimiz 1 ile 10 arasında bir sayı belirleyelim ve programda tanımlayalım.(x) Kullanıcıdan 1 ile 10 arasında bir sayı girmesini isteyelim(y) ve eğer bizim belirlediğimiz sayıyı girerse, ekrana “Sayıyı bildiniz.” şeklinde yazı yazdıralım. Öncesinde ilişkisel operatörlerden kısaca bahsetmek gerekir. İlişkisel operatörler, iki değeri karşılaştırmamızı sağlar ve karşılaştırma sonucunda “True” veya “False” değer üretir.

| **Operatör** | **MATLAB Fonksiyonu** | **Tanımı**                |
|--------------|-----------------------|--------------------------|
| `==`         | `eq()`               | Eşitse                   |
| `~=`         | `ne()`               | Eşit Değilse             |
| `<`          | `lt()`               | Küçükse                  |
| `<=`         | `le()`               | Küçükse veya Eşitse      |
| `>`          | `gt()`               | Büyükse                  |
| `>=`         | `ge()`               | Büyükse veya Eşitse      |

Daha detaylı bilgi için: [MATLAB Array Comparison with Relational Operators](https://www.mathworks.com/help/matlab/matlab_prog/array-comparison-with-relational-operators.html?s_tid=BB)

> “x == y” veya “eq(x,y)” şeklinde kullanabilirsiniz.

Özetleyecek olursak, kendimizin belirlediği sayı ile kullanıcının girdiği sayı aynıysa (x == y) “True” değeri üretilecek ve ekrana yazı yazdırılacak.  Kodlama kısmına geçelim:

```matlab
x = 5; %Belirlediğimiz Sayı
y = input('1-10 Arası Sayı Tahmin Edin: ');
if x == y
    fprintf('Sayıyı bildiniz.\n');
end
```

![](/assets/kod/matlab/matlab16.png)

Gördüğünüz üzere, koşul sağlandığı zaman  ekranda yazı çıkmakta ancak aksi durumda herhangi bir şey yapılmamaktadır. “if” koşul deyiminin, “False” değerine bağlı olarak gerçekleşmesini istediğimiz durumlar varsa “else” deyimini kullanmamız gerekir. Yukarıdaki örneği; kullanıcının sayıyı bilemediği durumda ekranda, “Sayıyı bilemediniz.”  yazısı çıkacak şekilde güncelleyelim:

```matlab
x = 5; %Belirlediğimiz Sayı
y = input('1-10 Arası Sayı Tahmin Edin: ');
if x == y
    fprintf('Sayıyı bildiniz.\n');
else
    fprintf('Sayıyı bilemediniz.\n');
end
```
![](/assets/kod/matlab/matlab17.png)

Eğer tek bir koşul değil de birden fazla koşul içeren durumlar varsa “elseif” deyimini kullanmamız gerekir. “elseif” deyimini, yukarıdaki örneği güncelleyerek anlatalım:

Kullanıcı, belirlediğimiz sayıdan daha küçük tahminde bulunursa ekranda “Daha büyük tahminde bulunun.”,  daha büyük tahminde bulunursa ekranda “Daha küçük tahminde bulunun.” veya sayıyı bilirse de ekranda “Doğru tahmin ettiniz.” yazısı çıksın. Kodu güncelleyelim:

```matlab
x = 5; %Belirlediğimiz Sayı
y = input('1-10 Arası Sayı Tahmin Edin: ');
if x > y
    fprintf('Daha büyük tahminde bulunun.\n');
elseif x < y
    fprintf('Daha küçük tahminde bulunun.\n');
else
    fprintf('Doğru tahmin ettiniz.\n');
end
```
![](/assets/kod/matlab/matlab18.png)
![](/assets/kod/matlab/matlab19.png)

“if“, “else” ve “elseif” mantığının iyice kavranması için akış diyagramları(üstlerine tıklayarak açabilirsiniz):

<div style="display: flex; justify-content: center; gap: 10px;">
    <img src="{{ site.baseurl }}/assets/kod/matlab/matlab20.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/matlab/matlab21.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/matlab/matlab22.png" alt="If-ElseIf-Else Yapısı">

</div>

Bu yazımızda koşul deyimi konusuna temel bir giriş yapmış olduk. Şimdilik bu kadarının yeterli olduğunu düşünüyorum. İlerleyen zamanlarda, koşul deyiminin farklı kullanımları ve mantıksal operatörler ile ilgili yazımız olacak.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)