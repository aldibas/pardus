## **Terminal & Kabuk -Shell- Komutları**

### Dosya Yönetimi -Listeleme-

#### **ls** -LiSt-


</br>

**ls** dosya listeleme komutudur. Belirtilen konum ya da çalışma dizini içeriklerini alfabetik olarak listeler. Listelemeyi **boyut, tarih** gibi alanlara göre sıralanacak şekilde değiştirebiliriz.


``` {.sh}
ls
```

Bu kullanım var ise çalışma dizinindeki -**pwd**- dosyaları listeler. Dizinleri de "dosya" ile ifade edebilir ya da tanımı, "dosya ve dizinleri listeler" şeklinde belirtebiliriz.


</br>

**Komutun dizilimi;**


```
ls [OPTIONS] [FILE] ...
```

<br>

Komut seçenekleri : -**OPTIONS**- [-aAbBcCdDfFgGhHiIklLmnNopqQrRsStTuUvwxXz1] 

| Seçenek | | Açıklama |
|--|:--:|--|
| -a, --all | » | "**.**" ile başlayan dosyaları gizlemez. |
| -A, --all | » | Aktif -**.**- ve üst dizin -**..**- isimleri listelenmez. |
| -b, --escape | » | Basılamayan karakterler öncesi **"\\"** karekteri ile gösterim. -space- |
| -B, --ignore-backups | » |  "**~**" ile biten dosyaları listelemez.  |
| --color[=koşul] | » | Dosya türüne göre renklendirme. **auto, never, always** |
| **-d, --directory** | » | dizinlerin içeriklerini değil kendisini listeler. |
| -F, --classify | » | Sınıfa göre isimlerin sonuna ***/=@\|** karakterlerinden birini ekleyerek listeler. |
| --file-type | » | Türe göre isimlerin sonuna **/=@\|** karakterlerinden birini ekleyerek listeler. Çalıştırılabilir -**\***- dosyaları işaretlemez |
| -h, --human-readable | » | Boyut bilgisini birimlere dönüştürerek -**kolay okunablir**-  görüntüler. **16G, 20M, 10K**  |
| -i, --inode | » | Her bir dosyayı index numarası ile listeler. |
| -l | » | Uzun -detaylı- biçiminde listeleme yapar. |
| -m, -- | » | Dosyaları **,** ile ayırarak listeleme yapar. |
| -r, --reverse | » | Sıralamayı tersine çevirir. |
| -R, --recursive | » | Alt dizinlerin içeriklerinşi de listeler. |
| --sort=sözcük | » | Sözcüğe göre sıralama yapılır. **size, time, extension, version** |
| -S | » | Boyuta göre sıralama yapar. |
| -t,  | » | Değişiklik zamanına göre sıralar. |
|-Z, --context |  » | Dosyaların **SELinux** güvenlik bağlamını listeler. |
|-1 |  » | Listeleme her satıra bir dosya yazılarak yapılır. |
|||




**ls komutu örnekleri:**

Örnekler için birkaç **dosya, dizin, sembolik bağlantı** oluşturalım:

``` {.sh}
cd && touch file .gizli dosya{1..5}.txt && mkdir Pardus && ln -s file dosya && free > bellek
```

</br>


Ev/home "**~**" dizinindeki dosyaları **ls** ile liteleyelim:
Yukarıdaki komutta **cd** ile ev dizinine konumlandığımız için ev dizinini ~ ile belirtmenize gerek yoktur.


``` {.sh}
ls ~
```

"**.gizli**" dosyası alınan çıktıta listelenmeyecek.

``` {echo}
bellek  dosya1.txt  dosya3.txt  dosya5.txt  Pardus
dosya   dosya2.txt  dosya4.txt  file
```

---

</br>

Tüm dosyaları listeleme:

``` {.sh}
ls --all ~
```

"Ev -**home** -dizinindeki **.**" ile başlayan dosyalar da listeye dahil ediliyor.

``` {echo}
.              .bash_logout  .cache   dosya1.txt  dosya4.txt  .gizli
..             .bashrc       .config  dosya2.txt  dosya5.txt  Pardus
.bash_history  bellek        dosya    dosya3.txt  file        .profile
```


---

</br>

Aktif ( **.** ) ve üst dizin ( **..** ) hariç liste:

``` {.sh}
ls -A ~
```


``` {echo}
.bash_history  bellek   dosya       dosya3.txt  file    .profile
.bash_logout   .cache   dosya1.txt  dosya4.txt  .gizli
.bashrc        .config  dosya2.txt  dosya5.txt  Pardus
```

---

</br>

Türleri belirtmek için dosya sonlarına **/=@\|**  karakterlerinden birini ekleyerek listeleyelim:

``` {.sh}
ls --file-type ~
```

``` {echo}
bellek  dosya1.txt  dosya3.txt  dosya5.txt  Pardus/
dosya@  dosya2.txt  dosya4.txt  file
```

---

</br>
Çıktıyı "**,**" ile ayırarak listeleme:

``` {.sh}
ls -m ~
```

``` {echo}
bellek, dosya, dosya1.txt, dosya2.txt, dosya3.txt, dosya4.txt,
dosya5.txt, file, Pardus
```
---

</br>

Alt dizinlerin içerikleri ile listeleme: 
Öncelikle Pardus dizinine bir dosya kopyalayalım.

``` {.sh}
cp 
```



