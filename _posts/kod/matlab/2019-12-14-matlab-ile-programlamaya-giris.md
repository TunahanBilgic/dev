---
title: Matlab ile Programlamaya Giriş
date: 2019-12-14 07:50:00
description: Matlab Temel Bilgiler
categories: matlab-temel-bilgiler
tags: 
    - disp 
    - fprintf 
    - komut penceresi
    - matlab
    - yazi yazdirma
---

Bu yazımızda MATLAB ile programlamaya giriş yapacağız. Ancak bu yazının amacı programlama mantığını anlatmak olmayacak. Ama ilerleyen zamanlarda programlama mantığı ve program oluşturulurken kullanılan akış diyagramları ile ilgili yazımız olacak.

Öncelikle MATLAB ile etkileşim kurduğumuz bileşen olan komut penceresinden (command window) bahsedeceğiz. Komut penceresinin işlevlerine; sayısal hesaplamalar yapabilme, program yazıp çalıştırabilme, daha önceden kaydedilmiş olan fonksiyonları kullanarak çıktı alabilme gibi örnekler verilebilir.

![](/assets/kod/matlab/matlab1.png)

> **Not:** Bir değişken tanımlamadan yapılan işlemler MATLAB tarafından otomatik olarak “ans” isimli değişkene kaydedilir. Değişken tanımlamayı önümüzdeki yazımızda yapacağız.

Bazen yazdığımız kodların yanına not düşmek isteriz. Bunun için “%” operatörü kullanılır.

```matlab
5+5 %toplama işlemi
1520-9 %çıkarma işlemi
1993/3 %bölme işlemi
3*3 %çarpma işlemi
8^2 %üs alma
```
![](/assets/kod/matlab/matlab2.png)

> **Not:** Komut pencereniz çok dolduysa eğer “clc” komutu ile temizleyebilirsiniz.

<h1>Ekrana Bilgi Yazdıralım!</h1>
Ekrana yazı yazdırmak için genellikle "fprintf()" ve "disp()" komutları kullanılır.

> Kullanılan bir diğer komut olan “sprintf()” komutundan ilerleyen zamanlarda bahsedeceğiz.

Bu komutlar:
```matlab
disp('Yazdırılacak Yazı');
fprintf('Yazdırılacak Yazı');
```
şeklinde kullanılır.

> MATLAB’da her satır sonuna “;” konulur. Bunu unutmamaya özen gösterelim. Komut penceresinde kullanmadığımız takdirde satırda yazan ifadenin değeri ekrana gelir. Değişken tanımlama yazımızı inceledikten sonra, komut penceresinde “x = 5” ile “x = 5;” arasındaki farkı inceleyebilirsiniz.

Komut penceresine aşağıdaki kodları girelim ve çıktılarımızı inceleyelim.

```matlab
disp('Hello, World!');
```
![](/assets/kod/matlab/matlab3.png)


```matlab
fprintf('Hello, World!');
```

![](/assets/kod/matlab/matlab4.png)

Dikkat ettiyseniz eğer “disp()” komutu ile kullanımda imleç bir sonraki satıra geçmişken, “fprintf()” komutu ile kullanımda imleç aynı satırda kalmıştır. Çünkü “fprintf()” komutu, imleci soldan sağa birim birim kaydırmakta ve iki tırnak(‘ ‘) içerisinde bulunan her şeyi karakter karakter ekrana basmaktadır. Yazdırılan yazıların konumlarını ayarlamak veya imleci bir sonraki satıra geçirmek istenirse eğer kaçış operatörleri kullanılması gerekir.

```matlab
\t : %İmleci bir TAB sağa kaydırır.
\n : %İmleci bir sonraki satırın başına götürür.
```
![](/assets/kod/matlab/matlab5.png)

Bir sonraki yazımız [*“değişken tanımlama ve ekrana yazdırma”*](https://www.kodlamaogreniyorum.com/matlabda-degisken-tanimlama/) hakkında olacak.

Bütün **MATLAB kodlarına** Github sayfam aracılığı ile erişebilirsiniz. Github sayfamın linkine aşağıdan ulaşabilirsiniz. Görüşmek üzere!

Github: [Github MATLAB](https://github.com/TunahanBilgic/kodlamaogreniyorum/tree/main/matlab)

Sitemize destek olmak isteyen sponsorlar için link: [Patreon](https://patreon.com/tunahanbilgic)