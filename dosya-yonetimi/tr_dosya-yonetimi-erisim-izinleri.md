# Yetkiler

Linux yetkilendirme modeli, UNIX ve BSD’den alınmıştır.

``` {.sh}
ls -l /bin/cp
```
Komut çıktısı:
``` {.echo}
-rwxr-xr-x 1 root root 146880 Şub 28  2019 /bin/cp
```

**ls** komutu **-l** parametresi ile kullanıldığında yukarıdaki gibi dosyaların yetkilerini belirten ayrıntılı bir çıktı verir. Satır başında yer alan **-rwxr-xr-x** bu dosyaya ait hakları belirtmektedir. 

>Bu haklar üç kısımdan oluşmaktadır.

- **-rwx**
- **r-x**
- **r-x**

İlk kısmın hemen başında tek bir simgeyle dosyanın türü ifade edilmektedir. Yukarıdaki gibi eğer boş ise (yani -) normal dosyadır.

- **d** :directory (dizin)
- **l** :symbolic link (sembolik bağ)
- **c** :character special device (karakter aygıt)
- **b** :block special device (blok aygıt)
- **p** :fifo
- **s** :socket

İlk kısım dosya sahibine ait hakları, ikinci kısım aynı gruptaki kullanıcılara ait hakları, son kısım ise diğer kullanıcılara ait hakları belirlemektedir.

- **r** :okuma izni(4)
- **w** :yazma izni(2)
- **x** :çalıştırma izni(1)

*Örneğin:* **754** modu Dosya sahibi için **7** (4 + 2 + 1, yani rwx), grubu için **5** (4 + 1, yani rx) ve herkes için **4** (yani r) hakkı vermektedir.

## chmod
**chmod** Yetkileri değiştirmek için kullanılır.

Örnek olarak bir dosya oluşturalım:

``` {.sh}
touch dosya.txt
```

Aşağıdaki komutu ile dosya izinlerini görelim:
``` {.sh}
ls -al dosya.txt
``` 

Komut çıktısı:
``` {.echo}
-rw-r--r-- 1 root root 0 Kas 29 16:34 dosya.txt
```

Aşağıdaki komutu ile dosya yetkilerini değiştirelim.
``` {.sh}
chmod 755 dosya.txt
```

Aşağıdaki komutu ile dosya izinlerini yeniden görelim:
``` {.sh}
ls -al dosya.txt
``` 

Komut çıktısı:
``` {.echo}
-rwxr-xr-x 1 root root 0 Kas 29 16:35 dosya.txt
```

**755** belirtilen üç grup için 7, 5, 5 haklarını vermektedir. Her bir yetkinin rakamsal değeri vardır. 7, 5 ve 5 bu rakamların toplamıdır.

- **r** :4
- **w** :2
- **x** :1

Bu rakamlara göre;

 **7 = r + w + x** anlamında,
 **5 = r + x** anlamındadır. 
 
 Bunun dışında **u :user**, **g :group** ve **o :other** olacak şekilde de yetki verilebilir:

``` {.sh}
chmod g+w dosya.txt
```

<u>Örnekler:</u>

Hiç hakları olmayan dosya aşağıdaki gibi görünür:

``` {.echo}
---------- 1 root root 0 Kas 29 16:37 deneme.txt
```

``` {.sh}
touch deneme.txt 
```
komutu ile **deneme.txt** isminde bir dosya oluşturalım.

``` {.sh}
chmod 000 deneme.txt
```
komutu ile tüm hakları elinden alalım.

Bu dosya için herkese **r:okuma** hakkı şu şekilde verilir:
``` {.sh}
chmod +r deneme.txt
```

``` {.sh}
ls -al deneme.txt
```
komutu ile kontrol edelim:

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al deneme.txt
-r--r--r-- 1 root root 0 Jan 26 14:46 deneme.txt
```

Eğer yalnızca dosya sahibine (**u:user**) yazma hakkı verilmek istenirse sırayla komutları uygulayalım:

``` {.sh},
chmod u+w deneme.txt
```
komutuyla yetkileri değiştirelim.

``` {.sh}
ls -al deneme.txt
```
komutu ile kontrol edelim:

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al deneme.txt
-rw-r--r--   1 root root    0 Jan 26 14:46 deneme.txt
```

Eğer gruba (g) ve diğerlerine (o) çalıştırma hakkı verilecekse aşağıdaki komut kullanılır:

``` {.sh}
chmod g+x,o+x deneme.txt
```
komutunu uygulayalım.

``` {.echo}
ls -al deneme.txt
```
komutu ile kontrol edelim:

Komut çıktısı:

``` {.echo}
kaan@pardus:~$ ls -al deneme.txt
-rw-r-xr-x   1 root root    0 Jan 26 14:46 deneme.txt
```

Veya tüm bu işlemler rakamlarla yapılabilir.

``` {.sh}
chmod 754 deneme.txt
```
komutunu uygulayalım.