``` {.sh}
ls -R
```


``` {echo}
.:
bellek  dosya1.txt  dosya3.txt  dosya5.txt     file
dosya   dosya2.txt  dosya4.txt  dosya-listesi  Pardus

./Pardus:
dosya
```

---

</br>


"**d**" ile başlamayan dosyaların index numarasını yazdırma:

``` {.sh}
ls -i ~/[^d]*
```

``` {echo}
3971652 /home/senol/bellek  3943721 /home/senol/file

/home/senol/Pardus:
```

---

</br>


"**txt**" uzantılı dosyaları tek sütun halinde ada göre azalan biçimde listeleme:

``` {.sh}
ls -1r ~/*.txt
```


``` {echo}
dosya5.txt
dosya4.txt
dosya3.txt
dosya2.txt
dosya1.txt
```
---

</br>

Dosya sisteminin kökündeki -**root "/"**- dosya listesi:

``` {.sh}
ls /
```


``` {echo}
bin   home            lib32       media  root  sys  vmlinuz
boot  initrd.img      lib64       mnt    run   tmp  vmlinuz.old
dev   initrd.img.old  libx32      opt    sbin  usr
etc   lib             lost+found  proc   srv   var
```



---

</br>

Dosyaları **detaylı** listeleme:

``` {.sh}
ls -l ~
```


``` {echo}
total 8
-rw-r--r-- 1 senol senol  207 Feb 20 11:19 bellek
lrwxrwxrwx 1 senol senol    4 Feb 20 11:19 dosya -> file
-rw-r--r-- 1 senol guest    0 Feb 20 11:19 dosya1.txt
-rw-r--r-- 1 senol guest    0 Feb 20 11:19 dosya2.txt
-rw-r--r-- 1 senol guest    0 Feb 20 11:19 dosya3.txt
-rw-r--r-- 1 senol guest    0 Feb 20 11:19 dosya4.txt
-rw-r--r-- 1 senol guest    0 Feb 20 11:19 dosya5.txt
-rw-r--r-- 1 senol senol    0 Feb 20 11:19 file
drwxr-xr-x 2 senol senol 4096 Feb 20 11:19 Pardus
```
</br>

"**l**" seçeneği ile alınan çıktıda sırasıyla;

Dosyanın;
* türü,
* erişim izinleri,
* bağlantı sayısı,
* sahibi,
* grubu,
* boyutu,
* erişim zamanı,
* adı

bilgileri listelenir.

Örnek:

drwxr-xr-x 2 senol senol 4096 Feb 20 14:54 Pardus


| d | rwxr-xr-x | 2 | senol | senol | 4096 | Feb 20 14:54 | Pardus |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|tür|izinler|link|sahip|grup|boyut|zaman|isim|
||

**Tür:** 
</br>
* "**-**" : Normal dosya
* "**d**" : Directory (dizin)
* "**l**" : Symbolic link (sembolik bağ)
* "**c**" : Character special device (karakter aygıt)
* "**b**" : Block special device (blok aygıt)
* "**p**" : Fifo -Pipe file-
* "**s**" : Socket

**İzinler:** rwxr-xr-x


* **r** : Read -okuma-
* **w** : Write -yazma- 
* **x** : eXecute -çalıştırma- 
* **s** : SUID -Set User ID- / SGID -Set Group ID-
* **t** : Sticky Bit

İzinler kısmında 9 karakterden oluşan "**rwxr-xr-x**" gibi bir veri görüyoruz. 

Bu veri, 3'er li gruplar hailinde;

* sahibinin,
* aynı gruptaki kullanıcıların,
* diğer kullanıcıların

dosya üzerindeki haklarını gösterir.

</br>

"**rwxr-xr-x**" izinlerini örnekleyelim:


| rwx | r-x | r-x | 
|:--:|:--:|:--:|
| sahibi / user -owner-| grubu -group | diğer -others-|
|**okuyabilir, yazabilir, çalıştırabilir** | **okuyabilir, çalıştırabilir** | **okuyabilir, çalıştırabilir** |
||

Erişim izinlerini belirleme hakkında detaylı bilgilere "**chmod**, **umask**" komutları ve "**Kullanıcı Yönetimi**" başlığına bakabilirsiniz. 

---

</br>

>**ls** komutu ile aldığımız listeyi bir dosyaya yazdırabiliriz. 




``` {.sh}
ls > dosya-listesi
```

``` {echo}
ls -m ~
```

``` {echo}
bellek, dosya, dosya1.txt, dosya2.txt, dosya3.txt, dosya4.txt,
dosya5.txt, dosya-listesi, file, Pardus
```

---

</br>


>**ls** komutu ile aldığımız çıktıya başka bir komuta giriş -input- olarak gönderebiliriz.

listede **txt** ifadesi geçen satırlar: -Bu liste **.txt** türündeki dostalar anlamına gelmez.-

``` {.sh}
ls -1 | grep txt
```

``` {echo}
dosya1.txt
dosya2.txt
dosya3.txt
dosya4.txt
dosya5.txt
```


</br>

---

[Dosya Sistemi Hiyerarşisi](../unix-gnu-linux-dosya-sistemi-yapisi/tr_unix-gnu-linux-dosya-sistemi-yapisi.md) << Önceki / Sonraki >> [Dosya Yönetimi -Kopyalama- -cp-](./tr_dosya-yonetimi-dosya-kopyalama-cp-.md)

