---
layout: post
title: MATLAB ile EKOK ve EBOB Bulma
date: 2020-11-25 02:03:00
description: matlab-ornek-uygulamalar
categories: matlab-ornek-uygulamalar
tags:  
    - ebob
    - ekok
    - gcd 
    - lcm
    - matlab
---

Bu yazımızda, MATLAB kullanarak EKOK(En küçük ortak kat) ve EBOB(En büyük ortak bölen) bulan program oluşturacağız. Oluşturduğumuz program, veri olarak girdiğimiz dizinin bütün elemanları arasında hesaplama yapacak. MATLAB’da bulunan hazır fonksiyonlar ile kolay bir şekilde EKOK veya EBOB hesaplayabiliyoruz ancak hazır fonksiyonlar, hesap yaparken iki elemanı veri olarak almaktadır.  Buna ek olarak programlama bilgimizi geliştirmek için kendimiz EKOK ve EBOB bulan bir program oluşturacağız. Kodlamaya geçelim:

<h1>EKOK:</h1>

```matlab
function ekok = ekok_bul(x)
    for i = 1:prod(x) %Dizinin çarpımı
        if mod(i, x) == 0
            ekok = i;
            fprintf('Ekok: %d\n',ekok);
            break
        end
    end        
end
```

<span >MATLAB Fonksiyonu:</span> `lcm(A, B)`

Hesaplama yapmak istediğimiz sayıların en küçük ortak katı, maksimum o sayıların çarpımına eşittir. Örnek olarak: verilen iki sayı A ve B olmak üzere; A ve B’nin en küçük ortak katı maksimum “A x B”, verilen üç sayı A, B ve C olmak üzere; A, B ve C’nin en küçük ortak katı maksimum “A x B x C” olabilir. Bu yüzden, döngümüz elimizdeki dizinin çarpımına kadar gitmek zorundadır.(2. Satır) En küçük ortak kat olan sayı, dizideki bütün sayılara kalansız bölünür.(3.Satır) Ancak en küçük ortak kat olan sayının katları da dizideki sayılara kalansız bölüneceği için o sayının katlarına geçmeden döngüyü durdurmamız gerekir.(6.Satır)

![](/assets/kod/matlab/matlab67.webp)

![](/assets/kod/matlab/matlab68.webp)

<h1>EBOB:</h1>

```matlab
function ebob = ebob_bul(x)
    for i = max(x):-1:1
        if mod(x, i) == 0
            ebob = i;
            fprintf('Ebob: %d\n',ebob);
            break
        end
    end
end
```

<span >MATLAB Fonksiyonu:</span> `gcd(A, B)`

En büyük ortak bölen sayıyı aradığımız için döngü iterasyonunun büyükten küçüğe doğru olması gerekiyor.(2.Satır) Birden fazla ortak bölen olabileceği için en büyük olanı bulduğumuzda döngüyü sonlandırmamız gerekiyor.(6.Satır)

![](/assets/kod/matlab/matlab69.webp)


![](/assets/kod/matlab/matlab70.webp)

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)