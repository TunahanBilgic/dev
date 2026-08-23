---
layout: post
title: MATLAB “for” Döngüsü
date: 2020-02-20 07:26:00
description: matlab-kosul-ve-donguler
categories: matlab-kosul-ve-donguler
tags: 
    - döngü 
    - for 
    - matlab
---

Yazdığımız programda tekrarlı işlemler bulunuyorsa döngü kullanmamız gerekir. Döngüler; belirlediğimiz sayıda veya sürekli( belirli bir koşul sağlandığı sürece ) tekrarlama deyimleridir. Bizim belirlediğimiz sayıda tekrarlama yapan döngü, “for” döngüsü; belirli bir koşul sağlandığı sürece, sürekli tekrarlama yapan döngü ise “while” döngüsüdür. Biz bu yazımızda “for” döngüsüne giriş yapacağız.

“for” döngüsünde tekrarlama sayısını kendimiz belirleriz. “for” döngüsü, kendimizin belirlediği sayıda tekrarlı işlem yapmamızı sağlar. Ancak “for” döngüsünün bize yardımcı olduğu çok daha önemli bir özelliği vardır. “for” döngüsü bize bir dizinin elemanları arasında dolaşmamız konusunda büyük kolaylıklar sağlar. Döngünün akış diyagramı(üstüne tıklayarak açabilirsiniz):

![](/assets/kod/matlab/matlab23.webp)

Daha önce belirttiğimiz gibi, döngünün tekrar sayısını biz belirliyoruz. Döngüye, bir başlangıç değeri ve bitiş değeri tanımlanır. Başlangıç değerinden, bitiş değerine kaç adımda ulaştığımız döngünün tekrar sayısını verir. Bu adımlarının büyüklüğünü( artış veya azalış miktarı ) kendimiz belirleyerek döngünün tekrar sayısını ortaya çıkarmış oluruz. Bunu döngü değişkeni( iterasyon değişkeni ) aracılığıyla yaparız. Döngü değişkeni, döngüye özel olarak kullanıcı tarafından tanımlanan değişkenlerdir. Döngü değişkeni, başlangıç değerinden artarak veya azalarak bitiş değerine ulaşır. Böylelikle döngü tamamlanmış olur. Örnek olarak, döngünün başlangıç değeri 1, bitiş değeri 5 ve adım büyüklüğümüz(artış miktarı) 1 olsun. Döngü, 1’den 5’e toplamda beş adımda tamamlanacaktır. MATLAB’da adım büyüklüğünün varsayılan değeri 1’dir. Varsayılan değer kullanılacaksa döngü yazılırken belirtmeye ihtiyaç yoktur. “for” döngüsüne kısa bir giriş yaptıktan sonra artık “for” döngüsünün nasıl kullanıldığına geçelim:
> Döngülerin her bir adımı iterasyon olarak adlandırılır.

```matlab
for (%döngü değişkeni)= (%baş. değeri) : (%adım büyük.) : (%bit. değeri)
     %işlemler
end
```
```matlab
for i=1:5 %varsayılan değeri yazmamıza gerek yok
    disp(i);
end
```
![](/assets/kod/matlab/matlab24.png)

```matlab
%Adım büyüklüğünü 2 yapalım.
for i=1:2:5
    disp(i);
end
```
![](/assets/kod/matlab/matlab25.png)


```matlab
%azalan miktara örnek
for i=5:-1:1
    disp(i);
end
```
![](/assets/kod/matlab/matlab26.png)

Bir dizinin elemanları arasında dolaşmak için döngü değişkenini, dizinin indisi olarak tanımlıyoruz :
```matlab
dizi = [1 10 35 93 6];
for i=1:5
    disp(dizi(i));
end
```
![](/assets/kod/matlab/matlab27.png)

Dizinin eleman sayısı değişiyorsa veya kesin olarak bilinmiyorsa “length()” fonksiyonundan faydalanabiliriz. “length()” fonksiyonu bir dizinin en büyük* boyutunu verir.
> * length() fonksiyonu, “mxn” boyutundaki bir matrisin satır(m) veya sütun(n) boyutlarından hangisi daha büyükse onu değer olarak verir.

```matlab
dizi = [1 10 35 93 6];
for i=1:length(dizi)
    disp(dizi(i));
end
```
“for” döngüsü ile dizinin elemanlarına erişmenin bir diğer yolu ise başlangıç ve bitiş değeri yazmak yerine direkt diziyi yazmaktır:

```matlab
dizi = [1 10 35 93 6];
for i=dizi
    disp(i);
end
```

Bir örnek ile yazımızı sonlandıralım. Örneğimiz; kullanıcının belirlediği aralıktaki tek ve çift sayıları bulup, onları iki ayrı dizide saklayan bir program olsun. Örneğimizde “mod()” fonksiyonundan yararlanacağız. “mod()” fonksiyonu, bölme işleminden kalan sayısı veren MATLAB yerleşik fonksiyonudur. Kodlamaya geçelim:

```matlab
bas=input('Başlangıç Değeri: ');
bit=input('Bitiş Değeri: ');
tek_sayilar=[];    %tek sayılar için boş dizi
cift_sayilar=[];   %çift sayılar için boş dizi
for i=bas:bit
    if mod(i,2)==0 %eğer 2'ye bölümden kalan yoksa çifttir.
        cift_sayilar=[cift_sayilar i]; %diziye mevcut sayıyı ekleme
    else           
        tek_sayilar=[tek_sayilar i];
    end
end
tek_sayilar
cift_sayilar
```
![](/assets/kod/matlab/matlab28.png)

![](/assets/kod/matlab/matlab29.png)



“for” döngüsü bizim belirlediğimiz sayıda tekrar eden bir döngüdür. Ancak “inf” özel terimi ile sonsuz sayıda tekrar eden döngüye dönüşebilmektedir.

Bu yazı için şimdilik bu kadarının yeterli olduğunu düşünüyorum. İlerleyen zamanlarda, “continue” ,”break” ve “inf” terimleri ile ilgili yazımız olacak.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)