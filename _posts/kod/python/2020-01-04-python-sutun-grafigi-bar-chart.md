---
layout: post
title: Python ile Sütun Grafiği (Bar Chart)
date: 2020-01-04 22:40:00
description: python-ornek-uygulamalar
categories: python-ornek-uygulamalar
tags:  
    - bar chart
    - python grafikler
    - sütun grafiği
    - python
---

Çalışmada Kullanılan Modüller:

* Tkinter: Arayüz ve grafik oluşturma
* Random: Sütunlara rastgele renkler verme

Bu yazımızda, Python’da “Tkinter” modülünü kullanarak basit sütun grafiği oluşturacağız. Bu işi yapan modüller elbette mevcut ancak modüllere olan bağlılığı azaltmak ve programlama bilgimizi geliştirmek amacıyla kodları kendimiz oluşturacağız. Farklı kullanımlar görmek amacıyla grafik verilerini, sözlük içinde sözlük yapısında programa dahil edeceğiz. Grafiğimiz bir arayüz ile gösterilecek ve bu arayüzde  3 adet buton olacak. Bu 3 buton; verilerin isimlerini, değerlerini ve yardımcı çizgileri açıp kapatmaya yaracak. Vakit kaybetmeden kodlama kısmına geçelim. 

Hatırlatma: Programı yazarken, kodların satır numaralarını takip etmeniz kolaylık sağlayacaktır.

Öncelikle programımıza  modülleri ekliyoruz:

```python
#!/usr/bin/env python
__author__     = "Tunahan Bilgiç"
__copyright__  = "kodlamaogreniyorum.com, Copyright 2020"

import tkinter as Tk
from random import randint
```

Değişik kullanımlar görelim diye verilerimizi sözlük içinde sözlük olarak aktaracağımızdan bahsetmiştik. Bu kısımda gerekli değişikleri yaparak, verilerinizi veri tabanından, Excel’den veya başka bir ortamdan aktarabilirsiniz.

“elemanlar” isimli sözlüğün, farklı isimlerde sözlükleri var.(“X”, “Y”, …)  Örnek olarak, “X” sözlüğünü inceleyelim. “X” sözlüğünde  iki tane anahtar bulunmaktadır. Bu anahtarlar, “X” ‘in grafikteki değerini ve renk kodunu içermektedir. Renkleri rastgele oluşturacağımız için “renk” anahtarının değeri bulunmamaktadır. 

```python
elemanlar = {
  "X" : {
    "değer" : 1500,
    "renk" : ""
  },
  "Y" : {
    "değer" : 335,
    "renk" : ""
  },
  "Python" : {
    "değer" : 750,
    "renk" : ""
  },
  "Kodlama" : {
    "değer" : 1000,
    "renk" : ""
  },
  "Öğreniyorum" : {
    "değer" : 1993,
    "renk" : ""
  }
}
```

Renk kodlarını, rastgele olacak şekilde üretelim:

```python
for i, j in elemanlar.items():
    renk = "#" + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9))
    elemanlar[i]['renk'] = renk
```

Kullanıcılar farklı ekran boyutlarına sahiptir. Bu nedenle, arayüz ve grafiğimizi her kullanıcının ekranına özel ölçekli olarak oluşturacağız. Kullanıcının ekran boyutlarını öğrenmek için öncelikle arayüzü oluşturuyoruz ve temel ayarları yapıyoruz:

```python
arayuz = Tk.Tk()

#Kullanıcı Arayüzü Ayarları
ekran_olcek = 0.6 #Boyut için
ekran_gen = int(arayuz.winfo_screenwidth() * ekran_olcek)
ekran_yuk = int(arayuz.winfo_screenheight() * ekran_olcek)
ekran_boyutu = str(ekran_gen)+'x'+str(ekran_yuk)
arayuz.geometry(ekran_boyutu)
arayuz.title("Sütun Grafiği")
arayuz.resizable(False, False)
canvas = Tk.Canvas(arayuz, width=ekran_gen, height=ekran_yuk, background="white smoke")
canvas.pack(expand=0)
ayarlar = [True, True, True]  # Sırasıyla: Çizgi, Değerler, İsimler (butonlar için)
```

Arayüzü oluşturduk. Şimdi bu arayüzün üzerindeki hesaplamaları yapalım. Arayüz alanının %90’ını kullanılarak, grafiğin ve butonların arayüzün kenarlarına çarpmasını engelleyelim. Sonrasında, yatay alanın %75’ini grafik için geri kalanını da butonlar için ayıralım ve sütunların hesaplarını yapalım:

```python
degerler = [t["değer"] for t in elemanlar.values()]
kul_alan_x = int(ekran_gen * 0.9)       #Arayüzün 0.9'u
grafik_alan_y = int(ekran_yuk * 0.9)    #Arayüzün 0.9'u
grafik_alan_x = int(kul_alan_x * 0.75)  #Yatay eksenin 0.75'i grafiğin
buton_x = ((kul_alan_x - grafik_alan_x) / 2) + grafik_alan_x
buton_pay_y = (grafik_alan_y * 0.5) / 3
bar_kalinlik = pay_x = int((grafik_alan_x / (len(elemanlar) + 1)) / 2)
pay_y = int(grafik_alan_y * 0.1)
bar_boy = (1 / max(degerler) * (grafik_alan_y - (2 * pay_y)))
```

