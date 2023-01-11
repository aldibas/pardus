## Bash Kullanımı

### Bash kabuğunda komut girişi


**BaSH** kabuğunda **help** yazarak **dahili** komutların listesiniz alabiliriz. Çalıştırılabilir komutların listesi için **/usr/bin** ve **/usr/sbin** dizinlerini **ls** komutu ile listeleyebiliriz.

**Dahili komutlar:**
</br>

``` {.sh}
help
```
</br>

Bulunduğumu konumdaki dosyalar:

``` {.sh}
ls
```
</br>


**Çalıştırılabilir komutlar:**

``` {.sh}
ls /usr/bin
```

``` {.sh}
ls /usr/sbin
```
GNU/Linux dosya sistemi konusunda bu konumlara ayrıca değineceğiz.

</br>


>**BaSH** kabuğu, komut ya da **path/yol/adres** -dosya ya da dosya konumu- girişlerinde **Tab -sekme-** tuşunu kullanmanız halinde yazmaya başladığınız path tanımı yapılmış komutu ya da dosya/dizin  ismini otomatik  tamamlayacaktır. Benzer karakterler ile başlayan komut ya da dosyalar var ise **2** defa **tab** -sekme- tuşuna basarak bunların listesini alabilirsiniz.

Örneğin "al" yazıp tab tuşuna basmanız halinde komutu "**alias**" olarak tamamlayacaktır.

``` 
alias
```
“**ls**” yazdıktan sonra iki defa tab tuşuna basarsanız aşağıdaki komut listesi ekrana gelecektir. Kullanmak istediğimiz komutu yazmaya ve tab ile tamamlamaya deva edebiliriz.

```
ls        lsblk     lsipc     lslogins  lsns      
lsattr    lscpu     lslocks   lsmem
```

Gördüğünüz gibi **CPU bilgilerimizi, PCI aygıtlarımızı, disk bloklarımızı/bölümlerimizi** görüntülemek için **ls** -list- yazıp **tab** tuşu ile bir nevi ipucu alabildik.  


>**Yukarı ok** ve **Aşağı ok** tuşları ile daha önce yazdığınız komutları yeniden yazmak yerine ekrana getirerek tekrar kullanabilirsiniz. **Ctrl + p , Ctrl + n** tuşları da aynı işlemi sağlayacaktır. p:**P**revious, n:**N**ext

Aşağıdaki diğer kısayol tuş kombinasyonlarının işlevlerini inceleyebilirsiniz. Bazı tuşları işlevleri kullandığınız kabuk (bash,sh) ya da uçbirime (gnome-terminal, guake, konsole, terminator, xterm, yakuake) göre değişebilir.  


|**Kısayol**|**İşlev**|
| ----: | ------- |
|Ctrl + r|Daha önce kullanılan komutlarda arama yapar.
|Ctrl + d|Çıkış (logout)|
|Ctrl + l|Temizle (ekran yukarı kayar (clear) )
|Ctrl + Shift + x| 	Geçmişi silerek konsol ekranını temizler/sıfırlar.
|Ctrl + u| 	imlecin solundaki karakterleri siler
|Ctrl + a| 	Satır başı
|Ctrl + e| 	Satır sonu
|Ctrl + c| 	Komutu sonlandırır.
|Ctrl + s| 	Komutu geçici süre durdurur.
|Ctrl + q| 	Durdurulmuş işlemi devam ettirir.
|Ctrl + +|	Yazı boyutunu büyütür.	
|Ctrl + -| 	Yazı boyutunu küçültür.	
|Alt + .|Son komut argümanı
||

Daha önce kullandığımız komut listesini "**history**" komutu ile alabiliriz.

``` {.sh}
history
```
Terminalinizde daha önce kullandığınız komutlar şağıdaki gibi listelenecektir.
```
senol@pardus:~$ history
1   help
2   ls  
3   ls /usr/bin
4   ls/usr/sbin
5   alias
6   lscpu
7   lsblk
8   history 
senol@pardus:~$
```
>Bu listeden bir komutu kullanmak için "**!**" karakterinden sonra **sıra numarasını** girin. Bu listeye göre, **!6** girmeniz halinde **cpu bilgileri**, **!7** ile de **disk bölümleri** görüntülenecektir. "**!-n**" şeklinde kullanarak **sondan** itibaren sıralı kullanabiliriz. **!-2** : "**sondan 2. komutu çalıştır.**" gibi.

