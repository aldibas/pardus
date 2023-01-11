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

Bu değişkenin içerisindeki bazı karekterler ve anlamları şu şekildedir:

>**\h**     : **h**ostname (makine adı)

>**\u**     : **u**ser (kullanıcı adı)

>**\w**     : **w**orking directory (çalışma dizini) 

Örneğin **PS1** değişkenini içeriğini **\u@\h:\w\$** şeklinde görüyorsanız ekran komut satırı promptunuz aşağıdaki gibidir.</br>

>**senol@pardus:~$**
----
>**_senol_** : _username_

>**_pardus_** : _hostname_

>**_~_**  : _Aktif kullanıcının "**ev**" -**home**- dizini "**/home/senol**"_

> **_$_**  : _sıradan kullanıcı hesabında oldugunuzu gösterir._</br>
-----

>Ekran promptundaki "**#**" karekteri yetkili kullanıcıda -**root-** olduğumuzu gözterir. 
-----
Bu ayarlar, buradaki senaryoda farklılık gösterebilir. PS1 değişkeninde **PTS** oturumlarınızda çoğunlukla sayılar görürsünüz. Bunlar ekran promtunuzun renkli olması için gereklidir.



</br>


## Senaryo 1

+ Temel Linux Komutları

İlk senaryoda çeşitli dosya işlemlerini temel seviyede gerçekleştirmenizi sağlayacak olan **echo**, **whoami**, **ls**, **cd**, **cat** ve **pwd** gibi komutları öğreneceksiniz. Sırasıyla başlayalım:



`whoami` komutu sayesinde terminale giriş yapmış olan kullanıcı hesabını görüntülersiniz. Bir başka deyişle, kim olduğunuzu görürsünüz:
``` {.sh}
BulutBilisimAkademi@playground:~$ whoami
>>> BulutBilisimAkademi
```

`ls` komutunu kullanarak bulunduğunuz dizinde yer alan dosyaları listeleyebilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:~$ ls
>>> bin   dev  home  lib    lib64   lost+found  mnt  proc  run   snap  sys  usr  
boot  etc  init  lib32  libx32  media       opt  root  sbin  srv   tmp  var 
```


`cd` komutuyla gitmek istediğiniz dizine gidebilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:~$ cd /home
BulutBilisimAkademi@playground:/home$
```

`pwd` komutunu kullanarak anlık olarak çalıştığınız dizinin patikasını (path) öğrenebilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:/home$ pwd 
>>>/home
``` 

`touch` komutu sayesinde bulunduğunuz dizinde sıfırdan bir dosya yaratabilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:~$ touch info.txt
```

`echo` komutu sayesinde istediğimiz herhangi bir metnin çıktısını terminalde görüntüleyebilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:~$ echo "Bulut Bilişim Akademiye Hoş Geldiniz!"
>>>Bulut Bilişim Akademiye Hoş Geldiniz!  
```

Yine `echo` komutu sayesinde istediğimiz bir metnin çıktısını bir dosyanın içine yönlendirebiliriz:
``` {.sh}
BulutBilisimAkademi@playground:~$ echo "Bulut Bilişim Akademi: Linux Playground" > info.txt
```

`cat` komutu sayesinde bir dosyanın içeriğini görüntüleyebilirsiniz: 
``` {.sh}
BulutBilisimAkademi@playground:~$ cat info.txt
>>>Bulut Bilişim Akademi: Linux Playground
```


`mkdir` komutunu kullanarak sıfırdan bir dizin (klasör) oluşturabilirsiniz. `mkdir` komutunun açılımı **Make Directory** yani **Dizin Oluştur** demektir:
``` {.sh}
BulutBilisimAkademi@playground:~$ mkdir klasor1
```

Biraz önce `mkdir` komutunu kullanarak oluşturduğunuz klasöre bakalım:
``` {.sh}
BulutBilisimAkademi@playground:~$ ls
>>>
info.txt  
klasor1
```


`file` komutu bir dosyanın tipini (türünü) öğrenmenize yarar:
``` {.sh}
BulutBilisimAkademi@playground:~$ file klasor1
>>>klasor1: directory
```


`cp` komutuyla bir dosya veya dizini kopyalayabilirsiniz. `cp` komutunun açılımı **Copy** yani **Kopyala** demektir:
``` {.sh}
BulutBilisimAkademi@playground:~$ cp info.txt klasor1
```

`mv` komutu sayesinde bir dosya veya dizini bulunduğu dizinden taşıyabilirsiniz. `mv` komutunun açılımı **Move** yani **Taşı** demektir:
``` {.sh}
BulutBilisimAkademi@playground:~$ mv info.txt klasor1 
```

`rm` komutuyla bir dosya veya dizini silebilirsiniz. `rm` komutunun açılımı **Remove** yani **Sil** demektir:
``` {.sh}
BulutBilisimAkademi@playground:~$ rm info.txt
``` 


`help` komutu, birlikte kullanıldığı komutun parametre ve argüman kullanımı hakkında bilgi verir. **`help` <'komut'>** şeklinde veya **<'komut'> --help** şeklinde kullanılabilir:
``` {.sh}
BulutBilisimAkademi@playground:~$ rm --help
 >>> Usage: rm [OPTION]... [FILE]...
