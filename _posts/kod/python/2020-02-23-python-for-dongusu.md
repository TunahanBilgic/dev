---
layout: post
title: Python “for” Döngüsü
date: 2020-02-23 11:53:00
description: python-kosul-ve-donguler
categories: python-kosul-ve-donguler
tags:  
    - döngü
    - for
    - python
---


Yazdığımız programda tekrarlı işlemler bulunuyorsa döngü kullanmamız gerekir. Döngüler; belirlediğimiz sayıda veya sürekli( belirli bir koşul sağlandığı sürece ) tekrarlama deyimleridir. Bizim belirlediğimiz sayıda tekrarlama yapan döngü, “for” döngüsü; belirli bir koşul sağlandığı sürece, sürekli tekrarlama yapan döngü ise “while” döngüsüdür. Biz bu yazımızda “for” döngüsüne giriş yapacağız.

“for” döngüsünde tekrarlama sayısını kendimiz belirleriz. “for” döngüsü, kendimizin belirlediği sayıda tekrarlı işlem yapmamızı sağlar. Ancak “for” döngüsünün bize yardımcı olduğu çok daha önemli bir özelliği vardır. “for” döngüsü bize bir dizinin elemanları arasında dolaşmamız konusunda büyük kolaylıklar sağlar. Döngünün akış diyagramı(üstüne tıklayarak açabilirsiniz):

![](/assets/kod/python/python35.webp)

Daha önce belirttiğimiz gibi, döngünün tekrar sayısını biz belirliyoruz. Döngüye, bir başlangıç değeri ve bitiş değeri tanımlanır. Başlangıç değerinden, bitiş değerine kaç adımda ulaştığımız döngünün tekrar sayısını verir. Bu adımlarının büyüklüğünü( artış veya azalış miktarı ) kendimiz belirleyerek döngünün tekrar sayısını ortaya çıkarmış oluruz. Bunu döngü değişkeni( iterasyon değişkeni ) aracılığıyla yaparız. Döngü değişkeni, döngüye özel olarak kullanıcı tarafından tanımlanan değişkenlerdir. Döngü değişkeni, başlangıç değerinden artarak veya azalarak bitiş değerine ulaşır. Böylelikle döngü tamamlanmış olur. Örnek olarak, döngünün başlangıç değeri 1, bitiş değeri 5 ve adım büyüklüğümüz(artış miktarı) 1 olsun. Döngü, 1’den 5’e toplamda beş adımda tamamlanacaktır. “for” döngüsüne kısa bir giriş yaptıktan sonra artık “for” döngüsünün nasıl kullanıldığına geçelim:

> Döngülerin her bir adımı iterasyon olarak adlandırılır.

```python
for döngü_değişkeni in kullanılacak_dizi:
    işlemler
```

```python
for döngü_değişkeni in range(iterasyon sayısı):
    işlemler
```

“range()” fonksiyonu, başlangıç ve bitiş değerini belirleyebildiğimiz bir liste oluşturur. Kullanımı:

```python
range(başlangıç_değeri, bitiş_değeri, adım_büyüklüğü)
```

![](/assets/kod/python/python36.webp)

“range()” fonksiyonunda, varsayılan başlangıç değeri 0 ve varsayılan adım büyüklüğü değeri de 1’dir. Başlangıç değeri ve adım büyüklüğü girilmezse varsayılan değerler alınacaktır.

```python
for i in range(5):
    print(i)
```

![](/assets/kod/python/python37.png)

```python
# Adım büyüklüğünü 2 yapalım
for i in range(1, 6, 2):
    print(i)
```

![](/assets/kod/python/python38.png)

```python
# Azalan miktara örnek
for i in range(5, 0, -2):
    print(i)
```

![](/assets/kod/python/python39.png)

```python
# reversed() fonksiyonunu da kullanabiliriz.
for i in reversed(range(1, 6, 2)):
    print(i)
```

![](/assets/kod/python/python40.png)

```python
dizi = [1, 3, 100, 93, 35]
for i in dizi:
    print(i)
```

![](/assets/kod/python/python41.png)

Dizinin eleman sayısı değişiyorsa veya kesin olarak bilinmiyorsa “len()” fonksiyonundan faydalanabiliriz. “len()” fonksiyonu bir nesnedeki eleman sayısını verir.

```python
dizi = [1, 3, 100, 93, 35]
for i in range(len(dizi)):
    print(i, dizi[i])
```

![](/assets/kod/python/python42.png)



Bir örnek ile yazımızı sonlandıralım. Örneğimiz; kullanıcının belirlediği aralıktaki tek ve çift sayıları bulup, onları iki ayrı listede saklayan bir program olsun. Örneğimizde “%” işlevinden yararlanacağız. “%” işlevi, bölme işleminden kalan sayısı verir. Kodlamaya geçelim:


```python
bas = int(input('Başlangıç Değeri: '))
bit = int(input('Bitiş Değeri: '))
tek_sayilar = []                # Tek sayılar için liste
cift_sayilar = []               # Çift sayılar için liste
for i in range(bas, bit):
    if i % 2:                   # eğer 2'ye bölümden kalan varsa tektir.
        tek_sayilar.append(i)   # Sayıyı listeye ekleme
    else:                       # eğer 2'ye bölümden kalan yoksa çifttir.
        cift_sayilar.append(i)
print('Tek sayılar: '+str(tek_sayilar))
print('Çift Sayılar: '+str(cift_sayilar))
```


![](/assets/kod/python/python43.png)

Bu yazı için şimdilik bu kadarının yeterli olduğunu düşünüyorum. İlerleyen zamanlarda, “continue“,  “break” ve “pass” terimleri ile ilgili yazımız olacak. Görüşmek üzere!

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)