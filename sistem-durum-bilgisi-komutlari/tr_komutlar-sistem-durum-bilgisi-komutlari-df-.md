## **Terminal & Kabuk -Shell- Komutları**

### Sistem & Durum Bilgisi Komutları 

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

[](./md_images/Cinnamon-logo.svg-64.png)


</br>

---

 [Sistem & durum bilgisi komutları -free-](./tr_komutlar-sistem-durum-bilgisi-komutlari-free-.md) << Önceki / Sonraki >> [Sistem & durum bilgisi komutları -free-](./tr_komutlar-sistem-komutlari-free-.md)

