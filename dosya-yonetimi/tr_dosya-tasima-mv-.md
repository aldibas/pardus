# **Terminal & Kabuk -Shell- Komutları**

## Dosya Yönetimi

### Dosya Taşıma -mv-

</br>

"**mv**" komutu;  Linux ve diğer Unix tabanlı işletim sistemlerinde dosyaları veya dizinlerin konumlarını değiştirmek veya yeniden adlandırmak için kullanılır.

>Taşıma işlemini aynı depolama birimi üzerinde yapıldığında sadece dosya sistemi dizinindeki kayıtların güncellemesi ile gerçekleştiği için veriler fiziksel olarak kopyalanmaz. Bu sebeple taşıma işlemi, özellikle veri boyutu büyüklüğü ile orantılı olarak kopyalama işleminden daha hızlıdır.

Taşıma işleminde kopyalanacak verilerin adresi -**kaynak/source**- ve kopyalanacağı konum -**hedef/dest**- belirtilmelidir.


</br>

**Komutun dizilimi;**

``` {echo}
mv [OPTIONS] SOURCE DEST
```

<br>

Seçenekler: -**OPTIONS**- [-TviStbfnuZ --backup --help ] 

| Seçenek | | Açıklama |
|--|:--:|:--|
| -f, --force | » | Hedefte aynı isimde dosya var ise üzerine yazma onayı istemez. |
| -s, --suffix= | » | Hedefte aynı isimde dosya varsa dosyanın **son-ek** ile yedeğini alır. |
| -i, --interactive | » | Hedefte aynı isimde dosya varsa üzerine yazmadan önce kullanıcıya sorar. |
| -u, --update | » | Hedefte aynı isimde daha yeni dosya var ise o dosyayı atlayarak kopyalama yapar. |
| -v, --verbose | » | İşlem yapılan dosyaları çıktı olarak listeler. |
||

</br>

**Örnekler:**

Ev -"**home**"- dizinimizin içeriğini uzun liste biçiminde listeleyelim. 
(Aşağıdaki liste yok ise bu dosyaları ve dizini, "**cd && mkdir debian && touch GNU-Linux pardus.txt debian/pardus.txt debian/GNU-Linux**" yazarak oluşturun. )

``` {.sh}
ls -lR ~
```

Dosya listemiz:

``` {.echo}
.:
drwxrwxr-x 2 senol senol  4096 Feb 22 10:35 debian
-rwxrw-r-- 1 senol senol     0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 root  pardus    0 Feb 21 11:11 pardus.txt

./debian:
-rwxr--r-- 1 senol senol 0 Feb 22 09:57 GNU-Linux
-rw-r--r-- 1 senol senol 0 Feb 22 10:39 pardus.txt
```

Çıktıda görüleceği üzere çalışma dizininde (**.**)  "debian" dizini ve 2 adet dosya var ve bu dosyalar aynı zamanda debian dizinin içerisinde de mevcut.

Aşagıdaki mv komutu örneklerini bu yapı üzerinde uygulayabiliriz...


Çalışma dizinindeki "pardus.txt" dosyasının adını "Pardus.txt" olarak değiştirelim:

``` {.sh}
mv pardus.txt Pardus.txt
```

Alt dizin içerikleri ile birlikte listeleyelim.

``` {.sh}
ls -R
```

Çıktı:

``` {.echo}
.:
debian  GNU-Linux  Pardus.txt

./debian:
GNU-Linux  pardus.txt
```

"**tree**" komutu ile de dosya konumlarını görüntüleyebiliriz. (tree komutu sisteminizde yok ise **apt install tree** ya da **sudo apt install tree** komutu ile kurabilirsiniz.) 

</br>

``` {.sh}
tree
```


``` {echo}
.
├── debian
│   ├── GNU-Linux
│   └── pardus.txt
├── GNU-Linux
└── Pardus.txt

1 directory, 4 files
```


"P" veya "G" ile başlayan dosyaları "debian" dizinine taşıyalım.

``` {.sh}
mv -v [GP]* debian
```

</br>

Alt dizin içerikleri ile birlite listeleme yapalım.

``` {.sh}
ls -R
```

Çıktı:

``` {.echo}
.:
debian

./debian:
GNU-Linux  pardus.txt  Pardus.txt
```
</br>

"**tree***" komutu ile çıktıyı alabiliriz.

``` {.sh}
tree
```

Çıktı:

``` {echo}
.
└── debian
    ├── GNU-Linux
    ├── pardus.txt
    └── Pardus.txt

1 directory, 3 files
```
</br>

>Bu örnekteki "**mv**" komutunda "GNU-Linux" dosyası hedefte de olmasına karşın onay istenmeden üzerine yazılmıştır. "**-i**" parametresi ile hedef dosyanın değiştirilmesi kullanıcı onayına sunulabilir.

</br>

>Hedef dosyaları korumanın diğer bir yolu ise "**-s / --suffix**" seçeneğini kullanmaktır.

</br>

Örnek : 

"GNU-Linux" isminde bir dosya oluşturalım.

``` {.sh}
touch GNU-Linux
```

``` {.sh}
touch GNU-Linux
```

Listeleme için "**ls**" ya da "**tree**"

``` {.sh}
tree
```

Çıktı:

``` {echo}
.
├── debian
│   ├── GNU-Linux
│   ├── pardus.txt
│   └── Pardus.txt
└── GNU-Linux

1 directory, 4 files
```

Çalışma dizinimizdeki "**GNU-Linux**" dosyasını "**debian**" dizinine taşıyalım ancak hedefteki "**GNU-Linux** dosyasının üzerine yazılmasın. Bu işlende kullancağımız **suffix** seçeneği **-S 'sonek'** ile kısaca ya da **--suffix='sonek'** şeklinde uzun olarak yazılabilir.

``` {.sh}
mv --suffix='.SNL' GNU-Linux debian
```

Listeleme için "**ls**" ya da "**tree**"

``` {.sh}
tree
```

Çıktı:

``` {echo}
.
└── debian
    ├── GNU-Linux
    ├── GNU-Linux.SNL
    ├── pardus.txt
    └── Pardus.txt

1 directory, 4 files
```

Bu örnekte hedefte var olan "**GNU-Linux**" dosyasının ismi belirtilen **son-ek**'e göre değiştirilerek olası bir bilgi kaybı önlendi.

---


</br>

>Dikkat edilmesi gereken bir nokta, **mv** komutu dosya veya dizinleri taşırken üzerine yazma işlemi yapar. Bu nedenle, var olan bir dosya veya dizinin üzerine taşıma yaparken dikkatli olunmalıdır.

>**mv** komutu dosya ve dizinlerin izinlerini değiştirmez, yani kaynak dosyanın izinleri hedef konuma taşındığında aynen kalır.


</br>

---
 [Dosya Yönetimi / Dosya Kopyalama -cp- ](tr_dosya-kopyalama-cp-.md) << Önceki / Sonraki >> [Dosya Yönetimi -Dosya/Dizin Silme- -rm- / -rmdir-](./tr_dosya-ve-dizin-silme-rm-rmdir-.md)

