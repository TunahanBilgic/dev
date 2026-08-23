---
layout: post
title: Python “while” Döngüsü
date: 2020-11-18 22:40:00
description: python-kosul-ve-donguler
categories: python-kosul-ve-donguler
tags:  
    - döngü
    - while
    - python
---


Bir önceki [yazımızda](https://www.kodlamaogreniyorum.com/python-for-dongusu/) “for” döngüsünden bahsetmiştik. Bizim belirlediğimiz sayıda tekrarlama yapan döngü, “for” döngüsü; belirli bir koşul sağlandığı sürece, sürekli tekrarlama yapan döngü ise “while” döngüsü olduğunu belirtmiştik. Bu yazımızda “while” döngüsüne giriş yapacağız.

“while” döngüsü için bir koşul tanımlanır. Bu koşulun değeri “True“(Doğru) olduğu sürece döngü sürekli tekrarlanır. Bu nedenle “while” döngüsüne sonsuz döngü de denilir. Döngünün akış diyagramı(üstüne tıklayarak açabilirsiniz):

![](/assets/kod/python/python44.webp)

“while” döngüsünün nasıl kullanıldığına geçelim:

```python
while koşul:
       komutlar
```

```python
a = 1
while a < 6:
    print(a)
    a += 1
```

![](/assets/kod/python/python45.webp)

Yukarıda belirttiğimiz gibi, koşulun değeri “True” olduğu sürece “while” döngüsü aktiftir. İkili(binary) sayı tabanında, “True” değerinin karşılığının 1 olduğunu biliyoruz. “while” teriminin yanına direkt “1” veya “True” yazarak döngüyü aktif edebiliriz:

```python
sayac = 1
while True:
    print(sayac)
    sayac += 1
    if sayac > 5:
        break
```

![](/assets/kod/python/python46.png)


Bir örnek ile konuyu pekiştirelim. [“if” koşul deyimi](https://www.kodlamaogreniyorum.com/python-if-kosul-deyimi/) yazımızda sayı tahmin oyunu yapmıştık. O örnekte kendimiz bir sayı belirliyor, kullanıcıya tek tahmin hakkı sunuyorduk. O örneği, bilgisayarın kendi rastgele sayı belirleyecek ve kullanıcı doğru bilene kadar tahmin etmeye devam edecek şekilde güncelleyelim:

```python
#kodlamaogreniyorum.com, 2020
import random as rd
sayı = rd.randint(1, 9)
while True:
    tahmin = int(input('1-9 Arası Sayı Tahmin Edin: '))
    if tahmin == sayı:
        print("Doğru tahmin ettiniz.\n")
        break
    else:
        print("Yanlış tahmin ettiniz.\n")
```

Sayımızı rastgele oluşturmak için “random” kütüphanesine ihtiyacımız var. “randint(1, 9)” komutu ile “randint()” fonksiyonunun ile 1 ile 9 arasında rastgele bir tam sayı üretmesini sağladık. “while” döngümüzün koşuluna “True” yazarak direkt döngünün aktif olmasını sağladık. Kullanıcının tahminini döngü içine alarak, kullanıcının yanlış bir tahminde bulunması durumunda tekrar tahmin etme şansını vermiş olduk.

![](/assets/kod/python/python47.webp)

![](/assets/kod/python/python48.png)

Bu yazımızda “while” döngüsüne kısa bir giriş yapmış olduk. İlerleyen zamanlarda, “break“, “continue“, “pass” ve “else” terimleri ile ilgili yazımız olacak

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)