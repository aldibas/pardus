## **Bash Kullanımı**

### **Dosya Adları ve Joker Karakterler -Wildcard Characters-**

</br>

POSIX uyumlu sistemlerde dosya adları;
* **a-zA-Z** harfler,
* **0-9** rakamlar,
* **_ - , .**
karakterlerinden oluşabilir ve en fazla **255** karakter olabilir. POSIX uyumlu olan GNU/Linux dağıtımları için de durum aynıdır. 

Elbette dosya isimlendiriken **boşluk, ?, $, \\** gibi karakterleri de kullanabilirsiniz ancak bu karakterleri içeren dosyaları yönetirken dikkat etmeniz gereken durumlar olabilir. Çünkü bu karakterlerin BASH kabuğunda özel işlevleri bulunur. Örneğin **?** bir joker karakter olup dosya adında herhangi bir karakteri ifade etmek için de kullanılabilir.

>**/** karakteri yol tanımında ayraç olarak kullanıldığından dosya adında kullanılamaz.

<div style="color:red;"> 

>Adı, **Nokta "."** ile başlayan dosyaları listeye dahil etmek için **ls** komutunda **-a** parametresi kullanılmalıdır. Bu dosyalar bir nevi gizli dosyalar olarak adlandırılabilir.

</div>
<br>

``` {.sh}
touch .cok-gizli-dosya
```

``` {.sh}
ls -a
```



<br>

>Dosya isimlerinde büyük/küçük harf duyarlılığı vardır. Örneğin; File, file, filE farklı 3 dosyayı ifade eder.


Şu 3 dosyayı oluşturalım: File, file, filE

</br>

>**touch** komutu bir dosyanın erişim zamanını günceller, ancak dosya yok ise oluşturur.


</br>

``` {.sh}
touch File
```

Önceki konularda değindiğimiz stdout "**>**" ile bir çıktıyı bir dosyaya yazabiliriz.

</br>

``` {.sh}
whoami > file
```

Hata çıktılarını -stderr- "**2>**" ile bir çıktıyı bir dosyaya yazabiliriz. Bu dosya standart çıktının - stdout- yönlendirildiği dosya da olabilir.

``` {.sh}
history >> filE 2>&1
```

Yukarıdaki komutların sonucunda oluşan dosyaları **ls** komutu ile listeleyebiliriz..

``` {.sh}
ls
```

Çıktı:

```{echo}
senol@pardus:~$ ls
file  filE  File
```

Bir GNU/Linux dağıtımında kullandığınız grafik arabirimde dosya uzantıları uygulamalar ile ilişkilendirilmiştir. Örneğin .txt uzantılı bir dosyayı açtığınızda ilişkilendirilmiş uygulama dosya içeriğini görüntüler. Ancak dosyanın türününü içeriği belirler. **file** komutu ile dosyanın türünü görebiliriz.


``` {.sh}
file File
```

Çıktı:

```{echo}
senol@pardus:~$ file File 
File: empty
```
---
``` {.sh}
file File
```

Çıktı:
```{echo}
senol@pardus:~$ file file
file: ASCII text
```

---

<br>

Bir komutun kullanım biçimini incelerken yol tanımından -path- bahsetmiştik. Bu anlatımlarda bir konumdaki bir kaynak dosya üzerinde örnekler yapmıştık. Birden fazla dosya ya da konum üzerinde işlem gerçekleştirmek için dosya/dizin adlarında desen -patern- uygulayabiliriz.



### Patern Uygulama
</br>

>Komutların kullanımında birden fazla dosyayı ifade etmek için dosya isimlerindeki benzerlikler dikkate alınarak joker karakterler **\*, ?** ** ve **.** ile patern -desen- uygulanabilir. 


<br>

>**?** dosya adında tek bir karaktere karşılık gelirken **\*** bir karakter dizisini ifade edebilir. Metin işleme komutlarında desen uygularken tek bir karakteri ifade etmek için **.** kullanacağız.

Örneğin yularıda oluşturduğumuz file,  filE,  File ismindeki dosyalardan sadece **file** ve **filE** dosyalarını herhangi bir komut ile işleme sokmak için "**f***" şeklinde gösterim yeterli olacaktır.

file ve filE dosyalarını listeleyelim:

``` {.sh}
ls f*
```

<br>

Sadece **filE** dosyasını listelemek istersek -elbette direk adını yazabiliriz- "**???E**" desenini kullanabiliriz.

``` {.sh}
ls ???E
```

Aşağıdaki örnekleri inceleyebilirsiniz.


| Desen | |Anlamı |
|:--:|:--:|--|
| s* | » |**s** ile başlayan dosyalar / dizinler |
| *.sh | » |**sh** uzantılı dosyalar |
| ??n* | » | 3. karakteri **n** olan dosyalar / dizinler |
| s*.sh | » | **s** ile başlayıp uzantısı **sh** olan dosyalar |
| \*.\* | » | Uzantıya sahip tüm dosya ve dizinler |
| * | » | **Tüm** dosyalar / dizinler |
| ??? | » | **3** karakterliler |
| \*e* | » | Adında **e** geçen dosyalar dizinler |
| \*e\*n*l | » | Adında önce **e** sonra **n** geçen ve **l** ile biten dosyalar/dizinler |
| [fF]* | » | **f** / **F** ile başlayan dosyalar / dizinler |
| [^fF]* | » | **f** / **F** ile başlamayan dosyalar / dizinler |
| [a-zA-Z]* | » | **harf** ile başlayan dosyalar / dizinler |
| [a-zA-Z0-9]* | » | **harf** ya da **rakam** ile başlayan dosyalar / dizinler |
| ?[a-d]* | » | 2. karakteri **a,b,c,** ya da **d** olan dosyalar / dizinler |
| *[ad] | » | **a** ya da **d** ile biten dosyalar / dizinler |
| ?[0-3] | » | **İki** karakterli ve 2. karakteri **0,1,2** ya da **3** olan dosyalar / dizinler |


<br>

<div style="color:red;"> 

>Dosya isimlerinde ya da desen belirtirken **$, >, \*, ., ], [, }, {, ), (, ), boşluk** gibi bir anlam ifade eden karakterleri  kullamanız gerektiğinde **\\** karakteri ile anlamının dışında  -kendisi- ve hatta anlam yükleyerek kullanabiliriz. 
</div>
<br>

---


Örneğin "**Anadolu pars**" isimli bir dosyayı silmek istediğimizde aşağıdaki gibi bir kullanım var ise **Anadolu** ve **pars** isminde 2 dosyayı silecektir.

``` {.sh}
rm Anadolu pars
```

Çıktı:
```{echo}
senol@pardus:~$ rm Anadolu pars
rm: cannot remove 'Anadolu': No such file or directory
rm: cannot remove 'pars': No such file or directory
```
---

"**Anadolu pars**" isimli dosyayı herhangi bir işleme sokmak için boşluktan önce **\\** karakteri kullanılabilir.


``` {.sh}
rm Anadolu\ pars
```

Çıktı:
```{echo}
test@pardus:~$ rm Anadolu\ pars
rm: cannot remove 'Anadolu pars': No such file or directory
```

---


<br>

>Yine yukarıda belirttiğimiz gibi, komut diziliminde **\*** bir joker karakterdir ve bir karakter dizisini ifade edebilir. Ancak biz çarpma işlemi yapmak isyiyorsak bu karakteri "**\\***" şeklinde kullanmalıyız. 

``` {.sh}
expr 5 \* 5
```
---

>Aşağıdaki gibi bir kullanımda **n** karakteri **\\** karakterinden kaynaklı yeni satır -new line- anlamına gelecektir.

``` {.sh}
echo -e "Merhaba\nDünya"
```

Çıktı:

```{echo}
test@pardus:~$ echo -e "Merhaba\nDünya"
Merhaba
Dünya
```
---


Bu bilgiler doğrultusunda desen örneklerini daha da genişletebiliriz ancak çok geniş bir konu oladuğundan farklı kaynakları araştırmanızda fayda var. Metin işleme konusundaki örneklere de göz atabilirsiniz.





| Desen | | Anlamı |
|:--:|:--:|--|
| ???\\?* | » | **4.** karakteri **?** olan dosyalar / dizinler. |
| ???\\* | » | **4** karakterli ve **4.** karakteri **\*** olan dosyalar / dizinler. |
| [!0-9]* | » | **rakam** ile başlamayan dosyalar / dizinler. |
| ??\\* | » | **3.** karakteri "**\\**" olan dosyalar / dizinler. |


<br>

<div style="color:red;">

>**!** ve **^** eşleşmeyen karakterleri eşleştirir. -**Değil/NOT**-

</div>

<br>

Aşağıdaki komutları uygulayın...

``` {.sh}
ls /dev/tt*
```

``` {.sh}
ls /etc/*.conf /etc/*.cfg
```

``` {.sh}
echo /etc/*.?
```

``` {.sh}
ls -d /etc/*.?
```


``` {.sh}
ls /sys/bus/cpu/devices/cpu[1-4]
```

``` {.sh}
echo /sys/bus/cpu/devices/cpu[1-3]
```

``` {.sh}
touch file{1..10}.txt
```


``` {.sh}
ls
```


``` {.sh}
rm file[1-58].txt
```

Listeleme yapmadan önce üstteki komutun hangi dosyaları sileceğiniz tahmin etmeye çalışın.

``` {.sh}
ls
```

 
 saat:dakika_gün-ay-yıl.png formatında isimlerden oluşan bir fotoğraf albümünde 2013 yılının 10-15 Ağustos aralığında saat akşam 5 ile 6 arasında oluşmuş/çekilmiş dosyaları gösteren paterni -deseni- düşünün.
 Örnek dosya adı : 05:09_30-08-2020.jpg



</br>






Daha detaylı bilgi için "Düzenli İfadeler" -**Regular Expressions**- konusunu inceleyebilirsiniz.





</br>

 [Komut yapısı](./tr_komut-yapisi.md) << Önceki / Sonraki >> [Yardım alma komutları -man-](../yardim-alma-komutlari/tr_komutlar-yardim-alma-komutlari-man-.md)