Yukarıdaki listeye göre örnek:
|sıra|karşılığı|
|--|--|
|**!3**|ls /usr/bin
|**!-1**|history
|**!-3**|lscpu
|**!!**|history
||
>Kullandığınız bir komutun geçmiş listesinde görünmemesini istiyorsanız komutun başında **boşluk " "** karakterini kullanabilirsiniz. Elbetteki sisteminizi bu durumu engelleyecek şekilde de yapılandırabilirsiniz.


>"**;**" ve mantıksal bağlaçları -**&&**- / -**||**- kullanarak birden fazla komutu tek satıra yazabiliriz.

```
command1 ; command2 ; command3 ...
command1 && command2 && command3 ...
command1 || command2 || command3 ...
command1 && command2 || command3 ...
command1 || command2 && command3 ...
command1 ; command2 || command3 ...
```
Örnek:

``` {.sh}
pwd ; whoami ; uname
```
Yukarıdaki dizilimde tüm komutlar çalışacaktır ve aşağıdakine benzer bir çıktı elde edilecektir.
```
/home/senol
senol
Linux
```

||||
|-|-|-|
|**pwd**|**P**rint **W**orking **D**irectory |-->  Çalışma dizinini yazdır. |
|**whoami**|**Who am i**| --> Kullanıcı adımı yazdır|
|**uname**|**U**nix **name**|--> Sistem Bilgilerini yazdır|
|||

Bu komutlardan herhangi birirnin, hata üretmesi/sistemimizde bulunmaması, hatalı girilmesi diğer komutların -sağındaki- çalışmasını engellemeyecektir.



Özetle kullandığımız tüm komutların her durumda çalışmasını istiyorsak komutları "**;**" ile ayırabiliriz.

 ``` 
pwd ; Whoami ; uname
```
Bu şekilde kullanımda "**Whoami**" büyük "**W**" karakterinden kaynaklı hataya sebep olacak ancak bu durum **uname** komutunun çalışmasını engellemeycektir. Aşağıdaki çıktıda **uname** komutunun cevabı olarak "**Linux**" çıkrısı görülmektedir.


```
/home/senol
Bash: Command 'Whoami' not found
Linux
```


>Bazen, bir amaca yönelik sıralı işlemler -komutlar- gerçekleştirmeniz gerekebilir. Bu durumda amaca yönelik işlemlerin hatasız tamamlanması -zincirin kopmaması- gerekir. Bunu sağlamak için "**ve**" -**&&**- bağlacını kullanmamız gerekir. 

"**&&**" karakterleri -bağlacı- hatalı bir komut ile karşılaşılması durumunda sağındaki komutu işletmeyecektir.

``` {.sh}
pwd && whoami && uname
```

3 komutun da hata üretmemesi durumunda çıktı:  

```
/home/senol
senol
Linux
```

Bu kullanımda **whoami** komutunun çalışması, **pwd** komutunun, **uname** komutunun çalışması ise, **pwd** ve **whoami** komutlarının hatasız çalışmalarına bağlıdır.

``` {.sh}
pwd && Whoami && uname
```

Bu örnekte **Whoami** hataya sebep olacağından uname komutu işletilmeyecektir. 

Çıktı :
```
/home/senol
Bash: Command 'Whoami' not found
```

>Bazen de aynı amaca yönelik farklı çözüm yöntemleri -komutlar- olabilir. Tek çözüm yöntemi ile amaca ulaşmak için "**veya**" -**||**- bağlacını kullanmamız gerekir. 


``` {.sh}
whoami || echo $USER   
```

Yukarıdaki dizilimde **whoami** komutu hata vermeyeceği için **echo $USER** komutu çalışmayacaktır.

Çıktı : 
```
senol
```

||||
|-|-|-|
|**echo $USER** |Print USER variable |-->  USER değişkenini yazdır. |
|**whoami**|Who am i| --> Kullanıcı adımı yazdır|
|||


``` {.sh}
Whoami || echo $USER   
```

Bu şekilde kullanımda "**W**hoami" büyük "**W**" karakterinden kaynaklı hataya sebep olacağı için istediğimiz amaca ulaşamamış olacağımızdan **echo #USER** komutu çalışacaktır.
masını engellemeycektir. Aşağıdaki çıktı "**W**hoami" değil "**echo #USER**" komutunun çıktısıdır.
```
senol
```
Aşağıdaki tabloda **koyu** renkli komutların hataya neden olacak şekilde yazıldığını varsayarsak, dizilime göre 2. sütundaki komutlar kabuk ile etkileşime geçecektir -çalışacaktır-. Bir komutun hata üretmesi çalışmıyor yanılgısına düşürmemeli.

