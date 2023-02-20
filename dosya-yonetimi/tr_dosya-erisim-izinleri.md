# **Terminal & Kabuk -Shell- Komutları**

## Dosya Yönetimi

### **Dosya Erişim İzinleri**


Linux yetkilendirme modeli, UNIX ve BSD’den alınmıştır. 
Bir dosyanın erişim izinlerinden kasıt dosya üzerinde;
* okuyabilme,
* değiştirebilme,
* çalıştırabilme
işlemlerini gerçekleştirebilme yetkilerinini olup olmamasıdır. Bu yetkiler, dosyanın sahibi, grup ve diğer kullanıcılar arasında farklılık gösterir.

Daha önce **ls** komutunda "**l**" parametresi ile dosyaları **detaylı** listelediğimizde aldığımız çıktıyı aşağıdaki gibi açıklamıştık.


``` {.sh}
ls -l 
```


``` {echo}
total 8
-rw-r--r-- 1 senol senol  207 Feb 20 11:19 bellek
lrwxrwxrwx 1 senol senol    4 Feb 20 11:19 dosya -> file
-rw-r--r-- 1 senol guest    0 Feb 20 11:19 dosya.txt
-rw-r--r-- 1 senol senol    0 Feb 20 11:19 file
drwxr-xr-x 2 senol senol 4096 Feb 20 11:19 Pardus
```
</br>

"**l**" seçeneği ile alınan çıktıda sırasıyla;

Dosyanın;
* türü,
* erişim izinleri,
* bağlantı sayısı,
* sahibi,
* grubu,
* boyutu,
* erişim zamanı,
* adı

bilgileri listelenir.

Örnek:

drwxr-xr-x 2 senol senol 4096 Feb 20 14:54 Pardus


| d | rwxr-xr-x | 2 | senol | senol | 4096 | Feb 20 14:54 | Pardus |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|tür|izinler|link|sahip|grup|boyut|zaman|isim|
||

**Tür:** 
</br>
* "**-**" : Normal dosya
* "**d**" : Directory (dizin)
* "**l**" : Symbolic link (sembolik bağ)
* "**c**" : Character special device (karakter aygıt)
* "**b**" : Block special device (blok aygıt)
* "**p**" : Fifo -Pipe file-
* "**s**" : Socket

**İzinler:** rwxr-xr-x


* **r** : Read -okuma-
* **w** : Write -yazma- 
* **x** : eXecute -çalıştırma- 
* **s** : SUID -Set User ID- / SGID -Set Group ID-
* **t** : Sticky Bit

İzinler kısmında 9 karakterden oluşan "**rwxr-xr-x**" gibi bir veri görüyoruz. 

Bu veri, 3'er li gruplar hailinde;

* sahibinin,
* aynı gruptaki kullanıcıların,
* diğer kullanıcıların

dosya üzerindeki haklarını gösterir.

</br>

"**rwxr-xr-x**" izinlerini örnekleyelim:


| rwx | r-x | r-x | 
|:--:|:--:|:--:|
| sahibi / user -owner-| grubu -group | diğer -others-|
|**okuyabilir, yazabilir, çalıştırabilir** | **okuyabilir, çalıştırabilir** | **okuyabilir, çalıştırabilir** |
||

</br>

<div style="color:red">

>Bu izinleri "**r, w, x, s, t**" karakterleri yerine ikilik -**binary**- sitemde düşüp sekizlik -**octal**- sistemde belirtebiliriz.

</div>

Konuyu örnek ile ele alalım:


``` {.sh}
touch file
```

"**file**" dosyasını detaylı listeleyelim:

``` {.sh}
ls -l file
```

Çıktı:
``` {echo}
-rw-r--r-- 1 senol senol 0 Feb 20 11:19 file
```

Bu çıktıda görüleceği üzere file dosyası erişim yetkileri "**r w - r - - r - -**" şeklindedir.

