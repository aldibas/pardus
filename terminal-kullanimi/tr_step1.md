###  Seviye: Başlangıç

#### Linux Nedir?

Linux, serbestçe dağıtılabilen, çokgörevli, çok kullanıcılı UNIX işletim sistemi türevidir. 

Linux, İnternet üzerinde ilgili ve meraklı birçok kişi tarafından ortak olarak geliştirilmekte olan ve başta sunucular ve kişisel bilgisayarlar olmak üzere birçok platformda çalışabilen ve herhangi bir maliyeti olmayan bir işletim sistemidir.

Linux, kabuk olarak da bilinen bir komut satırı arayüzünden (CLI) yönetilir. Donanım ve yazılım süreçlerini yöneten çekirdeğin yanı sıra, Linux dağıtımları, donanıma erişmek ve kontrol etmek için bir dizi Linux yazılımı içerir.

Çekirdeğin sistemi sonlandırmasını ve çökmesini önlemek için, işletim sistemlerinin tümünün çekirdeğini **çekirdek alanı** adı verilen korumalı ve kısıtlı bellekte çalıştırdığını bilmek önemlidir.

Bir kullanıcı bir uygulamayı veya aracı çalıştırdığında, bu uygulama veya araç, **kullanıcı alanı** adı verilen alanda çalışır. Bu ayrım kritiktir. Bu uygulamaları çekirdek alanından ayrı çalıştırmaları sayesinde, çekirdek kaynaklarına müdahale edemezler ve sistemin paniğe kapılmasına (çökmesine) neden olamazlar

## Linux Nasıl Ortaya Çıktı?
Linux'ın bir UNIX türevi olduğundan bahsetmiştik.

UNIX 70'li yılların ortalarında büyük bilgisayarlar üzerinde çok kullanıcılı bir işletim sistemi olarak geliştirilmiştir. Zaman içerisinde yayılmış ve birçok türevi ortaya çıkmıştır.Bugün kişisel bilgisayarlardan süper bilgisayarlara kadar biçok bilgisayar için yazılmış UNIX türevleri mevcuttur. 

Linux, temel olarak Finlandiya Üniversitesinde öğrenci olan Linus Torvalds'ın ve İnternet üzerinde meraklı bir çok yazılımcının katkıları ile geliştirilmiştir. Linux gelişimi açık bir şekilde yapılmaktadır. Bunun anlamı, işletim sisteminin her aşaması açık olarak İnternet üzerinde yayınlanmakta, dünyanın dört bir yanında kullanıcılar tarafından test edilmekte, hataları ve eksiklikleri tesbit edilerek düzeltilmekte ve geliştirilmektedir.

## Öğrenme Hedefleri
Linux Playground ortamını tamamladıktan sonra;

+ Dosya yönetimi, kopyalama,silme taşıma gibi temel işlemleri,
+ Sistem güncellemeyi, paket komutlarını, kurulumlarını ve yönetimlerini,
+ Kullanıcı yönetimini gerçekleştirmeyi,
+ Sistem izlemeyi ve süreç (process) yönetimini öğreneceksiniz.


## Ön gereksinimler

+ Temel manada bilgisayar kullanabilme, program yükleyebilme. Bunun haricinde Linux konusunda hiçbir temel bilgiye ihtiyacınız yok. İhtiyacınız olan her şey Bulut Bilişim Akademi'de mevcut.

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