``` {.sh}
ls -al deneme.txt
```
komutu ile kontrol edelim:

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al deneme.txt
-rwzr-xr-x   1 root root    0 Jan 26 14:46 deneme.txt
```


## chown
**chown** Dosya sahibi ve grubunu değiştirir.

- **R**: Belirtilen dizinin tüm dosyaları ve alt dizinleriyle birlikte sahip ve grup bilgilerini değiştirir.

Aşağıdaki örnekte şimdiki sahibi root:root olan beni.oku dosyasının sahibi kaan:root olarak değiştirilmiştir.

İlk olarak aşağıdaki komutu ile **kaan** isminde bir kullanıcı oluşturalım:

``` {.sh}
useradd kaan 
```

Aşağıdaki komutu ile okubeni isminde bir dosya oluşturalım.

``` {.sh}
touch okubeni
```

Aşağıdaki komutu ile sahibini kontrol edelim:
``` {.sh}
ls -al okubeni
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al okubeni 
-rw-r--r-- 1 root root 0 Jan 27 06:08 okubeni
```

Aşağıdaki komutu ile sahibini **kaan** kullanıcı olarak değiştirelim.
``` {.sh}
chown kaan:root okubeni
```

Aşağıdaki komutu ile sahibini kontrol edelim:
``` {.sh}
ls -al okubeni
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al okubeni 
-rw-r--r-- 1 kaan root 0 Jan 27 06:16 okubeni
```
## chgrp
Sadece dosya ve dizinin grubunu değiştirmede kullanır. Chown komutu gibi **-R** parametresi kullanılabilir. Aşağıdaki örnekte dosyanın sahibi users grubu yapılmıştır.

``` {.sh}
addgroup muhasebe
```
komutu ile **muhasebe** isminde bir grup oluşturalım.

``` {.sh}
ls -al okubeni
```
komutu ile gurubunu kontrol edelim:

Komut çıktısı:

``` {.echo}
kaan@pardus:~$ ls -al okubeni 
-rw-r--r-- 1 kaan root 0 Jan 27 06:16 okubeni
```

Aşağıdaki komutu ile gurubnu **muhasebe** gurubu olarak değiştirelim.
``` {.sh}
chgrp muhasebe okubeni
```

Aşağıdaki komutu ile gurubunu yeniden kontrol edelim:
``` {.sh}
ls -al okubeni
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al okubeni
-rw-r--r-- 1 kaan muhasebe 0 Jan 27 06:16 okubeni
```

## Özel İzinler(t ve s bitleri)
Yukarıdaki örneklerde dosya erişimlerinin 3bit(---) üzerinden tanımlandığı belirtilmişti. Aslında genelde 3 bit üzerinden yetkilendirilir demek daha doğru bir ifadedir.

Fakat gerçekte günlük hayatta çok fazla kullanılmayan 4. Bir bit daha vardır. Dördüncü bit’de **t(sticky bit)** ve **s(suid bit)** olmak üzere iki ayrı vardır.

### **Sticky bit(t)** 

Genelde herkesin yazmasına açık olan /tmp gibi dizinlere uygulanır. Bu bitin amacı herkesin erişimi olan dizinlerde kullanıcılar tarafından oluşturulan dosyaların sadece o kullanıcı tarafından silinebilmesini sağlar. Dizinlere sticky bit hakkı **chmod 1777** veya **chmod +t** komutu ile verilir. Dizinin stickey bit hakları olup olmadığı dosya haklarının sonundaki t ifadesi ile anlaşılır.

Aşağıdaki komutunu çalıştıralım:
``` {.sh}
ls -ald /tmp
```
Komut çıktısı:
``` {.echo}
drwxrwxrwt 1 root root 6 Jan 27 06:16 /tmp
```

>Çalıştırma hakkı olmayan dizin veya dosyaya sticky bit hakkı verilirse sondaki **t** yerine **T** gösterilir.

### **Suid bit(s)** 
Normal kullanıcıların bir komutu çalıştırırken sadece o komut için geçici olarak daha yetkili bir kullanıcı haklarıyla iş yapmasını sağlar. Bu hak **chmod 4755** komutu ile verilir.

Örnek olarak aşağıdaki komutları uygulayabilirsiniz:

``` {.sh}
touch liste
```

``` {.sh}
ls -al liste 
```

Komut çıktısı:
``` {.echo}
-rw-r--r-- 1 root root 0 Jan 27 06:29 liste
```

``` {.sh}
chmod +t liste 
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al liste
-rw-r--r-T 1 root root 0 Jan 27 06:29 liste
```

``` {.sh}
chmod -t liste 
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al liste
-rw-r--r-- 1 root root 0 Jan 27 06:29 liste
```

``` {.sh}
chmod +s liste 
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al liste
-rwSr--r-- 1 root root 0 Jan 27 06:29 liste
```

``` {.sh}
chmod -s liste 
```

Komut çıktısı:
``` {.echo}
kaan@pardus:~$ ls -al liste 
-rw-r--r-- 1 root root 0 Jan 27 06:29 liste
```
