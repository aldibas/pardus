## Bash Kullanımı

### **Komutlarda Yönlendirme**

Yukarıdaki örneklerimizde kullandığımız programlar bize terminal üzerinde çıktılar üretti. Unix ve GNU/Linux benzeri sistemlerde programların **girdi** ve **çıktı**larını yönlendirebiliriz.

>"**<**", "**>**","**2>**" karakterleri ile komutların girdi ve çıktılarını başka bir kaynağa -dosya,program,aygıt- yönlendirebiliriz. Buradaki aygıtlar için de dosya ifadesini kullanabiliriz. Geniş gösterimi ile yönlendirmede kullanabileceğimiz karakterler/biçimler: **<, >, >>, 2>, 2>> ve | -pipe-** 



|Dosya Tanımlayıcısı <br>File descriptor -Fd-|Kullanım|Açıklama |
|:-:|:-:|-|
|0 : STDIN |<|Standart Girdi -Input- |
|1 : STDOUT|>|Standart Çıktı -Output-|
|2 : STDERR|2>|Standart Hata -Error |

</br>


#### **Standart Girdi Yönlendirme** : -STDIN-
Bir uygulamaya girdi göndermek için "**<**" karakterini kullanabiliriz. 

``` {.sh}
sort <file 
```
Burada "file" ismindeki dosyanın içeriği **sort** komutuna yönlendirilir ve ekran çıktısı olarak file dosyasının içeriği sıralı biçimde çıktı olarak alınır.

``` {.sh}
sort <file >file-A-Z
```
Bu kullanımda ise "**file**" ismindeki dosyanın içeriği **sort** komutuna yönlendirilerek sıralanmış içerik **file-A-Z** dosyasına yazdırılır. Bu örnekteki çıktı yönlerdirme -**>**- için bir sonraki konuyu inceleyiniz.


#### **Standart Çıktı Yönlendirme** : -STDOUT-

Standat çıktı yönlendirme için "**1>**" karakterlerini kullanabiliriz. Buradaki "1" rakamını kullanmamıza gerek yoktur ancak 1 rakamı dosya adında kullanılabilen bir karakter oldugundan komut diziliminde ayıraç olarak boşluk kullanmayı unutmamalıyız.

</br>

``` {.sh}
echo merhaba dünya 
```
Üstteki "echo" komutu ekrana "merhaba dünya" yazdırır. 

``` {.sh}
echo merhaba dünya > mesaj
```
komutu echo komutunda çıktı olan "merhaba dünya" ifadesini mesaj dosyasına yazar. 
>Bu kullanımda mesaj dosyası yok ise oluşturulur var ise içeriği sıfırlanır. bu sebeple ">" karakteri dikkatli kullanılmalıdır. 

"**ls**" komutu ile dosya listesini alabiliriz.

```
senol@pardus:~$ ls
mesaj
```

"**cat**" komutu ile mesaj dosyasını içeriğini ekrana yazdıralım.

```
senol@pardus:~$ cat mesaj 
merhaba dünya
```

>"**set -o noclobber**" ile "**>**" karakteri ie üzerine yazma kapatılabilir. Bu durumda üzerine yazmak için "**|>**" kullanılmalıdır.

</br>

>"**>>**" karakterleri ise mevcut dosyanın sonuna **ekleme** -append- yapar.

``` {.sh}
echo hello world >> mesaj
```
Bu kullanımda mesaj dosyası yoksa oluşturulur ve icerisine "**hello world**" yazılır, var ise mevcut dosyanın sonuna "**hello world**" ifadesi eklenir.

"cat" komutu ile mesaj dosyasını tekrar görüntülediğimizde çıktı şu şekildedir.

```
senol@pardus:~$ cat mesaj 
merhaba dünya
hello world
```

**Örnekler:**

Çalışma dizinimizdeki dosya listesini list dosyasına yazalım:

``` {.sh}
ls >> list
```

Çalışma dizinimizdeki dosya listesini **list** dosyasına yazalım:

``` {.sh}
ls > list
```

**USB** aygıtlarımızın listesini "devices" dosyasına yazalım:

``` {.sh}
lsusb > aygit
```

**PCI** aygıtlarımızın listesini "**devices**" dosyasına ekleyelim:

``` {.sh}
lspci >> aygit
```

Disk bölümlerimizi **disk** dosyasına yazalım:

``` {.sh}
lsblk > disk
```

"**devices**" ve "**disk**" dosyalarını "**system-info**" dosyasına birleştirelim:


``` {.sh}
cat devices disk > system-info
```
 "**system-info**" dosyasını görüntüleyelim:

```
  cat system-info
```

#### **Standart Hata Yönlendirme:** -STDERR-

Üstteki örneklerimizde hata oluşmadığında oluşan çıktıları dosyaya yazdık. Peki uygulama hata çıktısı ürettiğinde bu hata çıktısını bir noktaya nasıl yönlendirebiliriz?

Yukarıdaki tabloda standart hata dosya tanımlayıcısın "2" olduğunu belirtmiştik. Dolayısı ile standart hatayı yönlendirirken "**2>**" ya da "**2>>**" karakterlerini kullanabiliriz.


``` {.sh}
ls 2> hata
```

Bu kullanımda "**ls**" komutu bir hataya neden olmasa da hata dosyası oluşturulur. Ancak hata dosyası var ise bu dosyanın içeriğinin sıfırlanacağı unutulmamalıdır.

