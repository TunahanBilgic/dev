---
layout: post
title: MATLAB Rastgele Sayı Üretme (rand, randi, randn)
date: 2020-12-12 20:25:00
description: matlab-fonksiyonlar
categories: matlab-fonksiyonlar
tags: 
    - fonksiyon 
    - gömülü fonksiyonlar 
    - rastgele sayı üretme
    - matlab
---

Bu yazımızda MATLAB’da bulunan gömülü fonksiyonlara giriş yapacağız. Gömülü fonksiyonlar, bize programlama yaparken büyük kolaylıklar sağlarlar. Örneğin bir dizinin en büyük elemanını bulmak için döngülerle, kodlarla uğraşmadan tek komut ile sonuca ulaşabiliriz. Bu yazımızda, rastgele sayı üreten gömülü fonksiyonları inceleyeceğiz. Kullanacağımız fonksiyonlar:

* “rand()”: Uniform(düzgün, tekdüze) dağılmış sayı üretmek için
* “randi()”: Uniform(düzgün, tekdüze) dağılmış tam sayı üretmek için
* “randn()”: Normal dağılmış sayı üretmek için
* “randperm(n)”: 1 – n arası tam sayıların permütasyonu için

<h1>“rand()” Fonksiyonu</h1>

0 ile 1 arasında, NxN uniform sayılar üretmek için:

```matlab
%Syntax: rand(N)
rand(3)
```

![](/assets/kod/matlab/matlab38.webp)

0 ile 1 arasında, MxN uniform sayılar üretmek için:

```matlab
%Syntax: rand(M,N)
rand(2,5) %2x5
```
![](/assets/kod/matlab/matlab39.png)

Belirli bir aralıktaki sayılardan, belirli adet rastgele sayı üretmek istiyorsak; “a” aralığın başlangıç sayısı, “b” aralığın bitiş sayısı olmak üzere, “a + (b–a) * rand(M,N)” formülünü kullanırız. Örnek olarak, -10 ile 10 arasında “2×5” matris olacak şekilde sayı üretmek istiyorsak: “-10 + (10 – (-10)) * rand(2,5)” komutunu kullanmalıyız.

```matlab
%Syntax: a + (b-a) * rand(M,N)
-10 + (10+10) * rand(2,5) %-10, 10 arasında 2x5
```

![](/assets/kod/matlab/matlab40.webp)

Gerçek ve sanal kısmı 0 ile 1 arasında normal dağılmış karmaşık sayı üretme:

```matlab
%Syntax: rand + 1i * rand
rand + 1i * rand
```

![](/assets/kod/matlab/matlab41.webp)

<h1>“randi()” Fonksiyonu</h1>

1 ile N arasında, rastgele bir tam sayı üretmek için:

```matlab
%Syntax: randi(N)
randi(7)
```

![](/assets/kod/matlab/matlab42.webp)

1 ile N arasında, MxM uniform tam sayılar üretmek için:

```matlab
%Syntax: randi(N,M)
randi(7,3) %1-7 arası, 3x3
```

![](/assets/kod/matlab/matlab43.webp)

a ile b arasında, MxN uniform tam sayılar üretmek için:

```matlab
%Syntax: randi([a b], M, N)
randi([-10 10], 2, 5) %-10 ile 10 arası, 2x5
```

![](/assets/kod/matlab/matlab44.png)

<h1>“randn()” Fonksiyonu</h1>

NxN normal dağılmış rastgele sayılar üretmek için:

```matlab
%Syntax: randn(N)
randn(3) %3x3
```

![](/assets/kod/matlab/matlab45.webp)


MxN normal dağılmış rastgele sayılar üretmek için:

```matlab
%Syntax: randn(M,N)
randn(2,5) %2x5
```

![](/assets/kod/matlab/matlab46.png)

Gerçek ve sanal kısmı normal dağılmış karmaşık sayı üretme:

```matlab
%Syntax: randn + 1i*randn
randn + 1i*randn
```

![](/assets/kod/matlab/matlab47.webp)

<h1>“randperm()” Fonksiyonu</h1>

“randperm()” fonksiyonu, 1 ile bizim belirlediğimiz “N” aralıktaki tam sayıların rastgele permütasyonunu verir. 

```matlab
%Syntax: randperm(N)
randperm(5) % 1 ile 5 arası sayıların permütasyonu
randperm(5) % 1 ile 5 arası sayıların permütasyonu 2
```

![](/assets/kod/matlab/matlab48.webp)


1 ile N arası tam sayıların M tanesinin permütasyonu için:

```matlab
%Syntax: randperm(N)
randperm(5) % 1 ile 5 arası sayıların permütasyonu
randperm(5) % 1 ile 5 arası sayıların permütasyonu 2
```

![](/assets/kod/matlab/matlab49.png)


<h1>“rng()” Fonksiyonu</h1>

Rastgele sayı üretilirken, başlangıç olarak bir sayı seçilir. Rastgele sayı üretecinin başlangıç sayısını kontrol ederek, rastgele sayı üretirken aynı sonuçları alabiliriz:

```matlab
b_s = rng;
randperm(5) %1-5 arası tam sayıların rastgele permütasyonu
rng(b_s)
randperm(5) %Aynı sonuç
```

![](/assets/kod/matlab/matlab50.webp)


Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)