Remove (unlink) the FILE(s).  
  -f, --force           ignore nonexistent files and arguments, never prompt  
  -i                    prompt before every removal  
  -I                    prompt once before removing more than three files, or
                          when removing recursively; less intrusive than -i,
                          while still giving protection against most mistakes  
...
``` 

`man` komutunun açılımı **Manual Pages**'dir yani **Kılavuz Sayfaları** anlamına gelmektedir. Bu kılavuz sayfaları, yapısında bulundurduğu **Name** (komutun ismi ve açıklaması), **Synopsis** (komutun nasıl kullanılacağı), **Description** (komutun işlevi hakkında detaylı bilgi), **Examples** (komutun kullanımıyla ilgili örnekler) ve **See Also** (komutla ilgili başlıklar) gibi bileşenler sayesinde birlikte kullanıldığı komut hakkında detaylı bir kılavuz sağlar:
``` {.sh}
BulutBilisimAkademi@playground:~$ man rm
>>>NAME
       rm - remove files or directories  
SYNOPSIS
       rm [OPTION]... [FILE]...  
DESCRIPTION  
       This  manual  page  documents  the  GNU version of rm.  rm removes each
       specified file.  By default, it does not remove directories.  
       If the -I or --interactive=once option is given,  and  there  are  more
       than  three  files  or  the  -r,  -R, or --recursive are given, then rm
       prompts the user for whether to proceed with the entire operation.   If
       the response is not affirmative, the entire command is aborted.   
       Otherwise,  if  a file is unwritable, standard input is a terminal, and
       the -f or --force option is not given, or the -i  or  --interactive=al‐
       ways  option  is  given,  rm prompts the user for whether to remove the
       file.  If the response is not affirmative, the file is skipped.  
OPTIONS
       Remove (unlink) the FILE(s).

```

Yukarıda **cd** ve **ls** komutlarıyla klasörlerin bulundukları dizine gitmeyi ve klasörleri listelemeyi öğrenmiştiniz. Peki ya yüzlerce, binlerce dosya arasından bulmak istediğiniz bir dosyayı nasıl arayacaksınız? İşte tam bu noktada **find** ve **grep** komutlarının gücüne hep beraber tanık olacağız.

`find` komutunu kullanarak bulmak istediğiniz dosyanın hangi dizinde olduğunu kolayca öğrenebilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:~$ find info.txt 
>>>klasor1
``` 

`grep` komutu sayesinde, aradığınız kelimenin veya metnin, belirttiğiniz dosyanın içinde bulunup bulunmadığını öğrenebilirsiniz:
``` {.sh}
BulutBilisimAkademi@playground:~$ grep "Akademi" info.txt
>>>Bulut Bilişim **Akademi** : Linux Playground
```
