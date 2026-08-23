---
layout: post
title: Python “print()” Komutu Detaylar
date: 2019-12-29 17:34:00
description: python-temel-bilgiler
categories: python-temel-bilgiler
tags:  
    - lower
    - upper
    - print
    - python
---


Bu yazımız “print()” komutu ile ilgili detaylar ve kolaylıklar üzerine olacak. Bir önceki yazımızda, “print()” komutu ile değişken yazdırma ve yazı yazdırma biçimlerini öğrenmiştik. Şimdi “print()” komutunun farklı kullanımlarını inceleyelim.

Yazıyı çoğaltmak için “*” ve “+” operatörü:

```python
print("Python"*2)
print(3 * 4)
print('3'*4)
print(1 + 2)
print("1"+"2")
print("*"*5+" 5 Tane Yıldız")
```

![](/assets/kod/python/python13.png)

```python
x = "Python"
y = 5
print(x * y)
print("x"*y)
```

![](/assets/kod/python/python14.png)

Yazıyı ayırmak için “*” operatörü ve ayraç kullanmak için “sep” parametresi:

```python
print("İzmir", "Manisa")
print("İzmir", "Manisa", sep="-")
print("İzmir", "Manisa", sep="*")
print(3, 2, 1, sep="x")
```

![](/assets/kod/python/python15.png)

```python
print(*"izmir")
print(1,2,3,4,5, sep="+")
print(*"12345", sep="+")
print("12345", sep="+")   #"12345" Tek eleman olduğu için ayrışmayacak.
```

![](/assets/kod/python/python16.png)

Yazının son karakterini belirlemek için “end” parametresi:

```python
print("Cümlenin sonunda ünlem var", end="!")
print("Cümlenin sonunda ünlem var", end="!\n") #Alt satıra geçmek için unutmayalım.
x = 35
print(x, end="!")
```

![](/assets/kod/python/python17.png)

> Kaçış operatörleri (“\t” ve “\n“) ile ilgili bilgi için, “Python ile Programlamaya Giriş“ yazımızı inceleyebilirsiniz.

Son olarak yazıyı büyültme ve küçültme fonksiyonlarına değineceğiz. Bu fonksiyonlar “print()” komutu ile ilgili değil ancak yazılarla ilgili olduğu için burada değinmek yararlı olacaktır. Örnek kullanım:

```python
yazı = "biçimSiZ yAzı" 
print(yazı.upper())
print(yazı.lower())
print(yazı.title())
#Bu fonksiyonlar kalıcı değildir. Kalıcı yapma:
büyük_yazı = yazı.upper()
print(büyük_yazı)
```

![](/assets/kod/python/python18.png)

Bir sonraki yazımız “Python Komut Dosyaları ve Veri Türleri” hakkında olacak.

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
