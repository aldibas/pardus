## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **free** 


</br>

**free** komutu; bellek -**RAM**- durum ve takas alanı -**swap**- ile ilgili bilgi verir.

</br>



``` {.sh}
free
```

<br>

Çıktı:

``` {echo}
               total        used        free      shared  buff/cache   available
Mem:        32665880     2397756    22341936      716292     7926188    29092484
Swap:        7812092           0     7812092
```

</br>


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

 [Sistem & durum bilgisi komutları -hostname-](./tr_komutlar-sistem-durum-bilgisi-komutlari-hostname-.md) << Önceki / Sonraki >> [Sistem & durum bilgisi komutları -free-](./tr_komutlar-sistem-komutlari-df-.md)

