---
layout: post
title: Python ile Dairesel Grafik (Pie Chart)
date: 2020-01-10 04:50:00
description: python-ornek-uygulamalar
categories: python-ornek-uygulamalar
tags:  
    - pie chart
    - dairesel grafik
    - pasta grafik
    - python
---

Çalışmada Kullanılan Modüller:

* Tkinter: Arayüz ve grafik oluşturma
* Random: Sütunlara rastgele renkler verme
* Functools: Buton komutlarını atama


Bu yazımızda, Python’da “Tkinter” modülünü kullanarak basit dairesel(pasta) grafik oluşturacağız. Bu işi yapan modüller elbette mevcut ancak modüllere olan bağlılığı azaltmak ve programlama bilgimizi geliştirmek amacıyla kodları kendimiz oluşturacağız. [Sütun grafiği yazımızda](https://www.kodlamaogreniyorum.com/python-sutun-grafigi-bar-chart/) olduğu gibi, farklı kullanımlar görmek amacıyla grafik verilerini, sözlük içinde sözlük yapısında programa dahil edeceğiz. Grafiğimiz bir arayüz ile gösterilecek ve bu arayüzde  veri sayısı kadar buton olacak. Bu butonlar ifade ettiği veriyi gösterip, gizlemeye yarayacak. Vakit kaybetmeden kodlama kısmına geçelim. 

Hatırlatma: Programı yazarken, kodların satır numaralarını takip etmeniz kolaylık sağlayacaktır.

Öncelikle programımıza  modülleri ekliyoruz:

```python
#!/usr/bin/env python
__author__     = "Tunahan Bilgiç"
__copyright__  = "kodlamaogreniyorum.com, Copyright 2020"

import tkinter as tk
from random import randint
from functools import partial
```

[Sütun grafiği yazımızda](https://www.kodlamaogreniyorum.com/python-sutun-grafigi-bar-chart/) olduğu gibi, verilerimizi sözlük içinde sözlük olarak aktaracağımızdan bahsetmiştik. Bu kısımda gerekli değişikleri yaparak, verilerinizi veri tabanından, Excel’den veya başka bir ortamdan aktarabilirsiniz. 

```python
elemanlar = {
  "A" : {
    "değer" : 15,
    "renk" : "",
    "buton": "",
    "durum" : True
  },
  "B" : {
    "değer" : 10,
    "renk" : "",
    "buton": "",
    "durum" : True
  },
  "C" : {
    "değer" : 20,
    "renk" : "",
    "buton": "",
    "durum" : True
  },
  "D" : {
    "değer" : 45,
    "renk" : "",
    "buton": "",
    "durum" : True
  }
}
```

Renk kodlarımızı rastgele üretelim ve hesaplamada kullanılmak üzere değerlerimizin toplamını bulalım:

```python
for i, j in elemanlar.items():
    renk = "#" + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9)) + str(randint(0, 9))
    elemanlar[i]['renk'] = renk

degerler = [t["değer"] for t in elemanlar.values()]
```

Kullanıcılar farklı ekran boyutlarına sahiptir. Bu nedenle, arayüz ve grafiğimizi her kullanıcının ekranına özel ölçekli olarak oluşturacağız. Kullanıcının ekran boyutlarını öğrenmek için öncelikle arayüzü oluşturuyoruz ve temel ayarları yapıyoruz:

```python
# kullanıcı arayüzü ayarları
arayuz = tk.Tk()

ekran_olcek = 0.6  # boyut için
ekran_gen = int(arayuz.winfo_screenwidth() * ekran_olcek)
ekran_yuk = int(arayuz.winfo_screenheight() * ekran_olcek)
ekran_boyutu = str(ekran_gen)+'x'+str(ekran_yuk)
arayuz.geometry(ekran_boyutu)
arayuz.title("Pasta Grafiği")
arayuz.resizable(False, False)
canvas = tk.Canvas(arayuz, width=ekran_gen, height=ekran_yuk, background="white smoke")
canvas.pack(expand=0)
```

Artık grafiğimizi oluşturma kısmına geçiyoruz. Ben başka projelerimde kullanmak için grafiği fonksiyon ile oluşturmayı seçtim. Siz bu kısımdaki yapıyı düzenleyerek, grafiği “sınıf” olarak tanımlayabilirsiniz. Bu kısımdan itibaren, fonksiyonun kodlarını parça parça inceleyeceğiz. Fonksiyonu tanımlayalım, grafiğin ve butonların konumları ile ilgili hesaplamaları yapalım:

```python
def pasta_dilimi(elemanlar, degerler):

    grafik = int(ekran_yuk / 6)
    buton_x = ((ekran_gen - ekran_yuk) / 2) + ekran_yuk
    buton_y = ekran_yuk / (2 * (len(elemanlar) + 1))
    bas = 0
```

Fonksiyonda grafiğin oluşturulduğu kısıma geçiyoruz. Bunun için “canvas” ‘ta yay oluşturmamıza yarayan “canvas.create_arc” komutunu kullanacağız. Sözlüğün elemanları arasında dolaşan döngüyü oluşturalım. Bütün yayların merkezi aynı olacağı için, yayların çizilme koordinatlarının aynı olması gerekir. Dairesel grafiğin dilimlerini belirlemek için, “canvas.create_arc” komutunun derecelendirme(“extent”) özelliğinden yararlanacağız. Dilimlerin, bir önceki dilimin bittiği dereceden başlaması gerekir. Elemanın değerini toplam değere bölerek, dilimin derecesini elde ediyoruz:

```python
    for i, j in elemanlar.items():

        aciklik = (j["değer"] / sum(degerler)) * 360
        if j['durum'] is True:

            canvas.create_arc(grafik, grafik, grafik * 5, grafik * 5, start=bas, extent=aciklik, fill=j["renk"], width=2)
        bas += aciklik
```

> “create_arc” komutunun kullanımı “create_arc(x1,y1,x2,y2)” şeklindedir. (x1,y1) koordinatları ile (x2,y2) koordinatları arasına yay çizilir.

Butonları ve işlevlerini (fonksiyonlarını) oluşturalım. Butonlara, ait oldukları elemanın anahtarını atadık “partial(buton_bas, i)” ve fonksiyonun parametresi yaptık. Buton hangi anahtara ait ise fonksiyonun o anahtarın durumunu değiştirmesini sağladık. Böylelikle buton sayısı kadar fonksiyon yazmak yerine, tek bir fonksiyon yazarak kolaylık sağlamış olduk. Butona basıldıktan sonra, eski çizimlerin kalmaması için “canvas” ‘ın temizlenmesi ve tekrar grafik oluşturmamız gerekir:

```python
        def buton_bas(ind):

            if elemanlar[ind]["durum"] is True:
                elemanlar[ind]["durum"] = False
            else:
                elemanlar[ind]["durum"] = True
            canvas.delete("all")
            pasta_dilimi(elemanlar, degerler)

        tk.Button(arayuz, text=i+"= "+str(j["değer"]), font="times 20 bold", command=partial(buton_bas, i), background=j["renk"]).place(x=buton_x, y=buton_y)
        buton_y += ekran_yuk / len(elemanlar)
```

Son olarak, program ilk çalıştığında grafiği oluştursun diye grafik fonksiyonunu çağırıyoruz ve arayüzü ana döngüye alıyoruz:

```python
pasta_dilimi(elemanlar, degerler)
arayuz.mainloop()
```

<div style="display: flex; justify-content: center; gap: 10px;">
    <img src="{{ site.baseurl }}/assets/kod/python/python53.png" alt="If-ElseIf-Else Yapısı">
    <img src="{{ site.baseurl }}/assets/kod/python/python54.png" alt="If-ElseIf-Else Yapısı">
</div>

![](/assets/kod/python/python55.gif)

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
