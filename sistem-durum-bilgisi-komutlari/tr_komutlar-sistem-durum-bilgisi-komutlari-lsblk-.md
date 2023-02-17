## **Terminal & Kabuk -Shell- Komutları**

### Sistem&Durum Bilgisi Komutları 

#### **lsblk** LiSt **BLock**- 


</br>

**lsblk** komutu; disklerimizi bölümleri -**partition**- ile listeler.

Bu listede;
* Disk dosyası adı, **- sd\* / nvme\* / ... -**
* Tipi, - **0 / 1** -
* Boyutu, - **size** -
* Bağlanma noktası </br>
bilgileri bulunur.

</br>


``` {.sh}
lsblk
```

<br>

Çıktı:

``` {echo}
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1     259:0    0 476.9G  0 disk 
├─nvme0n1p1 259:2    0 186.3G  0 part /
├─nvme0n1p2 259:3    0   954M  0 part /boot/efi
├─nvme0n1p3 259:4    0   7.5G  0 part [SWAP]
nvme1n1     259:1    0 476.9G  0 disk /mnt/storage

```

</br>

>Disk dosyalarımız **"/dev"** altında olup diskin bağlı olduğu  isimlendirilirler. 

Linux sistemler, diskleri adlandırmak için genellikle SCSI (Small Computer System Interface) veya ATA (Advanced Technology Attachment) arabirimlerini kullanır. Bu arabirimler aracılığıyla bağlı olan diskler, bir numara ile belirtilir. Örneğin, ilk disk sda (SCSI disk a) olarak adlandırılırken, ikinci disk sdb (SCSI disk b) olarak adlandırılır.

Daha yeni sürümlerde NVMe (Non-Volatile Memory Express) arabirimli diskler de kullanılmaya başladı. NVMe diskler genellikle "nvmeXnY" olarak adlandırılır, burada "X" bir sayıdır ve sistemin kaçıncı NVMe arabirimli diski olduğunu belirtir. "nY" kısmı ise, NVMe diskteki parçaları (partition) belirler.

Disklerin adlandırılması, disklerin bağlı olduğu arabirimlerin sıralamasına ve disklerin sisteme hangi sırayla bağlandığına bağlı olarak değişebilir. Bu nedenle, disklerin adlandırılması sisteme göre değişkenlik gösterebilir.



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

