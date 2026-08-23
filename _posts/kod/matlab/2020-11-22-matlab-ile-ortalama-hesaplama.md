---
layout: post
title: MATLAB ile Ortalama Hesaplama (Aritmetik, Geometrik, Harmonik)
date: 2020-11-22 19:33:00
description: matlab-ornek-uygulamalar
categories: matlab-ornek-uygulamalar
tags:  
    - aritmetik
    - geometrik
    - harmonik 
    - ortalama
    - matlab
---


Bu yazımızda MATLAB kullanarak ortalama hesaplayan program oluşturacağız. Oluşturduğumuz program, veri olarak girilen dizinin aritmetik, geometrik ve harmonik ortalamasını hesaplayacak. MATLAB’da bulunan hazır fonksiyonlar ile kolay bir şekilde bu ortalamaları hesaplayabiliyoruz ancak programlama bilgimizi geliştirmek için kendimiz bu hesaplamaları yapan bir program oluşturacağız.


# Aritmetik Ortalama:

$$
\bar{x} = \frac{1}{n} \sum_{i=1}^n x_i = \frac{1}{n}(x_1 + \cdots + x_n)
$$


<span style="color: red;">MATLAB Fonksiyonu:</span> `mean(x)`

```matlab
% Aritmetik Ortalama:
arit = 0;
for i = 1:length(x)
    arit = arit + x(i);
end
arit = arit / length(x);
```

# Geometrik Ortalama:

$$
\left( \prod_{i=1}^n x_i \right)^{1/n} = \sqrt[n]{x_1 \cdot x_2 \cdots x_n}
$$

<span style="color: red;">MATLAB Fonksiyonu:</span> `geomean(x)`

```matlab
% Geometrik Ortalama:
geo = x(1);
for i = 2:length(x)
    geo = geo * x(i);
end
geo = geo^(1 / length(x));
```

# Harmonik Ortalama:

$$
\frac{n}{\frac{1}{x_1} + \frac{1}{x_2} + \cdots + \frac{1}{x_n}}
$$

<span style="color: red;">MATLAB Fonksiyonu:</span> `harmmean(x)`

```matlab
% Harmonik Ortalama:
harm = 1 / x(1);
for i = 2:length(x)
    harm = harm + (1 / x(i));
end
harm = length(x) / harm;
```

Yazdığımız kodları tek bir fonksiyon altında toplayıp, “fprintf()” komutu ile ekrana bilgi olarak yazdıralım:

```matlab
%kodlamaogreniyorum.com, 2020
function [arit, geo, harm] = ortalama(x)
    %Aritmetik Ortalama:
    arit = 0;
    for i = 1:length(x) 
        arit = arit + x(i);
    end
    arit = arit / length(x);

    %Geometrik Ortalama:
    geo = x(1);
    for i = 2:length(x)
        geo = geo * x(i);
    end
    geo = geo^(1 / length(x));

    %Harmonik Ortalama:
    harm = 1 / x(1);
    for i = 2:length(x)
        harm = harm + (1 / x(i));
    end
    harm = length(x) / harm;

    fprintf(['Aritmetik Ortalaması: %f\n',...
             'Geometrik Ortalaması: %f\n',...
             'Harmonik Ortalaması: %f\n'],arit,geo,harm);
end
```
![](/assets/kod/matlab/matlab65.webp)

![](/assets/kod/matlab/matlab66.webp)

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)

