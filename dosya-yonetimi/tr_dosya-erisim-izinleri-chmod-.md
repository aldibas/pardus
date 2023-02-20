# **Terminal & Kabuk -Shell- Komutları**

## Dosya Yönetimi

### **Dosya Erişim İzinleri -chmod-** 


Linux yetkilendirme modeli, UNIX ve BSD’den alınmıştır.


**chmod** -change mode- komutu dosya ve dizinlerin erişim izinlerini belirlememiz sağlar. Bu işlemi **octal** -sekizlik- değerler ya da  semboller (**r, w, x, t, s**) ile belirterek yapabiliriz.



</br>

**Komutun dizilimi;**


```
chmod [OPTIONS] [MODE] [FILE]...
```

<br>

Seçenekler: -**OPTIONS**- [-cfRv] 

| Seçenek | | Açıklama |
|--|:--:|--|
| -R, --recursive | » | Alt dizilerin içeriklerini de işleme dahil eder. |
| -c, --changes | » | dosya izinleri değişmemişse çıktıya yazmaz. |
| -f, --silent | » | Çoğu hatayı çıktıya yazmaz. |
| -v, --verbose | » | İşlem yapılan dosyaları çıktı olarak listeler. |
||

</br>

**MODEs**

"**rwxr-xr-x**" gösterimini sahiplik -User-, grup -Group- ve diğer -Others- olarak gruplamıştık. Bunların tamamını birden ifade etmek için "**a**" -all users- sembolünü de ekleyebiliriz.

* **u** : User
* **g** : Group 
* **o** : Others 
* **a** : All users


</br>

Permissions / izinler: -MODEs- [ ugoa ] [ +-= ] [ permissions : rwx ] [ tsTS ]

Permissions / izinler: -MODEs- [ octal ]



* **r** : Read -okuma-
* **w** : Write -yazma- 
* **x** : eXecute -çalıştırma- 
* **s** : SUID -Set User ID- / SGID -Set Group ID-
* **t** : Sticky Bit



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


</br>



----
 [Dosya Yönetimi / Listeleme -ls- ](tr_dosya-yonetimi-listeleme-ls-.md) << Önceki / Sonraki >> [Dosya Yönetimi -Kopyalama- -cp-](./tr_dosya-yonetimi-dosya-kopyalama-cp-.md)