Bu yetkileri, sahip, grup ve diger kullanıcılara göre ayrı ayrı gösterelim:

Yetki varsa "**1**", yoksa "**-**"


| | user | group | other | 
|:--|:--:|:--:|:--:|
| İzinler  | r w - | r - - | r - - | 
| **Binary** |**110** | **100** | **100** |
| **Octal** |**6** | **4** | **4** |

</br>

İklik tabandaki -sistemdeki- sayıyı octal tabana çevirdiğimizde elde ettiğimiz **644** sayısı "**file**" dosyasının sahip, grup ve diğer kullanıcılar için erişim izinlerini göstermektetir. 

>Bu çevirmelerde basamak sayısı maksimum 3 olacağından elde edeceğimiz rakam 8 den küçüktür ve dolayısıyla hesaplamada sekizlik "octal" yerine onluk "decimal" gibi düşünebiliriz.

</br>

 **110** sayısı için Binary - Octal çevirme işlemi :

_**Decimal:** (110)<sub>2</sub>  = (1×2<sup>2</sup>) + (1×2<sup>1</sup>) + (0×2<sup>0</sup>) = (1x4) + (1x2) + (0x1) = (6)<sub>10</sub>_

_**Octal** = 6 / 8  = (6)<sub>8</sub>_  

</br>



**100** sayısı için Binary - Octal çevirme işlemi:

_**Decimal** : (100)<sub>2</sub> = (1×2<sup>2</sup>) + (0×2<sup>1</sup>) + (0×2<sup>0</sup>) = (1x4) + (0x1) + (0x1)  =(4)<sub>10</sub>_

_**Octal** : 4 / 8  = (4)<sub>8</sub>_ (mod)

</br>

#### **Varsayılan  Dosya/Dizin Yetkileri**

</br>

Varsayılan dosya ve dizin izinleri, bir Linux sistemde yeni bir dosya veya dizin oluşturulduğunda atanan varsayılan izinlerdir. 
Bu varsayılan izinler, genellikle sistemin öntanımlı ayarlarına göre belirlenir.

* Varsayılan **dosya** izinleri : **666** (rw-rw-rw-) 
* Varsayılan **dizin** izinleri : **777** (rwxrwxrwx)

Çoğu dağıtımda oluşturduğumuz dosyalarda izinleri **666** olarak görmeyiz. Bunun nedeni **UMASK** değeridir. 

<div style="color:red">

>Dosya ve dizin oluşturduğumuzda bu dosyaların izinleri **UMASK** değeri varsayılan değerlerden çıkartılarak belirlenir. Her kullanıcı için ayrı bir **UMASK** değeri ayarlanabilir.    
</div>

``` {.sh}
umask
```

Pardus İşletim Sisteminde varsayılan -öntanımlı- UMASK değeri:

``` {echo}
0022
```

Dolayısıyla bir;
* dosya oluşturduğumuzda izinler : 666 - 022 = **644**
* dizin oluşturduğumuzda izinler : 777 - 022 = **755**

olacaktır. 
Bu;

dosyalar için;
sahibinin dosyayı okuma ve yazma yetkisine sahip olacağı, grup üyelerinin dosyayı yalnızca okuyabileceği ve diğer kullanıcıların dosyayı görebileceği ancak hiçbir şey yapamayacağı,

dizinler için ise;
sahibinin tüm haklara sahip olduğu ancak diğer kullanıcıların dizinleri görebilecekleri ancak içlerine dosya koyamayacakları anlamına gelir. 


Varsayılan dosya ve dizin izinleri, sistemin güvenliğini sağlamak için önemlidir. Bu izinler, yeni dosyaların veya dizinlerin varsayılan olarak ne kadar güvende olduğunu belirler. Bu nedenle, bir sistem yöneticisi, varsayılan izinlerin gerektiği gibi ayarlandığından emin olmalıdır.

