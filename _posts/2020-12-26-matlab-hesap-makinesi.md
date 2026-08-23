---
layout: post
title: Matlab Hesap Makinesi Programı
date: 2020-12-26 19:32:00
description: Matlab'da dört işlem yapan hesap makinesi programı
tags: code matlab switch case hesap makinesi
categories: matlab-ornek-uygulamalar
---

Bu yazımızda, MATLAB’da “switch – case” yapısını kullanarak dört işlem yapan hesap makinesi programı oluşturacağız. [Bir önceki yazımızda](https://www.kodlamaogreniyorum.com/matlab-switch-case-yapisi/) “switch – case” yapısını açıklamıştık. Konuda eksiğiniz varsa inceleyebilirsiniz. 

Hesap makineleri, kullanıcı sonlandırana kadar işlem yapmaya devam eder. Bu sebeple “while” döngüsünü kullanacağız. Böylelikle, programımız kullanıcı çıkış yapana kadar hesap yapamaya devam edecek. Programın mantığı zor olmadığı için direkt kodlamaya geçelim:

```matlab
%kodlamaogreniyorum.com, 2020
clear all
clc
fprintf('Basit Hesap Makinesi...\n');
fprintf(['Toplama: "+" veya "topla"\n'...
            'Çıkarma: "-" veya "çıkar"\n'...
            'Çarpma: "*" veya "çarp"\n'...
            'Bölme: "/" veya "böl"\n'...
            'Çıkış: "=" veya "çıkış"\n']);
sayi = input('İşlem yapılacak sayıyı girin: ');
islem = '';
while islem ~= "="
    islem = input('Yapılacak işlemi girin: ','s');
    switch islem
        case {"+", "topla"}
            yeni_sayi = input('İşlem yapılacak sayıyı girin: ');
            sayi = sayi + yeni_sayi;
        case {"-", "çıkar"}
            yeni_sayi = input('İşlem yapılacak sayıyı girin: ');
            sayi = sayi - yeni_sayi;
        case {"*", "çarp"}
            yeni_sayi = input('İşlem yapılacak sayıyı girin: ');
            sayi = sayi * yeni_sayi;
        case {"/", "böl"}
            yeni_sayi = input('İşlem yapılacak sayıyı girin: ');
            sayi = sayi / yeni_sayi;
        case {"=", "çıkış"}
            fprintf('= %g\n',sayi);
            break
        otherwise
            fprintf('Hatali işlem girişi yaptınız.\n');
    end
    fprintf('= %g\n',sayi);
end
```

![](/assets/kod/matlab/matlab77.webp){: style="width: 125%; height: auto;" }

Oluşturduğumuz programda, program hesaplamaya başlamadan önce kullanıcıya işlemler ile ilgili bilgi verdik. Ayrıca yaptığımız ufak eklemeler sayesinde, kullanıcı yapmak istediği işlemi hem operatör(“+”, “-“, “*” veya “/”) aracılığıyla hem de yazarak yapabilme seçeneğine sahip oldu.

Yeni içerikler için sitemizi takip etmeyi unutmayın.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
