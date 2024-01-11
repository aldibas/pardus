# **Terminal & Kabuk -Shell- Komutları**

## Süreç Yönetimi ve Süreç İzleme

</br>


### **Süreç Oluşturma ve Sonlandırma**
</br>

Süreçler iki şekilde oluşturulur:

1. Çatallanma (fork): Ana süreç kendi kopyasını çıkartarak yeni iş bu kopyaya yaptırtılır. İlk çalışan süreç olan init kendi kopyasını çıkartarak yeni işleri bu kopyaya yaptırır. Bu şekilde bir soyağacı ile yeni süreçler oluşturulur.

2. Yeni süreç başlatma (exec): exec komutuyla yeni bir süreç başlatılır. Bu süreç ana sürecin yerini alır. Komut satırından exec ile bir komut çalıştırıldığında, komut bitince tekrar komut satırına dönülmez. Çünkü yeni süreç ana sürecin yerini almıştır, artık ana süreç kalmamıştır. Buna en güzel örnek komut satırından exec komutuyla ssh komutunu çalıştırmaktır. Karşı sunuya bağlantı kuran ssh komutu exec ile çalıştırıldığından kendi ana süreci olan kabuğun yerini almıştır. Karşı taraftan exit yapılıp ssh sonlandırıldığında konsol penceresi kapanır
Çünkü artık dönülecek bir kabuk yoktur.

Bash kabuğu komut çalıştırırken fork + exec yapar. Yani kendisinin bir klonunu çıkartır ve bu klon exec yaparak yeni süreci başlatır. Yeni süreç klonun yerini alır. Dolaysıyla komut bittiğinde klon kabuk olmayacak ancak klonu çıkartan esas kabuk hala var olacak.

Ana süreç oluşturduğu alt sürecin sonlanmasını wait(2) veya waitpid(2) sistem çağrısıyla bekler. Eğer bir alt süreç sonlandığı halde ana süreci tarafından beklenmiyor ise o alt süreç zombi durumuna geçer. Sistem kaynağı tüketmez ancak çok sayıda olmaları durumunda PID numaraları karmaşıklaşacaktır. Böyle bir durumda ana sürece **SIGCHLD** sinyali gönderilerek alt sürecini takip etmesi istenir. Sinyal göndermek için
kill komutu kullanılır. Eğer ana süreç halen daha alt sürecinin kendisine dönmesini beklemiyorsa artık ana süreç öldürülür. Bu durumda zombi süreç sahipsiz (orphan) süreç pozisyonuna geçer. Bütün süreçlerin atası olan init süreci belli aralıklarla sahipsiz süreçleri sahiplenerek yok eder.
Programlar, programcıların kodlarındaki exit fonksiyonlarıyla yada dışardan gelecek kesmelerle **(interrupt)** sonlanır. Programlar sonlanırken 0-255 arası bir çıkış değeri ile sonlanırlar. Bu değer programın neden çıktığını göstermesi açısından önemlidir.

Genel olarak 0 ile çıkan programlar başarıyla görevini tamamlayarak, 1-255 arası bir rakamla çıkan programlar ise bir hata ile karşılaşarak sonlanmıştır demektir. Hangi kodun hangi anlam taşıdığı genel olarak programcının belgelendirmesinde belirtilmektedir.

Programlar dışardan müdahalelerle kesme (interrupt) yiyerek sonlanabilirler. Örneğin çalışan harddiskte arıza çıkması bir kesme olarak çekirdek tarafından programa iletilecektir ve program kesmeyi alınca sonlanacaktır.

### Sinyaller
Kullanıcı ortamında kill komutuyla süreçlere ellen sinyal gönderilebilir. Sinyallerin her birinin özel bir anlamı olup sürecle haberleşmeyi sağlar. Örneğin bir süreç **SIGFPE** (Floating Point Error) almışsa sıfıra bölmek gibi anlamsız bir işlem yaptığını haber verir.

Sinyaller eğer program tarafından yakalanmazsa genellikle programın aniden sonlanmasına neden olur. Bu nedenle programcılar kendilerine gelen sinyali yakalayıp programı düzgün bir şekilde kapatırlar. Sinyali işleyen bu kısma programcılıkta sinyal işleyici (signal handler) denir.
Aşağıdaki tabloda sinyallerin bir kısmı verilmektedir:

|Sinyal|Değer|Aksiyon|Açıklama|
|-|:-:|:-:|-|
|SIGHUP|1|Term|Terminali askıya al yada süreci sonlandır|
|SIGINT|2|Term|Term Klavyeden gelen kesme|
|SIGQUIT|3|Core|Klavyeden gelen çıkış kesmesi|
|SIGILL|4|Core|Tanımsız CPU işlemi|
|SIGABRT|6|Core|Abort|
|SIGFPE|8|Core|Matematik işlemci hatası|
|SIGKILL|9|Term|Süreci öldür|
|SIGSEGV|11|Core|Geçersiz bellek adreslemesi|
|SIGPIPE|13|Term|Okuyucusu olmayan kırık pipe’a yazma hatası|
|SIGALRM|14|Term|Zamanlama sinyali|
|SIGTERM|15|Term|Sonlandırma sinyali|
|SIGUSR1|30,10,16|Term|Programcının tanımladığı özel sinyaller|
|SIGUSR2|31,12,17|Term|Programcının tanımladığı özel sinyaller|

