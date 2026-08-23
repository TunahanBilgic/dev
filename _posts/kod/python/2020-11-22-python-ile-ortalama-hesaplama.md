---
layout: post
title: Python ile Ortalama Hesaplama (Aritmetik, Geometrik, Harmonik)
date: 2020-11-22 21:01:00
description: python-ornek-uygulamalar
categories: python-ornek-uygulamalar
tags:  
    - pie chart
    - dairesel grafik
    - pasta grafik
    - python
---

Bu yazımızda Python kullanarak ortalama hesaplayan program oluşturacağız. Oluşturduğumuz program, veri olarak girilen dizinin aritmetik, geometrik ve harmonik ortalamasını hesaplayacak. Python’da bulunan “statistics” modülündeki fonksiyonlar ile kolay bir şekilde bu ortalamaları hesaplayabiliyoruz ancak programlama bilgimizi geliştirmek ve modüllere olan bağımlılığı azaltmak için kendimiz bu hesaplamaları yapan bir program oluşturacağız.

# Aritmetik Ortalama:

$$
\bar{x} = \frac{1}{n} \sum_{i=1}^n x_i = \frac{1}{n}(x_1 + \cdots + x_n)
$$

<span style="color: red;">Statistics Modülü Fonksiyonu:</span> `statistics.mean(x)`

```python
def aritmetik(self):
    art = 0
    for i in self:
        art += i
    art /= len(self)
    print('Aritmetik Ortalaması:', art)
```

# Geometrik Ortalama:

$$
\left( \prod_{i=1}^n x_i \right)^{1/n} = \sqrt[n]{x_1 \cdot x_2 \cdots x_n}
$$

<span style="color: red;">Statistics Modülü Fonksiyonu:</span> `statistics.geometric_mean(x)`

```python
def geometrik(self):
    geo = self[0]
    for i in range(1, len(self)):
        geo *= self[i]
    geo **= (1 / len(self))
    print('Geometrik Ortalaması:', geo)
```

# Harmonik Ortalama:

$$
\frac{n}{\frac{1}{x_1} + \frac{1}{x_2} + \cdots + \frac{1}{x_n}}
$$

<span style="color: red;">Statistics Modülü Fonksiyonu:</span> `statistics.harmonic_mean(x)`

```python
def harmonik(self):
    har = 1 / self[0]
    for i in range(1, len(self)):
        har += (1 / self[i])
    har = len(self) / har
    print('Harmonik Ortalaması:', har)
```

Yazdığımız kodları tek bir “script” dosyası altında toplayıp, “print()” komutu ile ekrana bilgi olarak yazdıralım:

```python
#kodlamaogreniyorum.com, 2020
import statistics

def aritmetik(self):
    art = 0
    for i in self:
        art += i
    art /= len(self)
    print('Aritmetik Ortalaması:', art)

def geometrik(self):
    geo = self[0]
    for i in range(1, len(self)):
        geo *= self[i]
    geo **= (1 / len(self))
    print('Geometrik Ortalaması:', geo)

def harmonik(self):
    har = 1 / self[0]
    for i in range(1, len(self)):
        har += (1 / self[i])
    har = len(self) / har
    print('Harmonik Ortalaması:', har)

dizi = []
[dizi.append(i) for i in range(1, 10)]
aritmetik(dizi)
geometrik(dizi)
harmonik(dizi)

#Modül çıktıları ile karşılaştırma
print("\nModül Çıktıları:\nAritmetik:", statistics.mean(dizi))
print("\nGeometrik:", statistics.geometric_mean(dizi))
print("\nHarmonik:", statistics.harmonic_mean(dizi))
```

![](/assets/kod/python/python56.webp)

![](/assets/kod/python/python57.webp)

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
