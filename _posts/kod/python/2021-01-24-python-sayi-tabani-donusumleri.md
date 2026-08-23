---
layout: post
title: Python Sayı Tabanı Dönüşümleri (Taban Aritmetiği)
date: 2021-01-24 00:59:00
description: python-ornek-uygulamalar
categories: python-ornek-uygulamalar
tags:  
    - taban dönüşüm
    - python
---


Bu yazımızda, Python kullanarak taban aritmetiği yapan programdan oluşturacağız. Biz günlük hayatta onlu(decimal) sayı sistemini kullanırız. Bilgisayarlar ikili(binary) sayı sistemini kullanır. Bu yazımızda, bir başka sayı tabanındaki sayıyı onlu sayı tabanına ve onlu sayı tabanındaki sayıyı bir başka sayı tabanına çeviren programlar yazacağız. Yazacağımız programlar pozitif ve ondalıksız sayılar için olacak. Lafı daha fazla uzatmadan kodlamaya geçelim.

<h1>Başka Bir Sayı Tabanından Onlu Sayı Tabanına Dönüşüm Yapan Python Programı</h1>

Başka bir sayı tabanından onlu sayı tabanına dönüşüm yaparken; sayının basamaklarındaki ifadeler(rakam veya harf olabilir), üssü olan taban ile çarpılır ve bu çarpımların toplamıyla onlu sayı sistemindeki karşılığı bulunur. Örnek olarak, üçlü sayı tabanında verilen 21 sayısını onlu sayı tabanına dönüşümü:

$$
(21)_3 = 2 \times 3^1 + 1 \times 3^0, \quad (21)_3 = 7 \text{ şeklindedir.}
$$

Tabanın üssü; son basamaktan itibaren, 0’dan başlayarak birer birer artmaktadır. Ayrıca dikkat edilmesi gereken bir başka kısım ise, sayının basamağındaki rakamlar tabandan büyük olamaz. Kodumuzu bu konulara dikkat ederek oluşturacağız. Kodlamaya geçelim:

```python
# kodlamaogreniyorum.com, 2021
def onlutabanaçevir(sayı, taban):
    alt = str.maketrans("0123456789", "₀₁₂₃₄₅₆₇₈₉")
    sayı = abs(int(sayı))
    taban = abs(int(taban))
    sayı = str(sayı)
    if (all(int(i) < taban for i in sayı)) and 1 < taban < 10:
        çevrilmiş_sayı = 0
        üs = 0
        for i in reversed(sayı):
            çevrilmiş_sayı += int(i) * taban ** üs
            üs += 1
        print("(%s)%s = %d\n" % (sayı, str(taban).translate(alt), çevrilmiş_sayı))
    else:
        print('Girdiğiniz sayı ile taban uyumsuz!\n')
```

3.satırda yazdığımız `“alt = str.maketrans("0123456789", "₀₁₂₃₄₅₆₇₈₉")”` komutunu; ekrana çıktı yazdırırken, tabanın alt karakter olarak gelmesi için kullandık. 4. ve 5. satırda yazdığımız ifadeler ile hatalı sayı veya taban girilmesini önlemiş olduk. 7. satırdaki “(all(int(i) < taban for i in sayı))” koşulu, sayının basamaklarındaki rakamların tabandan küçük olmasını garanti eder. `“for i in reversed(sayı):”` döngüsündeki “i”, sayının son basamağından başlayarak, her basamaktaki rakamları ifade etmektedir.

![](/assets/kod/python/python67.webp)

<h1>Onlu Sayı Tabanından Bir Başka Sayı Tabanına Dönüşüm Yapan Python Programı</h1>


Onlu sayı tabanından bir başka sayı tabanına dönüşüm yapmak için; sayı, tabandan küçük kalıncaya kadar sürekli olarak tabana bölünür. Bu işlem sonrasında, ilk olarak bölüm ve sondan başa olacak sırayla tüm kalanlar soldan sağa doğru yazılarak yeni sayı bulunur. Örnek olarak, 137 sayının altılı sayı tabanına dönüşümü:

$$
137 = (x)_6
$$

$$
\frac{137}{6} = 22 \quad \text{Kalan: } \textcolor{orange}{5}
$$

$$
\frac{22}{6} = \textcolor{blue}{3} \quad \text{Kalan: } \textcolor{orange}{4}
$$

$$
137 = (345)_6 \text{ şeklindedir.}
$$

```python
# kodlamaogreniyorum.com, 2021
def tabandeğiştir(sayı, taban):
    alt = str.maketrans("0123456789", "₀₁₂₃₄₅₆₇₈₉")
    taban = int(taban)
    if 1 < taban < 10:
        sayı = abs(int(sayı))
        sayı2 = sayı
        çevrilmiş_sayı = []
        while sayı >= taban:
            kalan = sayı % taban
            sayı = int(sayı / taban)
            çevrilmiş_sayı.insert(0, str(kalan))
            if sayı < taban:
                çevrilmiş_sayı.insert(0, str(sayı))
        çevrilmiş_sayı = "".join(çevrilmiş_sayı)
        print("%d = (%s)%s\n" % (sayı2, çevrilmiş_sayı, str(taban).translate(alt)))
    else:
        print('Tabanı kontrol edin!\n')
```

 3.satırda yazdığımız “alt = str.maketrans("0123456789", "₀₁₂₃₄₅₆₇₈₉")” komutunu; ekrana çıktı yazdırırken, tabanın alt karakter olarak gelmesi için kullandık. 4. ve 6. satırda yazdığımız ifadeler ile hatalı sayı veya taban girilmesini önlemiş olduk. “while sayı >= taban:” ifadesi ile döngünün, sayı tabandan küçük kalıncaya kadar devam etmesini sağladık. “çevrilmiş_sayı.insert(0, str(kalan))” ifadesi ile sondan başa ekleme yapmayı sağladık. “çevrilmiş_sayı = "".join(çevrilmiş_sayı)” ifadesi ile “çevrilmiş_sayı” değişkenini liste olmaktan çıkardık.       

![](/assets/kod/python/python68.webp)

Bütün **Python kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github Python](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/python)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)
