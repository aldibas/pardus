# **Terminal & Kabuk -Shell- Komutları**

## Dosya Yönetimi

### **Dosya Gurubu ve Sahipliğini Belirleme -chgrp & chown-** 

</br>

#### chown (CHange OWNer)

**chown** -change owner- komutu dosya ve dizinlerin sahiplik ve grubunu belirlememizi sağlar. 



</br>

**Komutun dizilimi;**


``` {echo}
chown [OPTIONS] [OWNER][:[GROUP]]  FILE...
```

<br>

Seçenekler: -**OPTIONS**- [-cfRvHLP --from= --help ] 

| Seçenek | | Açıklama |
|--|:--:|--|
| -R, --recursive | » | Alt dizilerin içeriklerini de işleme dahil eder. |
| -c, --changes | » | dosya izinleri değişmemişse çıktıya yazmaz. |
| -f, --silent | » | Çoğu hatayı çıktıya yazmaz. |
| -v, --verbose | » | İşlem yapılan dosyaları çıktı olarak listeler. |
||

</br>

Konuyu bir çıktı üzerinden alalım :

Bir önceki konuda oluşturduğumuz doslayarın listesini "**ls -l**" komutu ile alalım.


``` {echo}
drwxrwxr-x 2 senol senol 4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol senol    0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 senol senol    0 Feb 21 11:11 pardus.txt
```

Bu çıktıdaki 3. ve 4. alanların sırasıyla dosyanın adı ve grubu bilgisi olduğundan bahsetmiştik.

Bu listedeki "pardus.txt" dosyasının sahipliğini değiştirelim. 




</br>


Konuyu örneklerle inceleyelim:



``` {.sh}

```



``` {.sh}

``` 

Çıktı:

``` {echo}
```











``` {.sh}

``` 



``` {echo}

```

<div style="color:red">


</div>

---



``` {.sh}

``` 

**ls -l** ile alınan çıktı:

``` {echo}

```



---



``` {.sh}

``` 

Sonuç:

``` {echo}

```



---



``` {.sh}

``` 

Çıktı **-c**:

``` {echo}
(rwxrw-r--)
```

Sonuç:

``` {echo}

```

>bu örnekte dosyanın mevcut izinleri değiştiği için "**-c**" parametresi işlem sonunda ekrana bilgi basmaktadır. Benzer bir çıktıyı "**-v**" seçeneği de sağlayacaktır. Ancak "**-v --verbose**", buradaki "**-c** seçeneğinden farklı olarak her durumda yapılan işlemle ilgili bilgi basar. -**stdout**-  

Çıktı **-v**:

``` {echo}

```

---


``` {.sh}

``` 

Çıktı:

``` {echo}
0022
```

UMASK değerimizi 0002 olarak değiştirelim.

``` {.sh}
umask 0002
``` 

Örnek bir dosya ve dizin oluşturalım:

``` {.sh}
touch pardus.txt && mkdir debian 
``` 

Dosya listesini **ls -l** ile detaylı aldığımızda aşağıdaki izinler listelenecektir.

``` {echo}
drwxrwxr-x 2 senol senol 4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol senol    0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 senol senol    0 Feb 21 11:11 pardus.txt
```

Bu listede **UMASK** değeri değiştirildikten sonra oluşturulan dosya ve dizinlerin erişim izinleri güncel **UMASK** değerine göre hesaplanmıştır.;

* pardus.txt dosyası (rw-rw-r--): 666 - 002 = 664 
* debian dizini (rwxrwxr-x): 777 - 002 = 775

</br>

>UMASK değerini kalıcı olarak değiştirilebilir ya da her kullanıcıya ayrı UMASK tanımlanabilir. Bu işlem için oturum açılırken okunan dosyaları kullanabilirsiniz.

</br>

>Yukarıdaki örnekleri "**-R**" parametresi ile alt dizin içeriklerinde geçerli olacak şekilde yazabilirsiniz. Ancak dikkatli kullanmanız gereken bir parametre olduğunu unutmayın.



----
 [ Dosya Yönetimi / Dosya Erişim İzinleri ](./tr_dosya-erisim-izinleri.md) << Önceki / Sonraki >> [Dosya Yönetimi / Dosya Grup ve Sahipliğinin Ayarlanması -chgrp- -chown-](./tr_dosya-grup-ve-sahipligi-chgrp-chown-.md)