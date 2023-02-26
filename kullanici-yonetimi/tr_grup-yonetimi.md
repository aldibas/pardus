# **Terminal & Kabuk -Shell- Komutları**

## Grup Yönetimi

</br>

Kullanıcılar, birden fazla gruba üye olabilir. Bu gruplar, bir dosya veya dizinin izinlerini belirlemek için kullanılabilir. Kullanıcıların hangi gruba dahil olduğunu kontrol etmek için `groups` komutu kullanılır.




>Kullanıcı grupları  **/etc** dizinindeki **group** dosyasındadır.

``` {.sh}
cat /etc/group
```



"**group**" dosyasından örnek bir satır -kayıt-.

``` {echo}
root:x:0:
sudo:x:27:senol
audio:x:29:pulse,senol
lpadmin:x:118:senol
senol:x:1000:
```


> `man 5 passwd` komutu ile dosya içeriği ile ilgili detaylı bilgi alabilirsiniz.


</br>
---
</br>


### Grup Ekleme



Grup eklemek için **groupadd**, silmek için de **groupdel** komutu kullanılır. **groupadd** komutu otomatik olarak sıradan bir Grup numarası **(GID)** atar. Farklı bir GID vermek için **-g** parametresi kullanılır.


``` {.sh}
groupadd sistemci
```

komutu ile **sistemci** siminde bir gurup oluşturalım.

``` {.sh}
usermod -G sistemci cuneyt
```

komutu ile **cuneyt** kullanıcısını **sistemci** gurubuna dahil edelim.


``` {.sh}
id cuneyt
```
komutu ile **cuneyt** kullanıcısının dahil olduğu gurupları görelim:

Komut çıktısı:
``` {.echo}
uid=1000(cuneyt) gid=1000(cuneyt) groups=1000(cuneyt),1001(sistemci)
```








</br>

---
</br>



Örnek olarak **muhasebe** ve **bilgiislem** guruplarını oluşturalım ve **senol** kullanıcısını **muhasebe** ve **bilgiislem** gurubuna ekleyelim.

``` {.sh}
addgroup muhasebe
```
komutu ile **muhasebe** gurubunu oluşturalım.

Komut çıktısı:

``` {.echo}
Adding group `muhasebe' (GID 1000) ...
Done.
```

``` {.sh}
addgroup bilgiislem
```
komutu ile **bilgiislem** gurubunu oluşturalım.

Komut çıktısı:
``` {.echo}
Adding group `bilgiislem' (GID 1001) ...
Done.
```

Aşağıdaki komut ile **senol** kullanıcısını **muhasebe** ve **bilgiislem** gurubuna dahil edelim.
``` {.sh}
usermod -G muhasebe,bilgiislem senol
```

``` {.sh}
groups senol
```
komutu ile **senol** kullanıcısını guruplarını kontrol edelim.

``` {echo}
senol : senol muhasebe bilgiislem
```


