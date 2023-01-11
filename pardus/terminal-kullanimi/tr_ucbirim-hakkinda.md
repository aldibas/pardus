## Uçbirim Hakkında

### Giriş

Pardus işletim sisteminde işlemlerinizi grafik arayüzleri ile gerçekleştirebileceğiniz gibi komut istemcisini (uçbirim) kullanarak gerçekleştirebilirsiniz. Bu ifadeden de anlaşılacağı üzere Uçbirim, diğer bir adıyla konsol -console-, bir komut satırı aracıdır.

Çoğu Pencere yöneticisinde **Ctrl+Alt+T** klavye kısayolu ile başlatılabilir. Bu durumda aktif kullanıcı hesabında varsayılan olarak ayarlanmış olan giriş kabuğunda -shell- yandaki gibi oturum açılmış olacaktır.
Sizin oturumunda daha önce bahsettipimiz sh, bash, zsh, tcsh gibi kabuklardan hangi kabugun varsayılan olarak geldiğini görmek çin aşağıdaki komutu girin.</br>
``` {.sh}
echo $0
```

Ayrıca,
``` {.sh}
echo $SHELL
```
komutunu da kullanarak mevcut kabuğun tam yolunu öğrenebilirsiniz. Örneğin, eğer bash kabuğunu kullanıyorsanız, çıktı "/bin/bash" olacaktır.

Kullanabileceğiniz diğer kabukları görmek için shells dosyasına bakabilirsiniz. **shells** dosyası **/etc** dizini içerisindedir. dosya içerikleri ise **"cat, more, less"** gibi bir çok komut ile görüntülenebilir. Bu komutların detaylı kullanımlarına ileride değineceğiz.


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

