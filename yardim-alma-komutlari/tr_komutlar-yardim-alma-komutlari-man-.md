## **Uçbirim Komutları**

### Yardım Alma Komutları 

#### **man** 


</br>

Manual ifadesinin kısaltması olan **man** komutu;
* Kabuk komutları ve uygulamalar (1),
* Sistem çağrıları -işlevleri-(2), 
* Kütüphane çağrıları (3),
* Özel dosyalar -/dev- (4) 
* Dosya biçimleri (5),
* Oyunlar (6),
* Makro paketleri (7),
* Yönetici -root- yetkisi isteyen komutlar (8),
* Çekirdek rutinleri (9)

konularında kılavuz dosyalarını görüntüler. Bu kılavuz dosyalarının konumuna **whereis** komutu ile bakabiliriz. **man** komutu bu dosyaları biçimli şekilde görüntüleyecektir. 

>**man** komutu için kısaca "**yardım alma komutu**" diyebiliriz.

**man** komutu kakkında yardım almak için,

```
man man
```

komutunu kullanabilirsiniz.

Kılavuz dosyasından **q** ile çıkış yapabilirsiniz.

Komutun dizilimi;
```
man [options] [section/part number] \ <command/file/işlev>
```

>Çalıştırılabilir komut yardımları için section kısmı yazılmak zorunda değildir.

Örneğin,  

``` {.sh}
man ls
```

ile 

``` {.sh}
man 1 ls
```

kullanımları **ls** komutunun klavuz dosyasını görüntüleyecektir. 


Komut dizilimindeki "**section**" alanının öneminin kavranması için aşağıdaki örneği inceleyebiliriz.

---

***/etc/passwd** dosyası, kullanıcı listesinin bulunduğu dosya, **/usr/bin/passwd** ise parola değiştirme komutudur.

Parola değiştirme komutu hakkında yardım almak için:

``` {.sh}
man passwd
```

Kullanıcı verilerini içeren dosya hakkında bilgi almak için:


``` {.sh}
man 5 passwd
```
---

<br>

Komut seçenekleri : -**OPTIONS**- [a,c,d,D,f,k,K,l,i,I,.....]

| Desen | | Anlamı |
|:--:|:--:|--|
| -f, --whatis | » | Kılavuz dosyasının **TANIM** kısmını -kısa bilgi- görüntüler.|
| | » |  |
|  | » |  |
|  | » |  |



<br>

<div style="color:red;"> 

.

</div>

---


</br>

 [Dosya adları ve Joker karakterler](../terminal-kullanimi/tr_dosya-adlari.md) << Önceki / Sonraki >> [Yardım alma komutları -man-](./.md)