|Dizilim|Çalışan komutlar|
|-|:-:|
|komut-1 ; **komut-2** ; komut-3       | 1, 2, 3|
|komut-1 && **komut-2** && komut-3     | 1, 2  |
|komut-1 \|\| komut-2 \|\| **komut-3** | 1    |
|**komut-1** && komut-2 \|\| komut-3   | 1, 3  |
|komut-1 && komut-2 \|\| komut-3       | 1, 2  |
|**komut-1** \|\| komut-2 && komut-3   | 1, 2, 3|
|komut-1 \|\| komut-2 && komut-3       | 1, 3  |
|komut-1 ; **komut-2** \|\| komut-3    | 1, 2, 3|

</br>

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


command $(command)
command `command`











### Kabuk Değişkenleri















Kullanabileceğiniz diğer kabukları görmek için shells dosyasına bakabilirsiniz. **shells** dosyası **/etc** dizini içerisindedir. dosya içerikleri ise **"cat, more, less"** gibi bir çok komut ile görüntülenebilir. Bu komutların detaylı kullanımlarına ileride |değineceğiz.


``` {.sh}
cat /etc/shells
```
Kullanıcı Yönetimi konusunda varsayılan giriş kabuğunu belirleme konusuna ayrıca değineceğiz.

Varsayılan kapuğunuzu "**ps**" -**P**rocess **S**tatus- komutunu kullanarak ta görebilirsiniz.
``` {.sh}
ps
```
**ps** komutu açık olan süreçlerimizi görüntüler ve kabuğumuzda otomatik olarak başlatılmış süreçler ile kendisini -**ps**- ve giriş kabuğumuzu -**bash**- görüntüleyecektir.

Buradaki **TTY** altındaki **PTS** ler "sözde terminal" **PS**eudo**T**erminal- olarak adlandırılabilir. Sözde terminaller için basitçe grafik grafik arabirimden başlattığımız terminal pencereleri -**xterm**- diyebiliriz. Yardımcı uygulama diyebileceğimiz bu terminaller başlatma sıramıza **PTS/0, PTS/1, ..** şeklinde numaralandırılacaktır.

**TTY** ifadesi ise henüz TCP/IP protokolünün geliştirilmedi dönemlerde **UNIX** sistemlere **seri** bağlanan donanım cihazlarından/konsollardan -**T**ele**TY**pewriter- gelmektedir.

Bu aygıt dosyaları dosya sistemin "**kök**" -"**/**"- dizinindeki "**dev**" -**device**- altındadır. Bu aygıtların listesini,
``` {.sh}
ls /dev/tty
```
komutu ile alabiliriz.

Bu yerel terminallerde oturum açmak için "**Ctrl**+**Alt**+**Fn**" tuşlarını kullanabiliriz. Örneğin, **Ctrl**+**Alt**+**F1**" kısayolu ile **tty1** oturum ekranına geçebiliriz. TTY ekranında iken diğer oturumlar **Alt**+**Fn**" ile geçebilir, grafik arabirime dönmek için ise **Ctrl**+**Alt**+**F7**" tuşlarını kullanabiliriz.


Oturum açtığımız terminalde -**CLI**- komut satırının sol kısmında ekran promptu bulunur. Bu prompt **PS1** değişkeninde tutulur ve kullandığımız kabuğa göre içeriği farklı atanmış olabilir.
PS1 değişkeninin içeriğini görüntülemek için,

``` {.sh}
echo $PS1
```
komutunu kullanın.

Bu değişkenin içerisindeki bazı karakterler ve anlamları şu şekildedir:

>**\h**     : **h**ostname (makine adı)

>**\u**     : **u**ser (kullanıcı adı)

>**\w**     : **w**orking directory (çalışma dizini) 

Örneğin **PS1** değişkenini içeriğini **\u@\h:\w\$** şeklinde görüyorsanız ekran komut satırı promptunuz aşağıdaki gibidir.</br>

>**senol@pardus:~$**

----

>**senol** : _username_

>**pardus** : _hostname_

>**~**  : _Aktif kullanıcının "**ev**" -**home**- dizini "**/home/senol**"_

> **$**  : _sıradan kullanıcı hesabında oldugunuzu gösterir._</br>

>Ekran promptunda **$** yerine **#** karakteri varsa, bu yetkili kullanıcıda -**root-** olduğunuzu gözterir. 

-----

Bu ayarlar, buradaki senaryoda farklılık gösterebilir. PS1 değişkeninde **PTS** oturumlarınızda çoğunlsukla sayılar görürsünüz. Bunlar ekran promtunuzun renkli olması için gereklidir.

**Araştırma :** PS2 prompt / PS2 değişkeni

**Görev :  senol@pardus:~\$** şeklindeki birincil promptunuzda -PS1-, hostname yerine zaman görüntülensin. Sonuç : **senol@17:05:~$** gibi.

