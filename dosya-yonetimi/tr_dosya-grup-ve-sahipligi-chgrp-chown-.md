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
| -c, --changes | » | Dosya sahipliği ya da grup bilgisi değişmemişse çıktıya yazmaz. |
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

Sahip ve grup değişikliğini örneklemek için "pardus" isminde kullanıcı ekleyelim. 

``` {.sh}
adduser pardus
```
</br>

>Kullanıcı ekleme yetki gerektiren bir işlem olduğundan kendi bilgisayarınızda uygularken "**su**" komutu ile "**root**" kullanıcısına geçebilir ya da komutu başına "**sudo**" yazarak (**sudo adduser pardus**) kullanabilirsiniz.

Oluşturulan kullanıcıyı görmek için ana dizinde -**kök"/"**- bulunan "**etc**" dizini içerisindeki kullanıcı dosyasının -"**passwd**"- içeriğini "**cat**" komutu ile görüntüleyebiliriz.

Burada çıktıyı kısa görüntülemek için "**tail**" ve "**grep**" komutlarını kullanalım: 


``` {.sh}
tail -2 /etc/passwd
```

Çıktı: Dosya sonundaki son 2 satır. 

``` {echo}
messagebus:x:101:101::/nonexistent:/usr/sbin/nologin
pardus:x:1000:1000:,,,:/home/pardus:/bin/bash
```
2. Yöntem:

"**pardus**" ifadesini içeren satırlar. 

``` {.sh}
grep pardus /etc/passwd
```

Çıktı: 

``` {echo}
pardus:x:1000:1000:,,,:/home/pardus:/bin/bash
``` 

Bu kullanıcı ekleme işlemi esnasında aynı zamanda "pardus" isminde bu grup eklendiğine dair bilgi de almıştık. Şimdi "group" dosyasının içeriğine göz atalım:

``` {.sh}
tail -3 /etc/group
```

``` {echo}
mlocate:x:102:
ssh:x:103:
pardus:x:1000:
```

Kullanıcı ekleme işlemini tamamladığımıza göre konumuza geri dönelim ve "pardus.txt" dosyasının sahiplik bilgisini "**pardus**" kullanıcısı olarak değiştirelim.

``` {.sh}
chown pardus pardus.txt
``` 

>Dosya sahipliği değiştirme  yetki gerektiren bir işlem olduğundan kendi bilgisayarınızda uygularken "**su**" komutu ile "**root**" kullanıcısına geçebilir ya da komutu başına "**sudo**" yazarak (**sudo chown pardus pardus.txt**) kullanabilirsiniz.

Değişikliği görmek için dosyaları tekrar listeleyelim.

``` {.sh}
ls -l
``` 



``` {echo}
drwxrwxr-x 2 senol  senol 4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol  senol    0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 pardus senol    0 Feb 21 11:11 pardus.txt
```

"**chown**" komutu ile dosyanın grup bilgisini de değiştirebiliriz.

``` {.sh}
chown :pardus pardus.txt
``` 

``` {echo}
drwxrwxr-x 2 senol  senol 4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol  senol    0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 pardus pardus    0 Feb 21 11:11 pardus.txt
```

Bu değişiklikleri aynı anda da yapabilirdik. "**pardus:pardus**" ya da "**pardus.**" şeklinde gösterim hem sahiplik hemde grup bilgisini "**pardus**" olarak değiştirecekti.

>sahiplik ve grup bilgilerini aynı bilgi ile değiştirilecek ise  bilgiden sonra sadece "**.**" konularak işlem yapılabilir. "**pardus.**" gibi.

Yukarıda bilgilerini değiştirdiğimiz "pardus.txt" dosyasının sahibini ve grubunu "**root**" olarak değiştirelim.

``` {.sh}
chown root. pardus.txt
``` 

"**ls -l**" ile takrar listelediğimizde çıktı:

``` {echo}
drwxrwxr-x 2 senol senol 4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol senol    0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 root  root     0 Feb 21 11:11 pardus.txt
```
</br>

#### **chgrp (CHange GRouP)**
</br>

**chgrp** -change group- komutu dosya ve dizinlerin grubunu değiştirmek için kullanılar. 


**Komutun dizilimi;**

``` {echo}
chgrp [OPTIONS] GROUP  FILE...
```

<br>

Seçenekler: -**OPTIONS**- [-cfRvHLP --help --version ] 

| Seçenek | | Açıklama |
|--|:--:|--|
| -R, --recursive | » | Alt dizilerin içeriklerini de işleme dahil eder. |
| -c, --changes | » | Dosyanın grup bilgisi değişmemişse çıktıya yazmaz. |
| -f, --silent | » | Çoğu hatayı çıktıya yazmaz. |
| -v, --verbose | » | İşlem yapılan dosyaları çıktı olarak listeler. |
||

</br>

---

Konuyu tekrar bir çıktı üzerinden alalım :

Bir önceki konuda oluşturduğumuz doslayarın listesini "**ls -l**" komutu ile alalım.

``` {echo}
drwxrwxr-x 2 senol senol 4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol senol    0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 root  root     0 Feb 21 11:11 pardus.txt
```

Bu çıktıdaki 4. alan -sütun- dosyaların grup bilgileridir. Bu listedeki "pardus.txt" dosyasının grubunu "pardus" olarak  değiştirelim. ("pardus" grubu pardus kullanıcısını eklediğimizde oluşmuştu.)

``` {.sh}
chgrp pardus pardus.txt
```
</br>

>Dosya grubunu değiştirme  yetki gerektiren bir işlem olduğundan kendi bilgisayarınızda uygularken "**su**" komutu ile "**root**" kullanıcısına geçebilir ya da komutu başına "**sudo**" yazarak (**sudo chgrp pardus pardus.txt**) kullanabilirsiniz.

Değişikliği görmek için:

``` {.sh}
ls -l
``` 

>Dosya sahipliği değiştirme  yetki gerektiren bir işlem olduğundan kendi bilgisayarınızda uygularken "**su**" komutu ile "**root**" kullanıcısına geçebilir ya da komutu başına "**sudo**" yazarak (**sudo chown pardus pardus.txt**) kullanabilirsiniz.

Değişikliği görmek için dosyaları tekrar listeleyelim.

``` {.sh}
ls -l
```

``` {echo}
drwxrwxr-x 2 senol senol  4096 Feb 21 11:11 debian
-rwxrw-r-- 1 senol senol     0 Feb 21 00:29 GNU-Linux
-rw-rw-r-- 1 root  pardus    0 Feb 21 11:11 pardus.txt
```
---
</br>

>Yukarıdaki örnekleri "**-R**" parametresi ile alt dizin içeriklerinde geçerli olacak şekilde yazabilirsiniz. Ancak dikkatli kullanmanız gereken bir parametre olduğunu unutmayın.

</br>

----
 [ Dosya Yönetimi / Dosya Erişim İzinlerini Belirleme ](./tr_dosya-erisim-izinleri-chmod-.md) << Önceki / Sonraki >> [Dosya Yönetimi / Dosya Kopyalama -cp-](./tr_dosya-kopyalama-cp-.md)