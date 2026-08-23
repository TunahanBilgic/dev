---
layout: post
title: MATLAB Seçerek Sıralama (Selection Sorting) Algoritması
date: 2020-01-07 02:50:00
description: matlab-algoritmalar
categories: matlab-algoritmalar
tags: 
    - matlab algoritmalar 
    - seçerek sıralama 
    - selection sorting
    - matlab
---

Bu yazımızda, bir [Sıralama algoritması](https://www.kodlamaogreniyorum.com/matlab-algoritmalar/) olan “Seçerek Sıralama” (Selection Sorting) algoritmasına değineceğiz. Seçerek Sıralama algoritmasını diziyi küçükten büyüğe sıralamak için kullanacağız.

Seçerek Sıralama algoritmasının işleyişi; dizideki en küçük elemanı ilk sıraya yerleştirir, kalanlardan en küçük olanı da ikinci sıraya yerleştirir.Bir eleman kalana kadar bu şekilde devam eder.

[Buradaki bağlantıya](https://www.toptal.com/developers/sorting-algorithms) tıklayarak, sıralama algoritmalarının çalışma şekillerine ait animasyona bakabilirsiniz.

!["Kaynak: Vikipedi"](/assets/kod/matlab/matlab51.gif) Görsel Kaynak:Vikipedi

Örnek olarak, “a” isimli dizinin adım adım küçükten büyüğe sıralanması:

```matlab
a = [3 4 1 1000 -1 25 35 111];
```

[<span style="background-color: yellow;">3</span>, 4, 1, 1000, <span style="color: red;">-1</span>, 25, 35, 111]

[-1, <span style="background-color: yellow;">4</span>, <span style="color: red;">1</span>, 1000, 3, 25, 35, 111]

[-1, 1, <span style="background-color: yellow;">4</span>, 1000, <span style="color: red;">3</span>, 25, 35, 111]

[-1, 1, 3, <span style="background-color: yellow;">1000</span>, <span style="color: red;">4</span>, 25, 35, 111]

[-1, 1, 3, 4, <span style="background-color: yellow;">1000</span>, <span style="color: red;">25</span>, 35, 111]

[-1, 1, 3, 4, 25, <span style="background-color: yellow;">1000</span>, <span style="color: red;">35</span>, 111]

[-1, 1, 3, 4, 25, 35, <span style="background-color: yellow;">1000</span>, <span style="color: red;">111</span>]

[-1, 1, 3, 4, 25, 35, 111, <span style="background-color: yellow;">1000</span>]

Algoritmanın kodları:

```matlab
function sirali_vektor = secerek_sirala(Vektor)
 for i=1:length(Vektor)-1
    enk = Vektor(i);
    enk_indis = i;
    for j=i+1:length(Vektor)
        if Vektor(j) < enk
            enk = Vektor(j);
            enk_indis = j;
        end         
    end 
    depo = Vektor(i);
    Vektor(i) = Vektor(enk_indis);
    Vektor(enk_indis) = depo;    
 end
 sirali_vektor = Vektor;
end
```

İlk döngü ( i ) en küçük elemanın atanacağı indisi temsil ediyor. İkinci döngüyü ( j ) ise en küçük elemanı bulma amacıyla kullanıyoruz. Dolayısıyla ikinci döngüyü, ilk döngünün bulunduğu yerden bir sonraki sıradan başlatmamız gerekiyor. (for j=i+1) Algoritma son elemanda biteceği ve ikinci döngü, ilk döngüden bir sonraki sıradan başladığı için; ilk döngünün bitiş değeri, “a” dizisinin boyutundan bir eksik olması gerekiyor. Dizinin elemanlarının yerlerini değiştireceğimiz için bir saklama değişkeni(depo) kullanıyoruz. Programın ekran görüntüsü:

![](/assets/kod/matlab/matlab52.png)

> Fonksiyonun adı ile Script(“.m”) dosyasının adının aynı olması gerektiğini unutmayalım.

Algoritmayı kullanmak için komut penceresine:

```matlab
secerek_sirala([%Sıralanmasını istediğiniz dizi])
```

![](/assets/kod/matlab/matlab53.webp)

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)

Kaynak: [Carnegie Mellon University, School of Computer Science](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Sorting%20Algorithms/sorting.html)