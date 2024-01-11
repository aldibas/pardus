# **Terminal & Kabuk -Shell- Komutları**

## Süreç Yönetimi ve Süreç İzleme

</br>

Süreç (*process*) genel tanımla çalışan bir programdır. Süreçler, komut satırından çalıştırılan kısa süreli komut olabileceği gibi işletim sisteminin açık olduğu süre boyunca çalışan bir ağ servisi de olabilir.
Kullanıcıların süreçleri yönetebilmesi için her sürece ait bir **PID** numarası vardır. 

Süreçle ilgili yapılacak işlemler bu **PID** numarası üzerinden gerçekleştirilir. Linux altında çalışan ilk süreç init olup *PID numarası* her zaman **1**’dir. Init ilk süreç olduğu için kullanıcı tarafından başlatılan diğer süreçlerin aksine çekirdek tarafından başlatılır. Bazı süreçler eş zamanlı çalışan alt thread’lere sahip olabilir. Thread’ler aynı PID altındadır, kendilerina ait bir PID numarası olmaz. Örneğin Mozilla Firefox’ta bir thread DNS sorgularını çözerken diğer thread sunucuyla konuşur.

</br>

### **ps** (Process Status) 

</br>

"ps" (Process Status) komutu, Linux ve UNIX işletim sistemlerinde, çalışan işlemlerin listesini görüntülemek için kullanılan bir komuttur. Bu komut, işletim sistemi tarafından çalıştırılan tüm işlemlerin adını, PID (Process ID) numarasını, CPU kullanımını, bellek kullanımını, çalışma süresini ve diğer özellikleri gösterir. ps komutu, sistem yöneticileri için işletim sisteminin çalışma durumunu anlamak için önemli bir araçtır.


``` {.sh}
ps
```

Komut çıktısı:
``` {.echo}
    PID TTY          TIME CMD
      1 pts/0    00:00:00 startup.sh
      7 pts/0    00:00:00 supervisord
     12 pts/0    00:00:00 dockerd
    125 pts/0    00:00:00 bash
    127 pts/0    00:00:00 ps
```

Kabuk dışında çalışan süreçleri görüntülemek için ps komutunu, `ps aux` ya da `ps -aux` biçiminde kullanabiliriz. Opsiyonlarda "tire (-)" kullanımı POSIX ve UNIX standartları ile BSD standartları açısından farklılık oluşturabilir.

- **a** : x seçeneğiyle birlikte kullanıldığında tüm süreçleri listeler.
- **-a** : Uçbirimle ilişkili olmayan süreçler tüm süreçler. (Yönetici hesaplar hariç).
- **-A** / **-e**  : Tüm süreçler.
- **u** : Belirtilen kullanıcıya ait süreçler
- **t** : Belirtilen terminale ait kullanıcılar

``` {.sh}
ps aux
```

Komut çıktısı:
``` {.echo}
USER  PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root  1  0.0  0.0   4024  3184 pts/0    Ss   13:20   0:00 /usr/local/bin/startup.sh
root  7  0.0  0.1  29484 24288 pts/0    S    13:20   0:00 /usr/bin/superviso
root  12  0.0  0.3 1713704 58328 pts/0   Sl   13:20   0:00 /usr/local/bin/dockerd
...
```

---

</br>



### **top**

En çok CPU kullanan süreçleri gösterir. Aynı zamanda süreçleri düzenleyebilecek etkileşimli bir arayüz sunar. Görevleri CPU kullanımına, bellek kullanımına ve çalışma süresine göre sıralar ve sistem yöneticisinin kaynak kullanımını analiz etmesini sağlar.

- **d**: Değerlerin güncellenme aralığını belirlemek için
- **p PID**: Yalnızca verilen PID numarasına sahip süreci izlemeye alır
- **q**: Değerler herhangi bir bekleme olmadan güncellenir
- **C**: Birden fazla işlemci olan sunucularda tek tek CPU değerini göstermek yerine toplam CPU değerlerini gösterir
- **c**: Sadece süreç adını değil tam komut satırı parametrelerini gösterir
- **H**: Thread’leri göstermek için

`top` komutunu çalıştırdığımızda aşağıdaki gibi bir çıktı alırız:
``` {.sh}
top
```

