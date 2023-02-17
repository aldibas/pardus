## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **df -D**isk **F**ree- 


</br>

**df** komutu; dosya sisteminin disk alanı kullanımını görüntüler.

</br>



``` {.sh}
df
```

<br>

Çıktı:

``` {echo}
Filesystem     1K-blocks      Used Available Use% Mounted on
udev            16291192         0  16291192   0% /dev
tmpfs            3266588      1956   3264632   1% /run
/dev/nvme0n1p1 191134604 160330388  21022252  89% /
/dev/nvme1n1   491135216 249284088 216829364  54% /mnt/storage
```

</br>

>Disk dosyalarımız **"/dev"** altında olup diskin bağlı olduğu  isimlendirilirler. 

**Komutun dizilimi;**

```
<command>  [OPTIONS] 
```

Komut seçenekleri : -**OPTIONS**- [-hbkmglt -s \<number> -c \<number>]

| Seçenek | | Açıklama |
|--|:--:|--|
| -h, --human | » | Çıktıyı 3 basamakla halde **kolay okunablir** biçimde görüntüler. 16Gi, 100Mi  |
| -b, --byte | » | Çıktı **byte** cinsinden görüntülenir. |
| -k, --kibi | » | Çıktı **kilobayt -kB-** cinsinden görüntülenir. -Öntanımlı- |
| -m, --mebi | » | Çıktı **megabayt -MB-** cinsinden görüntülenir. | 
| -g, --gibi | » | Çıktı **gigabayt -GB-** cinsinden görüntülenir. |
| -l, --lohi | » | Düşük ve yüksek bellek kullanımı hakkında detaylı bilgi verir. |
| -t, --total | » | Çıktıda toplam -**total**- satırını görüntüler. |
| -c, --count | » | Belirtilen sayı kadar güncel bellek durumu çıktısı verir. |
| -s, --seconds | » | Çıktıyı belirtilen süre -saniye- aralığında vermeye devam eder. İptal: **Ctrl + C** |
|||

</br>

**Örnekler:**

</br>


 ``` {.sh}
free -h
```

Çıktı :

``` {echo}
               total        used        free      shared  buff/cache   available
Mem:            31Gi       2.5Gi        21Gi       752Mi       7.6Gi        27Gi
Swap:          7.4Gi
```


---

 ``` {.sh}
free -b
```

``` {echo}
               total        used        free      shared  buff/cache   available
Mem:     33449861120  2646781952 22604738560   785178624  8198340608 29546471424
Swap:     7999582208  
```

---




 ``` {.sh}
free -m
```

Çıktı :

``` {echo}
               total        used        free      shared  buff/cache   available
Mem:           31900        2533       21533         763        7833       28154
Swap:           7628           0        7628
```
---

 ``` {.sh}
free -g -t
```

Çıktı:

```
               total        used        free      shared  buff/cache   available
Mem:              31           2          21           0           7          27
Swap:              7           0           7
Total:            38           2          28
```



---
 ``` {.sh}
free -h --lohi
```
Çıktı:

``` {echo}
               total        used        free      shared  buff/cache   available
Mem:            31Gi       2.5Gi        21Gi       744Mi       7.6Gi        27Gi
Low:            31Gi        10Gi        21Gi
High:             0B          0B          0B
Swap:          7.4Gi          0B       7.4Gi
```

---

 ``` {.sh}
free --count=3
```

Çıktı:

``` {echo}
               total        used        free      shared  buff/cache   available
Mem:        32665880     2582960    22079032      760860     8003888    28861488
Swap:        7812092           0     7812092

               total        used        free      shared  buff/cache   available
Mem:        32665880     2583472    22077624      761756     8004784    28860080
Swap:        7812092           0     7812092

               total        used        free      shared  buff/cache   available
Mem:        32665880     2584136    22077196      761520     8004548    28859652
Swap:        7812092           0     7812092
```

---

</br>

>Bellek durumu bilgisini detaylı almak için **meminfo** dosyasını görüntüleyebiliriz.

</br>

``` {.sh}
cat /proc/meminfo
```


</br>



</br>

---

 [Sistem&durum bilgisi komutları -hostname-](./tr_komutlar-sistem-durum-bilgisi-komutlari-hostname-.md) << Önceki / Sonraki >> [Sistem&durum bilgisi komutları -free-](./tr_komutlar-sistem-komutlari-free-.md)

