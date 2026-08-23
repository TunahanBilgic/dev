---
layout: post
title: MATLAB “while” Döngüsü
date: 2020-03-16 17:27:00
description: matlab-kosul-ve-donguler
categories: matlab-kosul-ve-donguler
tags: 
    - döngü 
    - while 
    - matlab
---

Bir önceki [yazımızda](https://www.kodlamaogreniyorum.com/matlab-for-dongusu/) “for” döngüsünden bahsetmiştik. Bizim belirlediğimiz sayıda tekrarlama yapan döngü, “for” döngüsü; belirli bir koşul sağlandığı sürece, sürekli tekrarlama yapan döngü ise “while” döngüsü olduğunu belirtmiştik. Bu yazımızda “while” döngüsüne giriş yapacağız.

“while” döngüsü için bir koşul tanımlanır. Bu koşulun değeri “True”(Doğru) olduğu sürece döngü sürekli tekrarlanır. Bu nedenle “while” döngüsüne sonsuz döngü de denilir. Döngünün akış diyagramı(üstüne tıklayarak açabilirsiniz):

![](/assets/kod/matlab/matlab30.webp)

“while” döngüsünün nasıl kullanıldığına geçelim:

```matlab
while %koşul
     %işlemler
end
```
```matlab
a = 1;
while a < 6
    disp(a);
    a = a + 1;
end
```

![](/assets/kod/matlab/matlab31.png)

> * Eğer döngü sonsuz tekrara girdiyse ve program sonlanmıyorsa, “ctrl + c” kısayol tuşuyla programı sonlandırabilirsiniz.

Yukarıda belirttiğimiz gibi, koşulun değeri “True” olduğu sürece “while” döngüsü aktiftir. İkili(binary) sayı tabanında, “True” değerinin karşılığının 1 olduğunu biliyoruz. “while” teriminin yanına direkt 1 yazarak döngüyü aktif edebiliriz:

```matlab
sayac = 1;
while 1
   disp(sayac);
   sayac = sayac + 1;
   if sayac > 5
       break
   end
end
```

![](/assets/kod/matlab/matlab31.png)

> “break” terimi döngüyü durdurmak için kullanılmıştır. İlerleyen zamanlarda, “break” ve “continue” terimleri ile ilgili yazımız olacak.

Bir örnek ile konuyu pekiştirelim. [“if” koşul deyimi yazımızda](https://www.kodlamaogreniyorum.com/matlab-if-kosul-deyimi/) sayı tahmin oyunu yapmıştık. O örnekte kendimiz bir sayı belirliyor, kullanıcıya tek tahmin hakkı sunuyorduk. O örneği, bilgisayarın kendi rastgele sayı belirleyecek ve kullanıcı doğru bilene kadar tahmin etmeye devam edecek şekilde güncelleyelim:

```matlab
%kodlamaogreniyorum.com, 2020
sayi = randi(9); % rastgele sayı oluşturma
tahmin = 10;
while sayi ~= tahmin
    tahmin = input('1-9 Arası Sayı Tahmin Edin: ');
    if sayi ~= tahmin
        fprintf('Yanlış tahmin ettiniz.\n');
    else
        fprintf('Doğru tahmin ettiniz.\n');
    end
end
```

“randi(9)” komutu ile “randi()” fonksiyonunun 1 ile 9 arasında sayı üretmesini sağladık. “while” döngüsünü aktif edebilmek için belirlediğimiz sayı aralığından farklı bir değeri “tahmin” değişkenine atadık. “sayı ~= tahmin” koşulu sayesinde kullanıcı doğru tahminde bulunana kadar döngü tekrarlamaya devam edecektir. Kullanıcının sürekli tahminde bulunabilmesi için “input()” fonksiyonunu döngünün içine yazmayı unutmayalım.

![](/assets/kod/matlab/matlab33.png)

![](/assets/kod/matlab/matlab34.png)

Bu yazımızda “while” döngüsüne kısa bir giriş yapmış olduk. Bir sonraki yazımız “break” ve “continue” terimleri ile ilgili olacak. 

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)