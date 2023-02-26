## **Terminal & Kabuk -Shell- Komutları**

### Depolama Birimleri 

#### **lsblk** -LiSt **BLock**- 


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


---
</br>




#### **df -D**isk **F**ree- 


</br>

**df** komutu; dosya sisteminde blok aygıtlarının durumunu görüntüler.

</br>



``` {.sh}
df
```

<br>

Çıktı:

``` {echo}
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/nvme0n1p1 191134604 160330388  21022252  89% /
/dev/nvme1n1   491135216 249284088 216829364  54% /mnt/storage
/dev/sdb1        2373328   2373328         0 100% /media/senol/Pardus
```

</br>

>Bu çıktıda disk dosyalarımız / bölümlerimiz **"/dev"** altında olup diskin bağlı olduğu veri yoluna göre -yuva- / türe göre isimlendirilirler. Bu isimlendirmelere **lsblk**, **blkid** gibi konularda değineceğiz.

Yukarıdaki çıktıda sütunlar şu şelikdedir.
<br>
|||||||
|:--:|:--:|:--:|:--:|:--:|:--:|
|Dosya Sistemi|Boyut|Kullanılan Alan| Kullanılabilir Alan| Kullanım Oranı|Bağlama noktası|
||



**Komutun dizilimi;**

```
<command>  [OPTIONS] [FILE]
```

Komut seçenekleri: -**OPTIONS**- [-TaklitBhHpxv --output=[FIELD_LIST] --sync ]

| Seçenek | | Açıklama |
|--|:--:|--|
| -h, --human-readable | » | Kapasite verilerini birimlere dönüştürerek -**kolay okunablir**-  görüntüler. **16G, 20M, 10K**  |
| -i, --inodes | » | Her bölümün inode sayısını görüntüler. |
| -T, --type | » | Bölümlerin tipini görüntüler. |
| --sycn | » | Önce senkronizasyon yapar. | 
|||

</br>

**Örnekler:**

</br>

Kapasite verilerini kolay okunabilir görüntülemek için:

 ``` {.sh}
df -h
```

Çıktı :

``` {echo}
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  2.0M  3.2G   1% /run
/dev/nvme0n1p1  183G  153G   21G  89% /
/dev/nvme1n1    469G  238G  207G  54% /mnt/storage
/dev/nvme0n1p2  953M  152K  952M   1% /boot/efi
/dev/sdb1       2.3G  2.3G     0 100% /media/senol/Pardus
```

---
Dosya sistemleri için "**tür/type**" bilgisi ekleyerek görüntüleme:

 ``` {.sh}
df -T
```

``` {echo}
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs   16G     0   16G   0% /dev
tmpfs          tmpfs     3.2G  2.0M  3.2G   1% /run
/dev/nvme0n1p1 ext4      183G  153G   20G  89% /
/dev/nvme1n1   ext4      469G  238G  207G  54% /mnt/storage
/dev/nvme0n1p2 vfat      953M  152K  952M   1% /boot/efi
/dev/sdb1      iso9660   2.3G  2.3G     0 100% /media/senol/Pardus
```
---
Dosya sistemlerini indeks sayısı "**-inode-**" ile görüntüleme:

``` {.sh}
df -i
```

Çıktı :

``` {echo}
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            4072798    580  4072218    1% /dev
tmpfs           4083235   1121  4082114    1% /run
/dev/nvme0n1p1 12214272 868495 11345777    8% /
/dev/nvme1n1   31260672    565 31260107    1% /mnt/storage
/dev/nvme0n1p2        0      0        0     - /boot/efi
/dev/sdb1             0      0        0     - /media/senol/Pardus
```

---

</br>

>Dosya sisteminizde bağlama noktalarını **/proc/mounts** iceriği ile  görüntüleyebilsiniz.

</br>

``` {.sh}
cat /proc/mounts
```





</br>

---