Artık grafiğimizi oluşturma kısmına geçiyoruz. Ben başka projelerimde kullanmak için grafiği fonksiyon ile oluşturmayı seçtim. Siz bu kısımdaki yapıyı düzenleyerek, grafiği “sınıf” olarak tanımlayabilirsiniz. Bu kısımdan itibaren, fonksiyonun kodlarını parça parça inceleyeceğiz. Fonksiyonu tanımlayalım ve eksenleri arayüz üzerinde oluşturalım:

```python
def bar_chart(elemanlar, ayarlar):

    x = pay_x
    y = pay_y
    canvas.create_line(x, grafik_alan_y, grafik_alan_x, grafik_alan_y, fill="black")  # X ekseni
    canvas.create_line(x, y, x, grafik_alan_y, fill="black")                          # Y ekseni
    canvas.create_text(x, y - (pay_y / 2), text="Değerler")
    canvas.create_text(grafik_alan_x + pay_x, grafik_alan_y, text="Elemanlar")
```

Artık grafiği oluşturabiliriz. Bunun için “canvas” ‘ta dikdörtgen oluşturmamıza yarayan, “canvas.create_rectangle” komutunu kullanacağız. Sözlüğün elemanları arasında dolaşan döngüyü oluşturalım. Grafiğin ayarları, sözlüğün elemanına bağlı olduğu için onların da döngü içinde yer alması gerekir:

```python
    for i, j in elemanlar.items():

        if ayarlar[2] is True:
            canvas.create_text((pay_x / 2), grafik_alan_y - (elemanlar[i]['değer'] * bar_boy), text=elemanlar[i]['değer'])

        x = x + pay_x
        canvas.create_rectangle(x, grafik_alan_y - (elemanlar[i]['değer'] * bar_boy), x + bar_kalinlik, grafik_alan_y, fill=elemanlar[i]['renk'])

        if ayarlar[1] is True:
            canvas.create_line(x, grafik_alan_y - (elemanlar[i]['değer'] * bar_boy), pay_x, grafik_alan_y - (elemanlar[i]['değer'] * bar_boy), dash=(1, 5), fill="gray15")

        x = x + bar_kalinlik

        if ayarlar[0] is True:
            canvas.create_text(x - (bar_kalinlik / 2), grafik_alan_y + (pay_y / 2), text=i)
```

> “create_rectangle” komutunun kullanımı “create_rectangle(x1,y1,x2,y2)” şeklindedir. (x1,y1) dikdörtgenin sol üst köşesini, (x2,y2) dikdörtgenin sağ alt köşesini ifade eder. “(fill=””)” komutu ile dikdörtgenin içini boyamada kullanıyoruz.

> “x” değişkeni yatay eksende en son çizim yapılan koordinatı temsil etmektedir. Sürekli güncellendiğine dikkat edelim.

Butonları ve işlevlerini (fonksiyonlarını) oluşturalım. Butona basıldıktan sonra, eski çizimlerin kalmaması için “canvas” ‘ın temizlenmesi ve tekrar grafik oluşturmamız gerekir:

```python
    def isimler_on():
        if ayarlar[0] is False:
            ayarlar[0] = True
        else:
            ayarlar[0] = False
        canvas.delete("all")
        bar_chart(elemanlar, ayarlar)

    def cizgi_on():
        if ayarlar[1] is False:
            ayarlar[1] = True
        else:
            ayarlar[1] = False
        canvas.delete("all")
        bar_chart(elemanlar, ayarlar)

    def degerler_on():
        if ayarlar[2] is False:
            ayarlar[2] = True
        else:
            ayarlar[2] = False
        canvas.delete("all")
        bar_chart(elemanlar, ayarlar)

    Tk.Button(arayuz, font="times 12 bold", text="İSİMLERİ AÇ / KAPA", command=isimler_on, background="green",
                            anchor="nw").place(x=buton_x, y=(grafik_alan_y / 2) - buton_pay_y)
    Tk.Button(arayuz, font="times 12 bold", text="ÇİZGİLERİ AÇ / KAPA", command=cizgi_on, background="red",
                             anchor="nw").place(x=buton_x, y=grafik_alan_y / 2)
    Tk.Button(arayuz, font="times 12 bold", text="DEĞERLERİ AÇ / KAPA", command=degerler_on, background="blue",
              anchor="nw").place(x=buton_x, y=(grafik_alan_y / 2) + buton_pay_y)
```

Son olarak, program ilk çalıştığında grafiği oluştursun diye grafik fonksiyonunu çağırıyoruz ve arayüzü ana döngüye* alıyoruz:

```python
bar_chart(elemanlar, ayarlar)
arayuz.mainloop()
```

> * ”Tkinter” modülünün işleyişi gereği, oluşturduğumuz birimleri ana döngüye (mainloop) almamız gerekir. Yoksa oluşturduğumuz birimler görünmeyecektir.

<div style="display: flex; justify-content: center; gap: 10px;">
    <img src="{{ site.baseurl }}/assets/kod/python/python49.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/python/python50.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/python/python51.png" alt="If-ElseIf-Else Yapısı">
</div>

![](/assets/kod/python/python52.gif)

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)