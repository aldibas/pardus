###  Seviye: Başlangıç

#### Bash Shell Script Nedir, Ne İşe Yarar, Nasıl Çalışır?

Bash shell script, Unix/Linux kabuğu tarafından çalıştırılmak üzere tasarlanmış bir bilgisayar programlama dilidir. Linux işletim sisteminde komut satırında işletilen komutların tekrar tekrar yazılması yerine programlanarak tekrar edilmesini sağlar. Bash script hemen hemen bütün Linux dağıtımlarında bulunur, ayrıca herhangi bir kurulum yapmanıza gerek yoktur.

Bash dili, Stephen Bourne'nin UNIX için geliştirmiş olduğu sh kabuk dilini temel alarak geliştirildiği için; Bourne-Again SHell kelimelerinin kısaltması olan BASH şeklinde adlandırılmıştır. Linux sistemlerinde shell denilen yapı ile iletişim kurma konusunda BASH dışında (ksh,tcsh,zsh,fish...) gibi birçok Shell (kabuk) dili bulunuyor. Ancak yetenekleri dolayısıyla en çok tercih edilen kabuk programı BASH kabuk programıdır. Bash script kavramının tam olarak anlaşılabilmesi için öncelikle bahsedilmesi gereken birkaç önemli kavram bulunuyor. Şimdi sırasıyla bu kavramları bir örnek üzerinden ele alalım.

Örneğin kullanıcı bulunduğu konumda yeni bir dosya oluşturmak istiyor ve bunu bilgisayara bir şekilde ifade etmeli. İfade biçimi olarak grafiksel arayüz de olabilir komut kullanımı da olabilir. Komut kullanımını tercih edersek, kullanıcının komutu bilgisayara aktarması için konsol denilen yapıyı kullanması gerekiyor. Konsol kullanıcının komutlarını sisteme iletmesine yardımcı bir araçtır. 

Komut konsola giriliyor ve yazılmış olan komut, shell yani kabuk denilen yapı tarafından alınıyor. Daha sonra kernel yani çekirdeğe iletiliyor. Çekirdek, kabuktan aldığı emri donanımlara ifade ediyor. Ve en nihayetinde donanım, çekirdekten aldığı emir doğrultusunda yapılması gereken işlevi yerine getiriyor. Bu süreci görselleştirelim: 

