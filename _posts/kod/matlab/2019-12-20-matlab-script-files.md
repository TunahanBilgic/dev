---
layout: post
title: MATLAB Komut Dosyaları(Script Files)
date: 2019-12-20 02:47:00
description: matlab-temel-bilgiler
categories: matlab-temel-bilgiler
tags: 
    - komut dosyası 
    - m dosyası 
    - matlab script

---

MATLAB’da programlama, araç kutularını(toolboxes) saymazsak iki başlıkta özetlenebilir:

1. Komut Penceresi ile Programlama
2. Komut Dosyaları ile Programlama
   - *Düz Komut Dosyaları (Script Files)*
   - *Fonksiyon Komut Dosyaları (Function Files)*
Bundan önceki yazılarımızda komut penceresi ile programlama yapmıştık. Ancak bildiğiniz üzere komut penceresi ile yazdığımız programlar, tanımladığımız değişkenler ve aldığımız çıktılar geçici olarak saklanmaktadır. Oluşturduğumuz programların kaybolmaması için komut dosyalarını kullanırız. Komut dosyalarını kendi içinde; düz ve fonksiyon komut dosyaları şeklinde ikiye ayırmamız mümkündür.  Fonksiyon komut dosyaları ile düz komut dosyaları arasında bir takım farklar bulunmaktadır. Biz bu yazımızda düz komut dosyalarına değineceğiz ancak fonksiyon komut dosyaları ile ilerleyen zamanlarda bir yazımız olacak.

İşe öncelikle bir adet komut dosyası oluşturmakla başlayalım. Benim kullandığım arayüzün dili İngilizce ve sizde de öyle olduğunu varsayarak anlatımda İngilizce kelimelere yer vereceğim. Yeni komut dosyası oluşturmak için “Home” sekmesinin altındaki “New Script” butonuna tıklıyoruz. (Kısayol tuşu: “Ctrl + N”)
![](/assets/kod/matlab/matlab11.png)
MATLAB Metin Editörü karşımıza boş ve isimlendirilmemiş bir komut dosyası getiriyor. Artık kodumuzu yazıp, kaydetmeye hazırız. İlk programımız olarak; “a” ve “b” ismindeki iki tane değişkene kendimizin belirlediği sayıları atayan, bu değerlerin birbirleriyle dört işlemini yaptıran ve “fprintf()” komutuyla ekrana yazdıran bir program oluşturalım. Programımızı iki farklı şekilde yazabiliriz. 
```matlab
a = 35;
b = 6;
fprintf('%d ile %d sayılarının toplamı: %d, farkı: %d, çarpımı: %d ve bölümü: %g ''dir.\n',a,b,a+b,a-b,a*b,a/b);
```
```matlab
a = 35;
b = 6;
top = a + b;
cikarma = a - b;
carpma = a * b;
bolme = a / b;
fprintf('%d ile %d sayılarının toplamı: %d, farkı: %d, çarpımı: %d ve bölümü: %g''dir.\n,top,cikarma,carpma,bolme);   
```
> Yazı yazdırırken; ” ‘ “, ” % “ gibi operatörler MATLAB tarafından özel olarak algılanır. Eğer bunları ekrana yazdırmak istersek, arka arkaya iki defa kullanmamız gerekir.
Programımızı yazdıktan sonra çalıştırmadan önce kaydetmemiz gerekir. Bu işlemi, “Editor” sekmesinin altındaki “Save” butonu ile veya “Ctrl + S” kısayolu ile yapabiliriz. Kaydetme sırasında açılan pencerede, programı kaydetmek istediğimiz yeri seçmemiz ve programa bir isim belirlememiz gerekir. Programın ismini “ilkprogram” olarak belirleyip, kaydetme işlemini yapalım. MATLAB, açılışta kendisine bir çalışma klasörü belirler. Bunu kendimiz de ayarlayabiliriz. Eğer az önce kayıt yeri olarak seçtiğimiz klasör ile MATLAB’ ın çalışma klasörü farklı ise ekrana şu şekilde bir uyarı çıkacaktır: 
![](/assets/kod/matlab/matlab12.png)
Bu aşamada “Change Folder” seçeneğini seçip, mevcut çalışma klasörünü değiştirelim. Programı çalıştırmak için, “Editor” sekmesinin altındaki “Run” butonuna basmamız veya komut penceresine programın ismini girmemiz gerekir. (Kısayol tuşu: “F5”)

> Komut dosyalarının uzantısı “**.m**” şeklindedir.

> Yazdığınız kod uzun ise ve kodun tamamını görmek için yana kaydırma işlemi yapıyorsanız; kodu “…” ile bölüp, devamını alt satıra yazabilirsiniz.

![](/assets/kod/matlab/matlab13.png)
![](/assets/kod/matlab/matlab14.png)

> Daha önceden çalıştırılan programlardan kalan verileri temizlemek için “clc” ve “clear all” komutlarını kullanmayı unutmayalım.

Bir sonraki yazımız [*“klavyeden veri alma”*](https://www.kodlamaogreniyorum.com/matlab-klavyeden-veri-alma/) hakkında olacak.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
