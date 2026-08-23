---
layout: post
title: Python ile Programlamaya Giriş
date: 2019-12-25 00:09:00
description: python-temel-bilgiler
categories: python-temel-bilgiler
tags:  
    - ide
    - kaçış operatörleri
    - print
    - pycharm
    - python
---


Bu yazımızda Python ile programlamaya giriş yapacağız. Ancak bu yazının amacı programlama mantığını anlatmak olmayacak. Ama ilerleyen zamanlarda programlama mantığı ve program oluşturulurken kullanılan akış diyagramları ile ilgili yazımız olacak.

Ben Python 3.7 kullanıyorum. [(İndirmek için tıklayın.)](https://www.python.org/downloads/) Sitemizdeki bütün içerik Python >=3.7 üzerine olacaktır. Buna ek olarak Python’u bir IDE(Entegre Geliştirme Ortamı) ile kullanmaktayım. Sizlere de tavsiyem bir IDE kullanmanız olacaktır. Ben JetBrains şirketinin geliştirdiği Pycharm’ı kullanmaktayım. İncelemeniz için bazı IDE linkleri:

* [PyCharm](https://www.jetbrains.com/pycharm/download) – Geliştiricisi: JetBrains
* [Spyder & Anaconda](https://www.anaconda.com/distribution/) – Geliştiricisi: Open-Source 
* [Atom](https://atom.io/) – Geliştiricisi: Github
* [Visual Studio Code (VS Code)](https://code.visualstudio.com/) – Geliştiricisi: Microsoft 
* Python IDLE -> Python ile birlikte gelen, varsayılan geliştirme ortamı.

Öncelikle Python ile etkileşim kurduğumuz bileşen olan Python Interactive Shell’den (Python Etkileşimli Kabuk) bahsedeceğiz. Python Interactive Shell; sayısal hesaplamalar yapabilme, program yazıp çalıştırabilme, daha önceden kaydedilmiş veya programdaki mevcut fonksiyonları kullanarak çıktı alabilme gibi işlevlere sahiptir. Python Interactive Shell’e komut istemi(Linux dağıtımları için: terminal/uç birim) veya IDLE üzerinden erişilebilmektedir.


![](/assets/kod/python/python1.png)

```python
5 + 5   #toplama işlemi
5 - 5   #çıkarma işlemi
5 * 5   #çarpma işlemi
5 / 5   #bölme işlemi
12 // 5 #tam sayı bölme işlemi
5 % 5   #mod bulma
```

Bazen yazdığımız kodların yanına hatırlatma notları veya yorum yazmak isteriz. Bunun için “#” operatörünü kullanırız.

![](/assets/kod/python/python2.png)

Komut İstemi üzerinden Python Interactive Shell

![](/assets/kod/python/python3.png)

IDLE üzerinden Python Interactive Shell

> Python’un sitesi üzerinden Python Interactive Shell’i çevrim içi olarak deneyebilirsiniz.

<h1>Ekrana Bilgi Yazdıralım!</h1>

Ekrana yazı yazdırmak için “print()” komutu kullanılır. Bu komut:

```python
print('Yazdırılacak Yazı')
```

şeklinde kullanılır.

Aşağıdaki kodu girelim ve çıktımızı inceleyelim.

```python
print("Hello, World!")
```
![](/assets/kod/python/python4.png)

“print()” komutu ile yazı yazdırılırken üç farklı şekilde tırnak işareti kullanılabilir:

1. Tek tırnak -> print(‘Yazı‘)
2. Çift tırnak -> print(“Yazı“)
3. Üç tane çift tırnak -> print(“””Yazı“””)

![](/assets/kod/python/python5.png)

Yazdırılacak yazıda kesme işareti , tırnak varsa veya özel bir formata sahipse:

```python
print("İzmir'de hayat çok güzel! ")
print('"Python" öğreniyorum.')
print("""<----Python Öğreniyorum------
---kodlamaogreniyorum.com--->""")
```

![](/assets/kod/python/python6.png)

Yazdırdığımız yazılarda boşluk olması veya yazının alt satırdan devam etmesi gibi durumlar varsa kaçış operatörü kullanılması gerekmektedir.

```python
print("İki TAB boşluk\t\tbıraktım ve\nYazıyı alt satırdan devam ettirdim.")
```

![](/assets/kod/python/python7.png)

```python
\t         #Bir TAB sağa kaydırma
\n         #Bir alt satıra geçme
\a         #Uyarı sesi çıkartma
\b         #Backspace görevi(Sola kaydırarak silme)
\r         #Satır başına kadar silme
print(r"") #Kaçış operatörlerini iptal etme
```

> Kaçış operatörlerini iptal ederken print(r“”) ifadesi yerine, fazladan “\“ koyularak aynı işlem yapılabilir. Örnek kullanım: print(“D:\\tunahan\python”)

Programlamaya giriş yazısı için bu kadar bilgi yeterli. Bir sonraki yazımız [“değişken tanımlama”](https://www.kodlamaogreniyorum.com/pythonda-degisken-tanimlama/) hakkında olacak.

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)