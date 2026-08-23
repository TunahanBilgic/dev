---
layout: post
title: "Python “if” Koşul Deyimi"
date: 2020-01-21 11:31:00
description: "python-kosul-ve-donguler"
categories: "python-kosul-ve-donguler"
tags:  
    - "if"
    - "koşul deyimi"
    - "python"
---


Oluşturduğumuz programlarda bir koşula bağlı olarak gerçekleşmesini istediğimiz durumlar olabilir. Programımızda bir koşula veya kontrole bağlı olarak işlemler gerçekleştirmek istiyorsak, “if” koşul deyimini kullanmamız gerekir.

“if” koşul deyimi, “True” / “False” Boolean mantığı üzerine çalışır.(True = 1, False = 0) “if” ‘in yanına yazılan koşul incelenir. Bu koşulun doğruluğuna göre “True” veya “False” değeri üretilir. Eğer sonuç “True” ise koşul gerçekleşmiş olur ve koşula bağlı olarak gerçekleşecek durumlara izin verilir. “if” koşul deyiminin kullanımı şu şekildedir:

İlk olarak “if” yazıp yanına istediğimiz koşulu ve altına( “if” ‘ e göre girintili olacak şekilde ) koşula bağlı gerçekleşecek durumları yazıyoruz.

```python
if "istenilen koşul" :
   koşula bağlı gerçekleşecek durum
```

Koşul deyiminin kullanımını basit bir sayı tahmin uygulaması ile açıklayalım:

Önceden kendimiz 1 ile 10 arasında bir sayı belirleyelim ve programda tanımlayalım.(x) Kullanıcıdan 1 ile 10 arasında bir sayı girmesini isteyelim(y) ve eğer bizim belirlediğimiz sayıyı girerse, ekrana “Sayıyı bildiniz.” şeklinde yazı yazdıralım. Öncesinde ilişkisel operatörlerden kısaca bahsetmek gerekir. İlişkisel operatörler, iki değeri karşılaştırmamızı sağlar ve karşılaştırma sonucunda “True” veya “False” değer üretir.

| **Operatör** | **Tanımı**               |
|--------------|--------------------------|
| `==`         | Eşitse                   |
| `!=`         | Eşit Değilse             |
| `<`          | Küçükse                  |
| `<=`         | Küçükse veya Eşitse      |
| `>`          | Büyükse                  |
| `>=`         | Büyükse veya Eşitse      |

> “<>” Eşit Değilse operatörü Python 3’te geçerli bir operatör değildir.

Özetleyecek olursak, kendimizin belirlediği sayı ile kullanıcının girdiği sayı aynıysa (x == y) “True” değeri üretilecek ve ekrana yazı yazdırılacak.  Kodlama kısmına geçelim:

```python
x = 5  # Belirlediğimiz Sayı
y = int(input("1-10 Arası Sayı Tahmin Edin: "))
if x == y:
    print("Sayıyı bildiniz.\n")
```

![](/assets/kod/python/python28.webp)

Gördüğünüz üzere, koşul sağlandığı zaman  ekranda yazı çıkmakta ancak aksi durumda herhangi bir şey yapılmamaktadır. “if” koşul deyiminin, “False” değerine bağlı olarak gerçekleşmesini istediğimiz durumlar varsa “else” deyimini kullanmamız gerekir. Yukarıdaki örneği; kullanıcının sayıyı bilemediği durumda ekranda, “Sayıyı bilemediniz.”  yazısı çıkacak şekilde güncelleyelim:

```python
x = 5  # Belirlediğimiz Sayı
y = int(input("1-10 Arası Sayı Tahmin Edin: "))
if x == y:
    print("Sayıyı bildiniz.\n")
else:
    print("Sayıyı bilemediniz.\n")
```

![](/assets/kod/python/python29.webp)


Eğer tek bir koşul değil de birden fazla koşul içeren durumlar varsa “elif” (“else if” anlamında) deyimini kullanmamız gerekir. “elif” deyimini, yukarıdaki örneği güncelleyerek anlatalım:

Kullanıcı, belirlediğimiz sayıdan daha küçük tahminde bulunursa ekranda “Daha büyük tahminde bulunun.”,  daha büyük tahminde bulunursa ekranda “Daha küçük tahminde bulunun.” veya sayıyı bilirse de ekranda “Doğru tahmin ettiniz.” yazısı çıksın. Kodu güncelleyelim:

```python
x = 5  # Belirlediğimiz Sayı
y = int(input("1-10 Arası Sayı Tahmin Edin: "))
if x > y:
    print("Daha büyük tahminde bulunun.\n")
elif x < y:
    print("Daha küçük tahminde bulunun.\n")
else:
    print("Doğru tahmin ettiniz.\n")
```

![](/assets/kod/python/python30.png)

![](/assets/kod/python/python31.png)

“if“, “else” ve “elif” mantığının iyice kavranması için akış diyagramları(üstlerine tıklayarak açabilirsiniz):

<div style="display: flex; justify-content: center; gap: 10px;">
    <img src="{{ site.baseurl }}/assets/kod/python/python32.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/python/python33.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/python/python34.png" alt="If-ElseIf-Else Yapısı">
</div>

Bu yazımızda koşul deyimi konusuna temel bir giriş yapmış olduk. Şimdilik bu kadarının yeterli olduğunu düşünüyorum. İlerleyen zamanlarda, koşul deyiminin farklı kullanımları ve mantıksal operatörler ile ilgili yazımız olacak.

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)