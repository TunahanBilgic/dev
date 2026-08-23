---
layout: post
title: Python “input()” Komutu ve Veri Türleri
date: 2020-01-02 09:51:00
description: python-temel-bilgiler
categories: python-temel-bilgiler
tags:  
    - input
    - klavyeden veri alma
    - program dosyaları
    - veri türleri
    - py
    - python
---

Bu yazımızda, Python program(komut) dosyaları, klavyeden veri girişi ve veri türleri konularına değineceğiz. Bundan önceki yazılarımızda [“Python Etkileşimli Kabuk](https://www.kodlamaogreniyorum.com/python-ile-programlamaya-giris/)(Interactive Shell)” üzerinden programlama yapmıştık.([PyCharm](https://www.jetbrains.com/pycharm/download/) için -> “Python Console”) Ancak bildiğiniz üzere Etkileşimli Kabuk ile yazdığımız programlar, tanımladığımız değişkenler ve aldığımız çıktılar geçici olarak saklanmaktadır. Oluşturduğumuz programların kaybolmaması için program(komut) dosyalarını kullanırız. 

İşe öncelikle bir adet komut dosyası oluşturmakla başlayalım. PyCharm açıldıktan sonra, sol üstteki “File” menüsündeki “New Project” seçeneğine tıklayalım. “Create Project” isimli bir pencere açılacaktır. Açılan pencerede; “Location” kısmında proje ismi(“untitled” kısmını değiştirin) ve Python dosyalarımızın konumu, “Interpreter” kısmında ise yorumlayıcı yani Python sürümü seçilmektedir. Detaylı yardım için link: 
[PyCharm Yardım Sayfası](https://www.jetbrains.com/help/pycharm/quick-start-guide.html)

![](/assets/kod/python/python19.webp)

Projemizi oluşturduktan sonra; “File -> New -> Python File” adımlarını takip ederek veya proje klasörüne sağ tıklayıp, “New -> Python File” adımlarıyla program dosyamıza isim verelim ve oluşturalım. PyCharm karşımıza boş bir program dosyası getiriyor. Artık kodumuzu yazıp, kaydetmeye hazırız. İlk programımız olarak; “x” ve “y” ismindeki iki tane değişkene kendimizin belirlediği sayıları atayan, bu değerlerin birbirleriyle dört işlemini yaptıran ve “print()” komutuyla ekrana yazdıran bir program oluşturalım.  Programımızı iki farklı şekilde yazabiliriz. 

```python
x = 35
y = 10
print("%d ile %d sayılarının toplamı: %d, farkı: %d, çarpımı: %d ve bölüm: %g'dir.\n" %(x,y,x+y,x-y,x*y,x/y))
```

![](/assets/kod/python/python20.webp)

![](/assets/kod/python/python21.webp)

```python
x = 35
y = 10
top = x + y
cik = x - y
carp = x * y
bol = x / y
print("%d ile %d sayılarının toplamı: %d, farkı: %d, çarpımı: %d ve bölümü: %g'dir.\n" %(x,y,top,cik,carp,bol))
```

![](/assets/kod/python/python22.png)

![](/assets/kod/python/python23.png)

> Python program dosyalarının uzantısı “.py” şeklindedir.

> Programımızı yazdıktan sonra çalıştırmadan önce kaydetmemiz gerekir. PyCharm bu işlemi otomatik olarak yapıyor.

<h1>Veri Türleri</h1>

String – “str” : Karakter dizilerini ifade eden veri tipidir.

Örnek: x = “Python”

*Integer – “int” : Tam sayıları ifade eden veri tipidir.

Örnek: x = 35

Float – “float” : Ondalıklı sayıları ifade eden veri tipidir.

Örnek: x = 35.5

Complex – “complex” : Kompleks(Karmaşık) sayıları ifade eden veri tipidir.(Reel sayılar bu tipe dahildir.)

Örnek: x = 3+4j

List – “list” : Listeleri ifade eden veri tipidir.

Örnek: x = [35, 6, 20]

Tuple – “tuple“: Dilimizde “Demet, Tüp” olarak kullanımı yayın, içi değiştirilemeyen listeleri ifade eden veri tipidir.

Örnek: x = (“Python”, “Öğreniyorum”)

Dictionary – “dict“: Sözlükleri ifade eden veri tipidir.

Örnek: x = {“İzmir”:35, “Ankara”:6}

Set – “set” : Kümeleri ifade eden veri tipidir. Matematikteki kümelere karşılık gelmekte ve aynı özellikleri(kesişim, birleşim vb.) taşımaktadır.

Örnek: x = {1, 2, 3, 4}

**Boolean – “bool” : Mantıksal veri türünü ifade eden veri tipidir. Bu veri tipi  binary(ikili) yapıdadır, 1 byte’lık değeri vardır.  Yalnızca iki değer alır; bir değişken, ya doğrudur ya da yanlıştır. (0 = False, 1 = True)

Örnek: x = True

Veri türünü öğrenmek için “type()” komutunu kullanılırız.

Örnek: type(x)

> * Python 3’ten önce, “int” veri türü 32 bit olmakla beraber belli bir aralığa kadar olan tam sayıları kapsamaktaydı. Aralığın dışındaki tam sayılar 64 bit olan “long”(long-int) veri türüne dahil olmaktaydı. Python 3 ile birlikte, “int” veri tipini sınırsız aralığa sahiptir.

> * * ”Boolean”, bilgisayar biliminin babası olarak kabul edilen ve modern simgesel mantığın kurulmasına katkı veren “George Boole” adına ithaf edilmiştir. 


<h1>Klavyeden Veri Alma ve Tür Dönüşümleri</h1>

Bir bilgisayar programında kullanılacak verileri hep kendimiz belirlemeyiz. Bu verileri, kullanıcının anlık olarak  girmesini veya bir veri tabanından aktarmayı isteyebiliriz. Yazdığımız programlarda kullanılacak verileri değişkenlere atamıştık. Klavyeden veri alırken de aynı mantıkla veriyi bir değişkene atayacağız.

Klavyeden veri almak için “input()” komutu kullanılır. “input()” komutu ile hem sayısal hem de sözel(karakter, dizi) veri alınabilir. Ancak, Python’da “input()” ile girilen bütün veriler karakter dizisi olarak kayıt olur. İşte bu durumdan ötürü, sayısal veriler için tür dönüşümü uygulayacağız.

```python
isim = input('Adınızı girin: ')
yaş = int(input('Yaşınızı girin: '))
yaş2 = input('Yaşınızı girin: ')    #Dönüşüm yapmadık, "str" olacak.
print(isim, yaş)
print(type(isim), type(yaş), type(yaş2))
```

![](/assets/kod/python/python24.png)

![](/assets/kod/python/python25.png)

Gördüğünüz üzere, tür dönüşümü yapılmazsa veri tipi “str” olarak kalıyor. Program yazarken buna dikkat edelim.  Tür dönüşüm fonksiyonları ve bunlarla ilgili bir örnek uygulama yapalım:

```python
int(x, base)        #Veriyi verilen tabandan onlu tabanda tam sayıya dönüştürür.(base=10)
float()             #Veriyi ondalıklı sayıya dönüştürür.
str()               #Veriyi karakter dizisine dönüştürür.
chr()               #Sayısal veriyi karaktere dönüştürür.
ord()               #Karakteri onlu tabandaki değerine dönüştürür.
complex(real, imag) #Veriyi karmaşık sayıya dönüştürür.
bool()              #Veriyi mantıksal karşılığını verir.
hex()               #Veriyi heksadesimal(16 tabanlı) sayı sistemine dönüştürür.
list()              #Veriyi listeye dönüştürür.
set()               #Veriyi kümeye dönüştürür.
dict()              #Veriyi sözlüğe dönüştürür.
tuple()             #Veriyi "demete/tüpe" dönüştürür.
```

![](/assets/kod/python/python26.png)


![](/assets/kod/python/python27.webp)

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
