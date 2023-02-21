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

"GNU-Linux" isminde bir dosya oluşturalım.

``` {.sh}
touch GNU-Linux
```

Bu dosyanın izinlerini görelim:

``` {.sh}
ls -l GNU-Linux
``` 

Çıktı:

``` {echo}
-rw-r--r-- 1 senol senol 0 Feb 21 00:29 GNU-Linux
```

Çıktıdan da "**rw-r--r--**" anlaşılacağı üzere bu dosyayı;

* Sahibi : sadece **okuyabilir** ve **yazabilir** ( r w - )
* Grup üyeleri : sadece    **okuyabilir** ( r - - )
* Diğer kullanıcılar : sadece  **okuyabilir** ( r - - )


>Dosyanın izinlerinin sekilik -**octal**- tabanda karşılığı **644** tür. Varsayılan -öntanımlı- izinler ve **UMASK** konusunu hatırlayalım. ( 666 - 022 = 644 )


Şimdi bu erişim izinlerini nasıl belirlediğimize göz atalım.

GNU-Linux dosyasının mevcut izinlerine tüm kullanıcılar için çalıştırma izni ekleyelim.





``` {.sh}
chmod +x GNU-Linux
``` 

Dosyanın izinlerinin son hali:

``` {echo}
-rwxr-xr-x 1 senol senol 0 Feb 21 00:29 GNU-Linux
```

<div style="color:red">

>Bir dosyaya tüm kullanıcılar için **çalıştırma(x)** ve **yazma(w)** yetkilerini vermek **kesinlikle yapılmaması** gereken bir işlemdir.

</div>

---

GNU-Linux dosyasının mevcut izinlerinden diğer kullanıcılar -**other users**- için **okuma(r)** ve **çalıştırma(x)** iznini kaldıralım.

``` {.sh}
chmod o-wx GNU-Linux
``` 

**ls -l** ile alınan çıktı:

``` {echo}
-rwxr-xr-- 1 senol senol 0 Feb 21 00:29 GNU-Linux
```

>Bu örnekte "**-**" karakteri ile mevcut haklardan belirtilen izinler **çıkartılır.** 

---

GNU-Linux dosyasının izinlerini **sahibi(u)** ve **grubu(g)** için "**okuyabilir**" ve "**yazabilir**" olarak değiştirelim.

``` {.sh}
chmod ug=rw GNU-Linux
``` 

Sonuç:

``` {echo}
-rw-rw-r-- 1 senol senol 0 Feb 21 00:29 GNU-Linux
```

>Bu örnekte "**=**" karakteri ile mevcut izinlere ilave ya da bu izinlerden eksiltme yapıpmayıp verilecek izinlerin "**son hali**" belirlenir.

---

GNU-Linux dosyasının izinlerini,
* sahibi için **okuyabilir**, **yazabilir** ve **çalıştırabilir** (111),
* grubundaki kullanıcılar için **yazabilir** ve **okuyabilir** (110),
* diğer tüm kullanıcılar için sadece "**okuyabilir**"(100) 

olacak şekilde sekizlik -**octal**- tabanda belirteyak ayarlayalım.


``` {.sh}
chmod 764 GNU-Linux
``` 

Çıktı **-c**:

``` {echo}
mode of 'GNU-Linux' changed from 0664 (rw-rw-r--) to 0764 (rwxrw-r--)
```

Sonuç:

``` {echo}
-rwxrw-r-- 1 senol senol 0 Feb 21 00:29 GNU-Linux
```

>bu örnekte dosyanın mevcut izinleri değiştiği için "**-c**" parametresi işlem sonunda ekrana bilgi basmaktadır. Benzer bir çıktıyı "**-v**" seçeneği de sağlayacaktır. Ancak "**-v --verbose**", buradaki "**-c** seçeneğinden farklı olarak her durumda yapılan işlemle ilgili bilgi basar. -**stdout**-  

Çıktı **-v**:

``` {echo}
mode of 'GNU-Linux' retained as 0764 (rwxrw-r--)
```

---
Örneklerimizi **UMASK** değerini değiştirerek çeşitlendirelim. 
Mevcut UMASK değeri:

``` {.sh}
umask
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