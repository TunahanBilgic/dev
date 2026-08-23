---
layout: post
title: MATLAB Klavyeden Veri Alma
date: 2019-12-21 17:24:00
description: matlab-temel-bilgiler
categories: matlab-temel-bilgiler
tags: 
    - input 
    - klavyeden veri 
    - matlab
---

Bir bilgisayar programında kullanılacak verileri hep kendimiz belirlemeyiz. Bu verileri, kullanıcının anlık olarak  girmesini veya bir veri tabanından aktarmayı isteyebiliriz. Bu yazımızda kullanıcıdan klavye aracılığıyla veri almaya değineceğiz.

Bundan önceki yazılarımızda,  yazdığımız programlarda kullanılacak verileri değişkenlere atamıştık. Klavyeden veri alırken de aynı mantıkla veriyi bir değişkene atayacağız. Klavyeden veri almak için “input()” komutu kullanılır. “input()” komutu ile hem sayısal hem de sözel(karakter, dizi) veri alınabilir. Ancak “input()” komutunun varsayılan ayarı, kullanıcının sayısal değer gireceği şeklindedir. Kullanıcıdan sözel veri almak istiyorsak, ‘s‘ ifadesi ile programa belirtmemiz gerekir. “input()” komutunun kullanımları şu şekildedir:

```matlab
%DEĞİŞKEN İSMİ = input('Kullanıcıya gösterilecek yazı');
yas = input('Yaşınızı girin: ');          %Sayısal Veri Alma
isim = input('isminizi girin: ','s');     %Sözel Veri Alma
```
> MATLAB’da komut yazarken otomatik tamamlama özelliği bulunmaktadır. “TAB” tuşu ile bu özelliği kullanırız. Örnek olarak; “fprinf()” komutu yazmak istiyorsak, “fpr” yazıp “TAB” tuşuna basarsak MATLAB otomatik olarak komutu tamamlayacaktır.
Örnek uygulama olarak kullanıcının yaşını hesaplatan bir program yazalım. Kullanıcıdan isim ve doğum yılı bilgisini alalım ve yaşını hesaplatalım. Bir adet “fprintf()” komutu kullanarak, bu bilgilerin her birini ayrı satırlara yazdıralım. 
```matlab
isim = input('İsminizi Girin: ','s');
dogum_yili = input('Doğum Yılınızı Girin: ');
mevcut_yil = 2019; %Yaş hesaplatmak için bulunduğumuz yılı tanımlıyoruz.
fprintf('İsminiz: %s\nDoğum Yılınız: %d\nSayın %s %d yaşındasınız.\n',isim,dogum_yili,isim,mevcut_yil-dogum_yili);                                     
```
![](/assets/kod/matlab/matlab15.webp)

> Bir önceki yazımızda (MATLAB Komut Dosyaları), “…” ifadesinin kodu alt satırdan devam ettirmeye yaradığından bahsetmiştik.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)