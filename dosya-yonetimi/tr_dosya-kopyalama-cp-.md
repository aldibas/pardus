# **Terminal & Kabuk -Shell- Komutları**

## Dosya Yönetimi

### Dosya Kopyalama -cp-

</br>

"**cp**" komutu; dosya/dizin kopyalamak için kullanılan komuttur.

Kopyalama işleminde kopyalanacak verilerin adresi -**kaynak/source**- ve kopyalanacağı konum -hedef/dest- belirtilmelidir.


</br>

**Komutun dizilimi;**

``` {echo}
cp [OPTIONS] SOURCE DEST
```

<br>

Seçenekler: -**OPTIONS**- [-istanbulTRrSHLpdfxvZ --backup --parents ] 

| Seçenek | | Açıklama |
|--|:--:|:--|
| -R, -r, --recursive | » | Alt dizilerle birlikte kopyalar. |
| -l, --link | » | Kopyalamak yerine bağ oluşturur. |
| -s, --symbolic-link | » | Kopyalamak yerine sembolik bağ oluşturur. |
| -i, --interactive | » | Hedefte aynı isimde dosya varsa üzerine yazmadan önce kullanıcıya sorar. |
| -u, --update | » | Hedefte aynı isimde daha yeni dosya var ise o dosyayı atlayarak kopyalama yapar. |
| --parents | » | kaynakta belirtilen yolu hedefte oluşturarak kopyalar.|
| -v, --verbose | » | İşlem yapılan dosyaları çıktı olarak listeler. |
||

</br>

**Örnekler:**

Ev -"**home**"- dizinimizin içeriğini uzun liste biçiminde listeleyelim. 
(Aşağıdaki liste yok ise bu dosyaları ve dizini, "**cd && touch GNU-Linux pardus.txt && mkdir debian**" yazarak oluşturun. )

``` {.sh}
ls -l ~
```

Dosya listemiz:

``` {.echo}
drwxrwxr-x 2 senol senol  4096 Feb 22 01:45 debian
-rwxrw-r-- 1 senol senol     0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 root  pardus    0 Feb 21 11:11 pardus.txt
```

Buradaki "GNU-Linux" dosyasını "debian" dizinine kopyalaylalım. 

``` {.sh}
cp GNU-Linux debian
```

Komut çalıştırıldığında herhangi bir çıktı üretmemiş ise kopyalama işlemi gerçekleşmiştir. Elbette işlem yapılan dosya listesini "***--verbose (-v)**" ile alabilirdik.  

İşlemin sonucunu görmek için detaylı dosya listesini alt dizinler (**-R**) ile birlikte alalım.

``` {.sh}
ls -lR
```

``` {.echo}
.:
drwxrwxr-x 2 senol senol  4096 Feb 22 09:57 debian
-rwxrw-r-- 1 senol senol     0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 root  pardus    0 Feb 21 11:11 pardus.txt

./debian:
-rwxr--r-- 1 senol senol 0 Feb 22 09:57 GNU-Linux
```

---

</br>

"pardus.txt" dosyasını mutlak "**absolute**" adresiniadresleri belirterek debian dizinine kopyalamak için "**cp /home/senol/pardus.txt /home/senol/debian**" gibi tam adresleri yazmamız gerekir. Elbette burada ev dizini için "**~**" karakterini kullanarak "**cp ~/pardus.txt ~/debian**" şeklinde yazabiliriz.


``` {.sh}
cp /home/senol/pardus.txt /home/senol/debian
```

Bu örnekte kullanıcı adından kaynaklı dosya adreslerinin her kullanıcıda farklı olacağı aşikardır. Bu sebeple komutu şu şekilde yazmak daha uygun olabilir.

``` {.sh}
cp ~/pardus.txt ~/debian
```

Farklı bir yazım şekilleri:

``` {.sh}
cp $(pwd)/pardus.txt debian
```

``` {.sh}
cp ./pardus.txt ./debian
```

Kopyalama işleminin sonucu için listeleyelim.

``` {.sh}
ls -R
```

Çıktı :

``` {echo}
.:
debian  GNU-Linux  pardus.txt

./debian:
GNU-Linux  pardus.txt
```

>Bu örneklerde kendi ev dizinimizde sahibi ve grubu farklı olan bu dosyayı kopyalayabildiğimize dikkat edelim.

</br>

---

</br>

"GNU-Linux" dosyasını belirttiğimiz yolu -adresi- ile "/tmp" dizinine kopyalaylalım. 

``` {.sh}
cp --parents ~/GNU-Linux /tmp
```

/tpm dizininin içeriğini listelediğimizde burada ev dizinimizin oluştuğunu görürüz.

``` {.sh}
ls /tmp
```


``` {echo}
home
```

Kopyalama işleminin sonucunu daha net görmek için "/tmp" konumuna **tree** komutu ile bakabiliriz. (tree komutu sisteminizde yok ise **apt install tree** ya da **sudo apt install tree** komutu ile kurabilirsiniz.) 


``` {.sh}
tree
```

``` {echo}
/tmp
└── home
    └── senol
        └── pardus.txt

2 directory, 1 file
```

---
</br>

>**-R/-r** parametreleri ile dizinleri de kopyalayabiliriz.

</br>

"**debian**" dizinini /tmp dizinine **-R/-r** seçeneği **olamadan** kopyalamayı deneyelim: 


``` {.sh}
cp debian /tmp
```

Alacağımız hata çıktısı:

**cp: -r not specified; omitting directory 'debian'**

</br>

>Bu kullanımda elbette sadece "**debian**" yazmak yerine "**debian/***" şeklinde yazmış olsaydık debian dizininin **içeriği** /tmp altına kopyalanacaktı. "**debian**" dizininin kendisini kopyalamak için  **-R/-r** opsiyonu gereklidir.


``` {.sh}
cp -R debian /tmp
```

İşlem sonucunu görüntülemek için "**tree**" komutunu kullanalım:

``` {.sh}
tree /tmp
```

Çıktı: 

``` {echo}
/tmp
├── debian
│   ├── GNU-Linux
│   └── pardus.txt
└── home
    └── senol
        └── pardus.txt

3 directories, 3 files
```

</br>

---
 [Dosya Yönetimi / Sahiplik ve Grup Değiştirme -chown-chgrp- ](tr_dosya-yonetimi-listeleme-ls-.md) << Önceki / Sonraki >> [Dosya Yönetimi -Taşıma- -mv-](./tr_dosya-tasima-mv-.md)