Bir dosyanın erişim izinlerine "**getfacl**" komutu ile de bakabiliriz.

``` {.sh}
getfacl file
```

``` {echo}
# file: file
# owner: senol
# group: senol
user::rw-
group::r--
other::r--
```

</br>

#### **Özel İzinler (s ve t bitleri)**

Yukarıdaki örneklerde dosya erişimlerinin 3bit(---) üzerinden tanımlandığı belirtilmişti. Aslında genelde 3 bit üzerinden yetkilendirilir demek daha doğru bir ifadedir.

Fakat gerçekte günlük hayatta çok fazla kullanılmayan 4. Bir bit daha vardır. Dördüncü bitin ise **s(suid bit)** ve **t(sticky bit)** olmak üzere iki ayrı işlevi vardır.


</br>

#### **SUID Bit(s)** 

</br>


SUID (Set User ID) biti, bir dosyayı çalıştıran kullanıcının yerine dosya sahibinin kullanıcı kimliğini kullanarak dosyayı çalıştırmayı sağlar.

Örneğin, "**passwd**" komutu, kullanıcıların parolalarını değiştirmelerini sağlar. Ancak, parolalar "**shadow**" dosyasında şifrelenmiş şekilde saklanır ve bu dosya yetkili kullanıcı tarafından görüntülenebilir ve değiştirilebilir. İşte **passwd** komutundaki **SUID** biti bize shadow dosyasına yazma izni sağlar.

``` {.sh}
ls -l /usr/bin/passwd
```

Çıktıdaki "**s**" karakterine dikkat edin. 

``` {echo}
-rwsr-xr-x 1 root root 63960 Feb  7  2020 /usr/bin/passwd
```


</br>


#### **SGID Bit(s)** 

</br>

**SGID (Set Group ID)** biti, bir dosyayı çalıştıran kullanıcının yerine dosya sahibinin grubunun kimliğini kullanarak dosyayı çalıştırmayı sağlar. Bu özellik, birden fazla kullanıcının aynı dosyaları paylaşması gerektiğinde kullanışlıdır.

SGID biti, bir dizine uygulandığında, dizinin içindeki dosyaların varsayılan olarak bu dizinin grubunu sahipleneceği anlamına gelir. Bir dosyaya uygulandığında ise, dosyanın grubunu sahip olan kullanıcının grubuna değiştirir.

SGID yetkisi  "**...**"  değeri ile verilebilir.



#### **Sticky Bit(t)** 

Genelde herkesin yazmasına açık olan /tmp gibi dizinlere uygulanır. Bu bitin amacı herkesin erişimi olan dizinlerde kullanıcılar tarafından oluşturulan dosyaların sadece o kullanıcı tarafından silinebilmesini sağlar. 

Dizinlere sticky bit yetkisi "**1777**" veya "**+t**" komutu ile verilir. 

---

"**/tmp**" dizininin erişim izinlerine göz atalım:

``` {.sh}
ls -ald /tmp
```

Çıktıdaki "**s**" karakterine dikkat edin.

``` {.echo}
drwxrwxrwt 22 root root 36864 Feb 20 20:26 /tmp
```
---

</br>

>**Sticky Bit(t)**  genellikle, paylaşılan bir dizin içindeki dosyaların yanlışlıkla silinmesini önlemek için kullanılır.

</br>

>Çalıştırma hakkı olmayan dizin veya dosyaya sticky bit hakkı verilirse sondaki **t** yerine **T** gösterilir.

</br>
Şimdi dosya ve dizinler üzerinde bu izinleri nasıl ayarladığımıza bakalım: -**chmod**- 

----
 [Dosya Yönetimi / Listeleme -ls- ](tr_dosya-yonetimi-listeleme-ls-.md) << Önceki / Sonraki >> [Dosya Yönetimi -Erişim Haklarını Değiştirme- -chmod-](./tr_dosya-yonetimi-izinler-chmod-.md)