![Flow](https://raw.githubusercontent.com/taylanbildik/bash_script_dersleri/master/img/Giri%C5%9F/stab.gif)

Yapıyı tekrar kısaca ele alacak olursak, örneğin en başında dosya oluşturmak için konsola girilen komut bash dilinin bir komutudur ve kullanıcı bu komut sayesinde shell denilen yapı ile iletişim kurdu. Shell de kullanıcıdan aldığı emri kernel'e yani çekirdeğe aktardı. Neticede çekirdek de ilgili donanımlara gerekli işi yaptırarak dosyanın oluşmasını sağladı. 

Bash kabuk dilinin bu kadar yetenekli olmasının nedeni; sh dili haricinde ksh(korn shell) ve csh(C shell) gibi çeşitli kabuk dillerinin en iyi özelliklerini içerisinde barındırarak, hem etkileşimli olması hem de programlanabilirlik için işlevselliği arttıran geliştirmeler içermesidir. Bu gibi sebeplerden ötürü, GNU/Linux işletim sistemlerinde BASH dışında da kabuk dilleri barındırılmasına rağmen, genelikle sistemin varsayılan kabuk yorumlayıcısı BASH kabuğudur.
 

## Öğrenme Hedefleri

Bu eğitim senaryosunda, bash kabuk programının komutlarını tek bir dosya içerisinde uygun şekilde toparlayarak toplu işlemleri yerine getirmeyi öğreneceksiniz. Bu işlem bash shell scripting olarak geçiyor. Böyle ifade edilmesinin nedeni de kabuk dili olan bash dilinin, yerine getirebileceği işlemleri tek tek yapmak yerine senaryolaştırılarak tek seferde tek elden gerçekleşmesinin sağlanmasıdır.

Yani kısacası gerekli tüm komutları tek bir dosyada uygun şekilde toparlayarak; durumlara özel senaryolar oluşturacağız ve oluşturulan senaryolara göre de sistem verilen emirleri otomatik olarak gerçekleştirecek.

Peki bu neden önemli? Olası senaryolara bir kaç örnek verelim.

Örneğin sistem dosyalarının her gün yedeklenmesinin gerektiği bir durumda bu işlemi otomatikleştirmek yerine her gün elle yapmak gereksiz bir uğraş olacaktır. Yine bir diğer örnek olarak, sistemin online olup olmadığını her daim kontrol etmek yerine bu iş için bir script yazarak 7/24 sistem çalışma durumunun gözetlenmesini ve olası bir kesinti durumunda bizleri haberdar etmesini sağlayabiliriz.

Bu gibi pek çok örnek verebilir ve ayrıca bu otomatikleştirilebilir işlemlere oldukça karmaşık olan görevler de atanabilir. Örneğin sistemdeki işleyişin kontrolü için 50 duruma göre 100 karmaşık komutu her gün dikkatli şekilde konsola girmeniz gerektiği bir durumda, bu işlemleri bash schell scripting ile otomatikleştirerek kullanmak oldukça verimli ve stabil sonuçlar doğuracaktır.

Kısacası bash script kullanarak, sistemle ilgili otomatikleştirilebilir her türlü işi tek seferde kolayca yerine getirtebilirsiniz. Yani ihtiyaçlarınıza göre script yazarak, çalışan ve yorulmak bilmeyen binlerce sistem yöneticisi üretebilirsiniz.

Üstelik bash bir kabuk dili olduğundan diğer dillere oranla sistemle çok daha hızlı etkileşim kurarak, bizlere yüksek performans sağlıyor. Hazırsanız Bulut Bilişimciler Platfromunda bu üstün gücü nasıl kontrol edebileceğimizi öğrenmeye başlayalım.


## Ön gereksinimler

+ Linux dağıtımlarından en az birine aşina olmalı ve kullanabiliyor olmalısınız.


## Senaryo 1

Bu bölümde komutları senaryo haline getirme yani scripting kısmına odaklanacağız. Bunun nedeni de konu kapsamını mümkün oldukça verimli şekilde öğrenmenizi sağlamaktır. Ancak yine de komutları kullandıkça kullandığım komutlar hakkında kısa hatırlatmalarda bulunacağız.


Öncelikle kullanmakta olduğumuz sistemde varsayılan olarak hangi kabuk programı kullanılıyor buna bakalım. Bakmak için birden fazla yol bulunuyor, örneğin konsola `echo $SHELL` komutunu girersek konsol bize mevcut oturumda kullanılan shell yani kabuk programını çıktı olarak basıyor:

``` {.sh}
root@bulutbilisimciler:~# echo $SHELL
>> /bin/bash
``` 

Ayrıca `ps` komutuyla süreç sorgusu yaparsak da karşımıza çalışmakta olan shell programı çıkacaktır:

``` {.sh}
root@bulutbilisimciler:~# ps
>> PID TTY   TIME     CMD
    9 pts/0  00:00:00 bash
   89 pts/0  00:00:00 ps
``` 

Bu şekilde sistemde kullanılmakta olan mevcut kabuk programını kolaylıkla öğrendik.Fakat sistemde yalnızca tek bir kabuk programı da bulunmuyor. Bunu da etc dizini altında yer alan shells isimli dosyanın içeriğine bakarak teyit edebiliriz. Konsola `cat /etc/shells` komutunu girerek dosyamızın içeriğini sorgulayalım:

``` {.sh}
root@bulutbilisimciler:~# cat /etc/shells
>>/etc/shells: valid login shells
/bin/sh
/bin/bash
/usr/bin/bash
/bin/rbash
/usr/bin/rbash
/bin/dash
/usr/bin/dash
/usr/bin/tmux
/usr/bin/screen
```

Gördüğünüz gibi sistemde yüklü bulunan kabuk programlarının hepsi bu dosya içerisinde listelenmiş bulunuyor. Daha önce de belirttiğimiz şekilde birden fazla kabuk programının olduğunu ve bunların aynı sistemde yüklü bulunabileceğini de hep birlikte teyit etmiş olduk. Şimdi asıl odak noktamız olan bash kabuk programını ele alarak ilk scriptimizi yazmaya başlayalım.

Bash script yazarken ilk olarak dosyanın başına `#!/bin/bash` ifadesini eklememiz gerekiyor. Neden diyecek olursanız, bu satır sonraki alt satırların hangi kabuk tarafından yorumlanacağını bildiren standart bir tanımdır ve komutların doğru yorumlanabilmesi için her bash scriptinde olmalıdır. 

Program çalıştırıldığında sistem tarafından öncelikle ilk satır okunur ve ilk satırda geçen kabuk diline göre program ilgili kabuk dili aracılığı ile çalıştırılır. Şayet ilk satıra hiç bir ifade eklemezseniz program varsayılan olarak mevcut kabuk üzerinden script dosyasını çalıştırmayı dener. Yani aslında mevcut sisteminizde kullanılan kabuk bash ise, `#!/bin/bash` ifadesini betik dosyanıza eklemeseniz de betik dosyanız sistemde varsayılan kabuk bash olduğundan sorunsuz şekilde çalışacaktır. Ancak yine de yazmış olduğunuz betik dosyasının diğer sistemlerde de doğru şekilde çalıştırılabilmesi için bu ifadeyi eklemek son derece önemlidir. Zira çoğu sistem bash kabuğunu varsayılan olarak kullansa da, istisnai durumlarda farklı kabukların kullanıldığı da olabiliyor.

İlk scriptimize konsol ekranına çıktı basan program örneği ile başlayalım. Bunun için konsola çıktı basan komutumuz olan `echo` komutunu kullanacağız. Örneğin konsola `echo "Bulut Bilişimciler"` yazarsak çıktı olarak "Bulut Bilişimciler" ifadesi konsola basılacaktır:

``` {.sh}
root@bulutbilisimciler:~# echo "Bulut Bilişimciler"
>>Bulut Bilişimciler
```

İşte bizler de bu komutu betik dosyamız içerisine yazıp kaydedersek, bu dosyamızı her çalıştırdığımızda konsol ekranına selamlar ifadesi basılacak.

Hemen test edelim, `echo "Bulut Bilişimciler"` komutunu betik dosyasının içerisine yazıp, dosyayı "bb.sh" ismi ile kaydedelim. Bunun için `vi bb.sh` komutuyla "bb" isimli bir metin belgesi yaratıp düzenlemeye gidebiliriz. Bu dosyanın ilk satırına daha önce bahsettiğimiz `#! /bin/bash` komutunu, ikinci satırına ise `echo "Bulut Bilişimciler"` yazalım. Ardından ESC'ye basıp sırasıyla `:wq!` komutunu uygularsak "bb.sh" belgemizi kaydedip çıkmış olduk. Şimdi bu betiği çalıştıralım:

``` {.sh}
root@bulutbilisimciler:~# bash bb.sh
>>Bulut Bilişimciler
```


Yazmış olduğumuz betiği çalıştırmanın birden fazla yolu bulunmaktadır. Bunlar içinde biri, biraz önce gördüğünüz gibi konsola `bash BetikDosyasıAdı.sh` şeklinde komut vermektir. Ayrıca bir diğer yol da "bash" yerine "sh" ifadesini kullanarak konsola `sh BetikDosyasıAdı.sh` şeklinde komutumuzu girmektir:

``` {.sh}
root@bulutbilisimciler:~# sh bb.sh
>>Bulut Bilişimciler
```

Bash kabuk dili sh kabuk dilininin daha da gelişmiş halidir. Bu gelişmeler daha çok kullanıcı deneyimini arttırmaya yönetilik işlevselliklerin eklenmesi yönündedir. Örneğin bash kabuğunu kullanıyorken konsola bir komutun yarısını yazıldıktan sonra Tab tuşuna basılırsa komutun geri kalan kısmı otomatik olarak tamamlanıyor. İşte bu gibi özellikler kullanıcı deneyimini arttırmaya, dolayısı ile sistem yönetimini daha verimli hale getirmeye yöneliktir. Yani sh ile bash kabuk dillerinin temel yapıları benzer olup, işlevsellik bakımından farklılık gösterdiklerinden, bash kabuk dili ile yazdığımız betik dosyasını hem sh hem de bash ile çalıştırabiliyoruz.

Ayrıca betik dosyasını konsola `./BetikDosyasıAdı.sh` şeklinde komut girerek de çalıştırabiliriz: 

``` {.sh}
root@bulutbilisimciler:~#  ./bb.sh
>> -bash: ./selam.sh: Permission denied
```

Eğer "Permission denied" veya "Erişim engellendi" gibi bir çıktı alıyorsanız merak etmeyin. Çünkü bu kullanımda diğer iki kullanımdan farklı olarak, dosyamızın çalıştırma yetkisinin bulunması gerekiyor. 

Bu sorunu aşmak için dosyamıza chmod komutu ile gereken çalıştırma yetkisini vermemiz gerekiyor. Bunun için konsola `chmod +x bb.sh` şeklinde komutunu girelim ve `ls -la | grep bb` komutu ile dosyanın aldığı yetkiyi teyit edelim:

``` {.sh}
root@bulutbilisimciler:~# chmod +x bb.sh
root@bulutbilisimciler:~# ls -la | grep bb
>> 
-rwxr-xr-x  bb.sh
```

Şimdi çıktı olarak "Permission denied" aldığımız komutu tekrar çalıştırabiliriz:

``` {.sh}
root@bulutbilisimciler:~# ./bb.sh
>>Bulut Bilişimciler
```

Dosyamızı çalıştırdık ancak, dosyamızı çalıştırmak üzere girmiş olduğumuz komutun çalışma yapısını daha iyi anlamak adına, kullanmış olduğumuz `./` komutunu açıklayalım.

Komutta kullandığımız ".(nokta)" ifadesi bildiğiniz gibi şu anda bulunduğumuz konumu ifade ediyor. Noktadan sonra kullanmış olduğumuz "/(Slash)" ifadesi ise bulunduğumuz konumdaki betik dosyasına ulaşmamızı sağlıyor. Yani konsola `./bb.sh` yazmak ile `/root/bb.sh` şeklinde yazmak aynı şeyi ifade ediyor:

``` {.sh}
root@bulutbilisimciler:~# /root/bb.sh
>>Bulut Bilişimciler
```

Böylelikle ilk bash shell scriptimizi diğer bir deyişle ilk betiğimizi yazıp çalıştırmış olduk.

Bir sonraki kısımda anlatıma değişkenler ile devam edeceğiz.