``` {.sh}
LS 2> hata
```

Bu kullanımda "**LS**" isminde bir program ya da "**alias**" -ileriki konularda değineceğiz- olmadığını varsayarsak "hata" dosyasına "**komut bulunamadı**" gibi bir ifadenin yazılmasını bekleriz. Halihazırda "**hata**" isminde dosya mevcut ise bu dosyanın mevcut içeriği sıfırlanacaktır.

``` {.sh}
cat hata
```
komutunu kullandığımızda dosyanın içeriği aşağıdaki gibidir.

```
senol@pardus:~$ cat hata
LS: command not found
```

oluşan hataları bir dosyada toplamak için "2>>" şeklinde yönlendirme yapılmalıdır.

``` {.sh}
LS 2>> hata
```

```
senol@pardus:~$ cat hata
LS: command not found
LS: command not found
```
Uygulamaların ürettikleri çıktıları -stdout/stderr- burada olduğu gibi sistem günlük dosyaları -**log**- gibi  tutabiliriz. 
Bu hata çıktılarını log dosyalarında tutmak gereksiz ise oluşan bu hata çıktıları terminalde görüntülenecektir. Bazı durumlarda bu istenmeyen bir durumdur. Sayfalarca akan çıktıda gereksiz hataları görmek odaklanmamız gereken bilginin gözden kaçmasına neden olabilir. Buna çözüm olarak:

>Uygulama hata çıktılarını **kök** "-/-" dizinindeki "**dev**" altında bulunan "**null**" aygıt dosyasına yönlendirebiliriz.

```
fping -a -g 192.168.1.0/24 
```

Bu komut, ağımızdaki aktif olan cihazların listesini verecektir ancak netmask değerimize göre alınmamış IP'lerden kaynaklı hata mesajları ile birlikte 256 satırlık çıktı oluşacaktır -netmask:24-. 

Biz sadece açık olan cihazların ip adreslerini istiyorsak üsteki bu komutu aşağıdaki biçimde yazabiliriz.

```
fping -a -g 192.168.1.0/24 2> /dev/null
```

>Uygulamaların ürettikleri standart outpu ve standart hatayı "**2>&1**" dizilimi ile aynı noktaya yönlendirebiliriz.

``` {.sh}
ls file >list 2>&1
```

Bu örnekte **file** isminde dosya **var** ise dosyanın ismi, **yok** ise "**bulunamadı**" gibi bir hata mesajı "**list**" dosyasına list dosyasının içeriği **sıfırlanarak** yazılacaktır.

**Örnekler:**

``` {.sh}
ls file 1>liste 2>> error
```
Aşağıdaki sonuçlar elde edilir:
* **liste** ve **error** dosyaları yoksa oluşur.
* Çalışma dizininde "**file**" isminde dosya **varsa** bu dosyanın ismini liste dosyasının içeriğini sıfırlayarak bu dosyaya yazar.
* Çalışma dizininde "**file**" isminde dosya **yoksa** "bu isimde bir dosya ya da dizin yok" gibi bir hata mesajını error dosyasına **ekler**.


##### **Pipe kullanımı**

GNU/Linux komutlarını kullanırken komutların işlevlerini birleştirerek -birlikte kullanarak- çok hızlı sonuçlar alabilirsiniz.


>"**Pipe**" -boru- "**|**" karakteri bir komutun çıktısını -**output**-, başka bir komuta girdi -**input**- olarak göndermemizi sağlar.

</br>

**Örnekler:**

"**history**" komutu ile komut geçmişimizi görebiliriz.

``` {.sh}
history   
```
Ancak kullandığımız komut sayısı fazla ise bu komut geçmişimizi "**pipe**" -**|**- karakteri ile "**more**" komutuna göndererek sayfa sayfa görüntüleyebiliriz.

``` {.sh}
history | more  
```
>Ekran çıktısında;<br>
sayfa sayfa ilerlemek için "**space**" -boşluk-,</br>
satır satır ilerlemek için "**enter**" -giriş-,</br>
Çıkış için "**Q**"
tuşunu kullanın. 

Bu örnekten anlaşılacağı üzere history komutunun çıktısı, "**|**" karakteri ile  standart output aygıtı -ekran gibi- yerine "**more**" komutuna gönderilmiştir.

Örnek 2: 1000 e karadar olan sayıları toplayalım:

"**seq**" komutu ile sayıları ekrana yazdırabiliriz.
``` {.sh}
seq 1000 
```
"**paste**" komutunda, "**s**" -serial- parametresi ile bu sayıları yan yana, "**d**" parametresi ile de araya "+" koyarak yazdırabiliriz.

``` {.sh}
seq 1000 | paste -s -d+
```
Son olarak bu çıktıyı "bc" -**B**asic **C**alculator- uygulamasına göndererek sonucu yazdırabiliriz.

``` {.sh}
seq 1000 | paste -s -d+ | bc
```
>"**|**" karakteri ile komutların gücünü birlikte kullanarak, tek satırlık bu kodun çıktısı gibi süreç alacak işlemleri hızlıca sonuçlandırabiliriz.

</br>

 [Bash kullanımı](./tr_bash-kullanimi.md) << Önceki / Sonraki  >>  [Bash kabuğu değişkenleri](tr_bash-kabugu-degiskenleri.md)