Komut çıktısı:
``` {.echo}
top - 13:38:30 up 130 days, 31 min,  0 users,  load average: 0.00, 0.00, 0.00
Tasks:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 99.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15761.9 total,  10431.5 free,   1498.2 used,   3832.2 buff/cache
MiB Swap:  16384.0 total,  16379.1 free,      4.9 used.  13804.9 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                        
     25 root      20   0 1628568  35056  22588 S   0.3   0.2   0:00.05 containerd                     
      1 root      20   0    4024   3236   2864 S   0.0   0.0   0:00.01 startup.sh                     
      7 root      20   0   29484  24516   8944 S   0.0   0.2   0:00.10 supervisord                    
     12 root      20   0 1639460  54852  32632 S   0.0   0.3   0:00.07 dockerd                        
    126 root      20   0    4236   3420   2932 S   0.0   0.0   0:00.00 bash                           
    128 root      20   0    6936   3220   2736 R   0.0   0.0   0:00.00 top
```

Top çıktısında gösterilen bazı alanların açıklamaları:

- İlk satır: Sistemin ne kadar süredir açık olduğunu gösteren uptime (yukarıdaki çıktıda 24 gün) ve son 1, 5 ve 15 dakika içerisindeki CPU yükünü gösterir. Uptime komutuyla aynı sonucu verir.

- Mem satırı: Toplam bellek, boş bellek ve kullanılan bellek miktarı gibi bellekle ilgili istatistikleri içerir.


|||
|-|:-|
|**PID**|Process ID|
|**PPID**|Ana sürecin PID numarası|
|**User**|Sürecin sahibi kullanıcı|
|**PRI**|Sürecin önceliği|
|**Time**|Süreç başladığından beri tükettiği CPU zamanı|
|**%CPU**|Tüm süreçler içinde CPU zamanının % ne kadarını kullandığı|
|**%MEM**|Toplam süreçler içinde fiziksel belleği % ne kadar kullandığı|
|||



</br>

---
</br>

### htop

**htop**, ncurses tabanlı top benzeri çalışan süreçleri gösteren bir uygulamadır.

Htop programı sistemle birlikte kurulu olmayabilir. Aşağıdaki şekilde kurabilirsiniz:

``` {.sh}
apt-get install htop
```
ya da 
``` {.sh}
apt install htop
```

Kurulum işlemi tamamlandıktan sonra aşağıdaki komut ile çalıştırabilirsiniz.

``` {.sh}
htop
```

Ekran görüntüsü:

<br>
<img align="center" src="md_images/htop.png">
<br>
<br>

>**Htop** arayüzü üç kısımdan oluşmaktadır:

- **Başlık kısmı**: İşlemci, bellek ve Swap kullanımı gösteren barlar ve çalışan süreç sayısı, işlemci yük durumu ve sistemin ne kadar süredir açık olduğu gibi bilgileri içermektedir. Bu görüntü htop menüsünden değiştirilebilir.

- **Gövde kısmı**: top’a benzer olarak süreçlerin işlemci kullanımına göre listelendiği kısımdır.

- **Alt kısım**: Htop menüsünü ve kısayollarını gösterir.



</br>
---


### nice,renice

Bir komutu işlemci önceliğini değiştirmiş olarak başlatır.

**nice -n öncelik komut**

Öncelik -20 ile 19 arasında bir tamsayıdır. -20 en yüksek öncelik demek oluyorken 19 en düşük öncelik demektir. Komut verilmez ise mevcut öncelik değerini ekrana basar. Öncelik değeri bir değer belirtilmezse öntanımlı olarak 10 artırılır.

``` {.sh}
nice
```

Komut çıktısı:
``` {.echo}
0
```
<br>

``` {.sh}
nice nice
```
Komut çıktısı:
``` {.echo}
10
```

<br>

``` {.sh}
nice -n 10 nice
```
Komut çıktısı:
``` {.echo}
10
```

``` {.sh}
nice nice -n 3 nice
```

Komut çıktısı:
``` {.echo}
13
```

<br>

``` {.sh}
nice -n 1000000 nice
```

Komut çıktısı:
``` {.echo}
19
```

Bir sürecin öncelik değerini düşürmeyi ancak yetkili kullanıcılar yapabilir:

``` {.sh}
nice -n -1 nice
```

Komut çıktısı:
``` {.echo}
nice: cannot set niceness: Permission denied
0
```

``` {.sh}
sudo nice -n -1 nice
```

Komut çıktısı:
``` {.echo}
-1
```

Çalışan bir sürecin önceliğini değiştirmek için renice kullanılır. Parametre olarak çalışan sürecin **PID** numarası verilir.

``` {.sh}
renice -n -19 -p 1312
```

Komut çıktısı:
``` {.echo}
-1
```

- **g**: Aynı gruptaki tüm süreçler
- **u**: Aynı kullanıcıya ait tüm süreçler
- **p**: PID numarasına göre eşleşen süreçler

Aşağıdaki komut muhasebe kullanıcı grubuna ait tüm süreçlerin önceliğini 5 yapar.

``` {.sh}
renice -n 5 -g muhasebe
```

</br>
---