Listede tanımlanmış aksiyonlar:
- **Term**: Süreci sonlandır
- **Ign** : Sinyali gözardı et
- **Core**: Süreci sonlandır ve bellek dump’ı al
- **Stop**: Süreci durdur

</br>
---
</br>


### **nohup**

</br>

Verilecek komutları herhangi bir kesintiye uğramadan çalıştırmayı sağlar. Bütün sinyalleri devre dışı bırakarak çalışan sürecin sinyallerden etkilenmesini engeller. Genelde uzak bağlantılarda uzun sürecek komutların bağlantı sonlandığında bile arka planda devam etmesi için kullanılır. Kullanıcı sistemden çıksa ve terminali kapatsa bile komut çalışmasına devam edecektir. Çünkü nohup komutu terminalin ürettiği ve süreci de sonlandıracak sinyalleri engeller.

**nohup komut &** biçiminde uygulayabilirsiniz.

**<u>Örneğin</u>** çok uzun sürecek bir işlem olan SUID biti set edilmiş dosyaların bulunmasını nohup ile başlatıp terminal kapatılabilir. Normalde ekrana (Stdout) basılacak çıktılar nohup.txt dosyasına yazılır. Arka planda ne olduğunu görmek için bu dosyaya bakılabilir.

``` {.sh}
nohup find / -xdev -type f -perm +u=s -print &
```

Komut çıktısı:
``` {.echo}
[1] 17897
kaan@pardus:~$ nohup: girdi gözardı ediliyor ve çıktı 'nohup.out' e ekleniyor
```

Nohup komutu sadece arka planda sinyallere maruz kalmadan çalışmayı engeller. Screen gibi bir terminal yöneticisi değildir.

**& bg fg jobs**
Bash kabuk altında çalışan bir süreç yarıda kesilebilir, arka plana gönderilebilir, tekrar önplana alınabilir veya arka planda sonlandırılabilir.

Aşağıdaki gibi uzun sürecek bir görev arka plana gönderilebilir. Arka plana göndermek için komut sonuna & simgesi eklenir.

``` {.sh}
find / -ctime -1 > changed-files.txt &
```
Bir komutu çalıştırıp, bir süre izledikten sonra **Ctrl-Z** ile kesilip **bg** komutu verilerek de
arka plana gönderilebilir.

``` {.sh}
wget http://www.google.com
```

Komut çıktısı:
``` {.echo}
[1]+ Stopped
wget http://www.google.com
$ bg
[1]+ wget http://www.google.com &
```
Arkaplana giden bir iş sonlandığında konsola aşağıdaki gibi mesaj verilir:

``` {.echo}
[1]+
Done
wget http://www.google.com
```

Arka plana gönderilmiş görevleri görmek için jobs komutu kullanılır:

``` {.sh}
jobs
```

Ekran çıktısı:
``` {.echo}
[1]
Running
[2]- Running
[3]+ Done
bash script.sh &
sample-soft &
browser .
```

Arka plandaki bir işi tekrar ön plana almak için fg komutu kullanılır. Hiçbir parametre verilmezse en son arka plana gönderilen komutu ön plana alır. Aşağıdaki komutla 1 numaralı arka plan işi öne alınır:

``` {.echo}
kaan@pardus:~$ fg %1
```

Arka plandaki bir işi sonlandırmak için kill komutu kullanılır. Aşağıdaki komut arka plandaki 2 numaralı işi sonlandırır:

``` {.echo}
kaan@pardus:~$ kill %2
```

### Kill, killall

Süreçlere sinyal göndermek için kill komutu kullanılır.

Aşağıdaki komut 1120 PID numaralı sürece 9 numaralı (SIGKILL) sinyali gönderir. Dolaysıyla süreci öldürür.


``` {.sh}
kill -9 1120
```

Linux altında bir sürecin yapılandırma dosyasını yeniden okuması için normalde sürecin sonlandırılıp yeniden başlatılması gerekmektedir. Süreci sonlandırmadan bunu yapmanın yolu çalışan sürece **SIGHUP** göndermektir. Bu sinyali alan sürec kendini askıya alır ve aynı **PID** numarası içerisinde çalışmasına en baştan başlar.

``` {.sh}
kill -1 1531
```

``` {.sh}
killall -HUP httpd
```

killall komutu PID numarasına bakmadan süreç ismi, kullanıcı, protokol gibi opsiyonlar ile sürece sinyal göndermek için kullanılabilir.

### Pkill, pgrep

Sürecin adı veya sahibi gibi değişik pattern’ler verilerek belirtilen sürece sinyal göndermek için pkill kullanılır. Aşağıdaki komut user4 kullanıcısının sahip olduğu tüm süreçleri sonlandırır.

``` {.sh}
pkill -STOP -u user4
```

Aşağıdaki komut ise adında http geçen bütün süreçleri sonlandırır.

``` {.sh}
pkill http
```

Verilen kritere hangi süreçlerin uyduğunu görmek için pgrep komutu kullanılır. Böylece verilen komuttan etkilenecek süreçlerin istenen süreçler olduğundan emin olunur.

``` {.sh}
pgrep -u user4
```

Komut çıktısı:
``` {.echo}
6081
6082
```
<br>

``` {.sh}
pkill -u user4
```
veya

``` {.sh}
pgrep http
```

Komut çıktısı:
``` {.echo}
3077
3531
3532
3533
3534
```

<br>

``` {.sh}
pkill http
```

</br>
---