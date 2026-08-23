---
layout: post
title: Python Hesap Makinesi Programı
date: 2021-01-22 09:58:00
description: Python'da “while” döngüsünü ve “if-elif” koşul deyimini kullanarak dört işlem yapan hesap makinesi programı
categories: python-ornek-uygulamalar
tags: code python hesap makinesi

---

Bu yazımızda, Python’da [“while” döngüsünü](https://www.kodlamaogreniyorum.com/python-while-dongusu/) ve [“if-elif” koşul deyimini](https://www.kodlamaogreniyorum.com/python-if-kosul-deyimi/) kullanarak dört işlem yapan hesap makinesi programı oluşturacağız. Daha önceki yazılarda bu yapıları açıklamıştık. Konuda eksiğiniz varsa inceleyebilirsiniz. 

Hesap makineleri, kullanıcı sonlandırana kadar işlem yapmaya devam eder. Bu sebeple [“while” döngüsünü](https://www.kodlamaogreniyorum.com/python-while-dongusu/) kullanacağız. Böylelikle, programımız kullanıcı çıkış yapana kadar hesap yapamaya devam edecek. Programın mantığı zor olmadığı için direkt kodlamaya geçelim:

```python
# kodlamaogreniyorum.com,2021
print("Basit Hesap Makinesi..\n")
print("Toplama: '+' veya 'topla'\n"
      "Çıkarma: '-' veya 'çıkar'\n"
      "Çarpma: '*' veya 'çarp'\n"
      "Bölme: '/' veya 'böl'\n"
      "Çıkış: '=' veya 'çıkış'\n")
sayı = int(input('İşlem Yapılacak Sayı: '))
while True:
    işlem = input('Yapılacak İşlem: ')
    if işlem == '+' or işlem.lower() == 'topla':
        yeni_sayı = float(input('İşlem Yapılacak Sayı: '))
        sayı += yeni_sayı
    elif işlem == '-' or işlem.lower() == 'çıkar':
        yeni_sayı = float(input('İşlem Yapılacak Sayı: '))
        sayı -= yeni_sayı
    elif işlem == '*' or işlem.lower() == 'çarp':
        yeni_sayı = float(input('İşlem Yapılacak Sayı: '))
        sayı *= yeni_sayı
    elif işlem == '/' or işlem.lower() == 'böl':
        yeni_sayı = float(input('İşlem Yapılacak Sayı: '))
        sayı /= yeni_sayı
    elif işlem == '=' or işlem.lower() == 'çıkış':
        print('= %g\n' % sayı)
        break
    else:
        print('Hatalı giriş yaptınız.\n')
    print('= %g\n' % sayı)
```
![](/assets/kod/python/python62.png)


Oluşturduğumuz programda, program hesaplamaya başlamadan önce kullanıcıya işlemler ile ilgili bilgi verdik. Ayrıca yaptığımız ufak eklemeler sayesinde, kullanıcı yapmak istediği işlemi hem operatör(“+”, “-“, “*” veya “/”) aracılığıyla hem de yazarak yapabilme seçeneğine sahip oldu. Ayrıca “lower()” fonksiyonu sayesinde büyük/küçük harf hatalarından kurtulmuş olduk.

Yeni içerikler için sitemizi takip etmeyi unutmayın.

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)