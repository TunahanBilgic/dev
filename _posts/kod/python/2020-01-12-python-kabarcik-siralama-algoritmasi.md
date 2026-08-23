---
layout: post
title: Python Kabarcık Sıralama (Bubble Sorting) Algoritması
date: 2020-01-12 00:30:00
description: python-algoritmalar
categories: python-algoritmalar
tags:  
    - python algoritmalar
    - kabarcık sıralama
    - bubble sorting
    - python
---


Bu yazımızda, bir [Sıralama algoritması](https://www.kodlamaogreniyorum.com/python-algoritmalar/) olan Kabarcık Sıralama” (Bubble Sorting) algoritmasına değineceğiz. Seçerek Sıralama algoritmasını diziyi küçükten büyüğe sıralamak için kullanacağız.

Kabarcık Sıralama algoritmasının işleyişi, algoritmanın her adımında dizideki iki elemanı karşılaştırma üzerinedir. Küçükten büyüğe sıralama için; dizinin son elemanlarından başlayarak, iki eleman arasında küçük olan her adımda bir sola kayarak başa taşınır. 

![](/assets/kod/matlab/matlab54.webp) 

Görsel Kaynak: [Code Pumpkin](https://codepumpkin.com/bubble-sort/)

[Buradaki bağlantıya](https://www.toptal.com/developers/sorting-algorithms) tıklayarak, sıralama algoritmalarının çalışma şekillerine ait animasyona bakabilirsiniz.

Örnek olarak, “vekt” isimli dizinin adım adım küçükten büyüğe sıralanması:

```python
vekt = [3, 5, 1, 10, -3, 8]
```

[3 5 1 <span style="background-color: yellow;">10</span> <span style="color: red;">-3</span> 8]

[3 5 <span style="background-color: yellow;">1</span> <span style="color: red;">-3</span> 10 8]

[3 <span style="background-color: yellow;">5</span> <span style="color: red;">-3</span> 1 10 8]

[<span style="background-color: yellow;">3</span> <span style="color: red;">-3</span> 5 1 10 8]

[-3 3 5 1 <span style="background-color: yellow;">10</span> <span style="color: red;">8</span>]

[-3 3 <span style="background-color: yellow;">5</span> <span style="color: red;">1</span> 8 10]

[-3 <span style="background-color: yellow;">3</span> <span style="color: red;">1</span> 5 8 10]

[-3 1 3 5 8 10]

Algoritmanın kodları:

```python
def kabarcik_sirala(vektor):
    for i in range(len(vektor)-1):
        for j in reversed(range(i+1, len(vektor))):
            if vektor[j] < vektor[j-1]:
                depo = vektor[j-1]
                vektor[j-1] = vektor[j]
                vektor[j] = depo
                #print(vektor) Algoritmanın adımlarını görmek için.
    print(vektor)

vekt = [3, 5, 1, 10, -3, 8]
kabarcik_sirala(vekt)
```

İlk döngü ( i ) en küçük elemanların atanacağı indisi temsil ediyor. İkinci döngüyü ( j ) ise dizinin iki elemanını kontrol etme amacıyla kullanıyoruz. Algoritma; dizinin son elemanından başlayarak, iki eleman arasındaki en küçük olanı başa taşıyor. Dolayısıyla ikinci döngü ( j ) dizinin son elemanından başlamalı ve son eleman ile kendisinden bir önceki elemanı kontrol ettiği için ilk döngünün bulunduğu yerin bir ilerisinde bitmelidir.[for j in reversed(range( i+1, len(vektor)))] “reversed” komutu, döngü iterasyonlarının azalan biçimde olmasını sağlıyor. Dizinin elemanlarının yerlerini değiştireceğimiz için bir saklama değişkeni(depo) kullanıyoruz. Programın ekran görüntüsü:

![](/assets/kod/python/python65.png)

> “if” koşulunun içine sadece “vektor[j-1], vektor[j] = vektor[j], vektor[j-1]” yazarak kodlamayı kısaltabiliriz.

> 11.satırda sıralanmasını istediğimiz diziyi tanımlıyoruz, 12.satırda da fonksiyonumuzu çağırıyoruz.

Aldığımız çıktı:

![](/assets/kod/python/python66.png)

> Sıralama yapmak için “.sort()” fonksiyonunu kullanabilirsiniz.

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)

Kaynak: [Carnegie Mellon University, School of Computer Science](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Sorting%20Algorithms/sorting.html), [Vikipedi](https://tr.wikipedia.org/wiki/Kabarc%C4%B1k_s%C4%B1ralamas%C4%B1)