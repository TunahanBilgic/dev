---
layout: post
title: Python’da Değişken Tanımlama
date: 2019-12-26 15:19:00
description: python-temel-bilgiler
categories: python-temel-bilgiler
tags:  
    - ide
    - kaçış operatörleri
    - print
    - pycharm
    - python
---


Bundan sonraki yazılarımızda Python’u, PyCharm üzerinden kullanacağım. PyCharm, Python için bir geliştirme ortamıdır. Bir önceki yazımızda bu konu ile ilgili detaylı bilgiler bulunmaktadır.

Bir program oluştururken bazı bilgileri saklamak, üzerlerinde işlem yapmak ve bu bilgileri güncellemek ihtiyacı duyarız. Bunun için, değişken(variable) kullanmamız gerekir. Kısacası değişkenler, bizim isimlendirdiğimiz ve bilgisayarda geçici süreyle saklı kalan tanımlamalardır. Değişken tanımlama:

```python
DEĞİŞKEN İSMİ = ATANAN DEĞER
```

şeklinde yapılır. Örnek olarak, “plaka” isimli bir değişken tanımlayalım ve ona “35” değerini atayalım. Sonrasında, “print()” komutu ile ekrana yazdıralım.

```python
plaka = 35
print(plaka)
```

![](/assets/kod/python/python8.png)

> Değişken isimleri; boşluk, önce sayı sonra harf(6x) ve özel ifade olmayacak şekilde belirlenmelidir. Aşağıdaki atamaları yapmayı denerseniz bir hata uyarısı ile karşılaşacaksınız.

```python
35y = 5         #Önce sayı olmamalı
bu sene = 2019  #Boşluk olmamalı
def = 5         #Özel ifade olmamalı
```

<h1>Değişkenler Aracılığı ile Ekrana Bilgi Yazdıralım!</h1>

Sözel bir ifadeyi değişkene atamak istiyorsak tek tırnak(‘ ‘) veya çift tırnak(” “) içinde yazmamız gerekir. Örnek olarak; “şehir” isimli bir değişken oluşturup, “İzmir” ifadesini atayalım. Sonrasında, “print()” komutu ile ekrana yazdıralım. “print()” komutunun içine çift tırnak kullanmadan değişkenin ismini yazarsak, yazdığımız değişkenin değerini ekrana yazdırır. 

```python
şehir = "İzmir"
print(şehir)
```

![](/assets/kod/python/python9.png)

Eğer ekrana bir sözel ifade ile bir sayısal değer yazdırılmak istenirse bunun için çeşitli yazdırma yöntemleri mevcuttur.Bunu bir örnek ile açıklayalım. Ekrana, “Bugün günlerden perşembe. Hava 12 derece ve saat 14.45 .” yazısını yazdıralım. “perşembe”, “12” ve “14.45” bilgileri; “gün”, “hava” ve “saat” isimli değişkenlerden gelsin. 

```python
gün = "perşembe"
hava = 12
saat = 14.45
print("Bugün günlerden %s. Hava %d derece ve saat %g." %(gün, hava, saat))
print("Bugün günlerden", gün, ". Hava", hava, "derece ve saat", saat, ".")  #bu kodun çıktısına dikkat edelim.
bilgiler = ['perşembe', '12', '14.45'] #liste tanımlaması yaptık bu konuyu ile ilgili yazımız olacak.
print('Bugün günlerden {0}. Hava {1} derece ve saat {2}.'.format(*bilgiler))
```

![](/assets/kod/python/python10.png)

Dikkat ettiyseniz eğer, ikinci “print()” komutunun çıktısında değişkenlerden sonra boşluklar oluştu. Ben kod yazarken, ilk “print()” komutundaki yöntemi tercih ediyorum. Bana kullanımı daha esnek ve rahat geliyor.

“print()” komutunu inceleyecek olursak, “%” ile başlayan ifadeler dikkat çekmektedir. Tıpkı kaçış operatörü gibi, “%” operatörü de “print()” komutu için özel anlam taşımaktadır. “%” ifadesinin yanında yer alan karaktere göre “print()” ekrana bilgi yazdırmaktadır. Bu bilgiler değişkenlerden gelmektedir. Bilgi sağlayan değişkenler; tırnağın dışında  “%” operatörü ile belirtilmeli ve  birden fazla ise eğer sırasıyla, parantez içinde yazılmalıdır.

```python
%c : Değişkeni tek bir karakter olarak yazdırma.
%s : Değişkeni karakter dizisi olarak yazdırma.
%d : Değişkeni tam sayı olarak yazdırma.
%f : Değişkeni ondalıklı sayı olarak yazdırma.
%g : Değişkeni en uygun formda yazdırma. (Tam sayı, ondalıklı sayı)
```
![](/assets/kod/python/python11.png)

Tanımladığımız bir değişkeni silmek istiyorsak “del” komutunu kullanırız.

![](/assets/kod/python/python12.png)

> del(saat) şeklinde de kullanabilirdik.

<h1>Değişken Atamalarında Bazı Kolaylıklar</h1>

```python
x, y, z = 3, 4, 5        #Aynı anda çok sayıda değişkene atama yapma
x = y = z = 35           #Aynı anda bir değeri birden fazla değişkene atama
x, y = y, x              #İki değişkenin değerlerini birbiriyle değiştirme(swap)
```

Bir sonraki yazımız [*“print()” komutu ile ilgili detaylar*](https://www.kodlamaogreniyorum.com/python-print-komutu-detaylar/) hakkında olacak.

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)