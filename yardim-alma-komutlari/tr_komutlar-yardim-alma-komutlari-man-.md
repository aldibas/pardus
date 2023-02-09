## **Terminal & Kabuk -Shell- Komutları**

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

>Kılavuz dosyasından **q** ile çıkış yapabilirsiniz.

>Kılavuz dosyalarında, **Enter** -giriş- tuşu ile satır satır, **Space** -boşluk- tuşu ile sayfa sayfa haraket edebilirsiniz.

>Klavuz dosyalarında arama yapmak için, arama mentinden önce "**/**" -aşağı yönde-, ve "**?**" -yukarı doğru- karakterleri kullanılır.


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

| Seçenek | | Anlamı |
|--|:--:|--|
| -f, --whatis | » | Kılavuz dosyasının tanım **NAME** kısmını -kısa bilgi- görüntüler.|
| -k, --apropos | » | Klavuz dosyalarının **NAME** kısmında anahtar kelimeyi arar.  |
| -K, --global-apropos | » | Tüm kılavuz sayfalarında metni arar. |
| -M, --manpath | » | Kılavuz dosyası konumunu belirler. Farklı dillerde yardım almak için kullanılabilir. |
| -i, --ignore-case | » | BÜYÜK/küçük harf duyarlılığını kaldırır. Öntanımlı olarak gelir.|
| -I, --match-case | » | BÜYÜK/küçük harf duyarlılığı yapar. |

<br>

<br>
Örnekler:

---
ls komutunun kısa açıklaması için;

``` {.sh}
man -f ls
```
"**-i**" seçeneği öntanımlı oldugundan oyun bölümü kılavuz dosyası olan "**LS**" için kısa açıklama -TANIM- bilgisi de gelecektir.

Çıktı:

```
senol@pardus:~$ man -f ls
LS (6)  - display animations aimed to correct users who accidentally enter LS instead of ls.
ls (1)  - list directory contents

```

---



</br>

---
 **-k** seçeneği ile, kılavız dosyalarının **isim & tanım** -**NAME**- kısımlarında arama yapabiliriz. 


``` {.sh}
man -k "user password"
```

**"user password"** anahtar kelimesine göre ilgili komutların listesi:

```
senol@pardus:~$ man -k "user password"
chage (1)   - change user password expiry information
passwd (1)  - change user password
```
<br>

>Yukarıdaki örnekten de anlaşılacağı üzere **-k** seçeneği, **apropos** komutu gibi, bir amaca yönelik kullanabileceğimiz komutları listeleyerek yol seçmemizi sağlar. Kullanmanız gereken komutu belirledikten sonra yine **man** komutu ile kullanımı hakkında bilgi alabilirsiniz.






---


</br>

 [Dosya adları ve Joker karakterler](../terminal-kullanimi/tr_dosya-adlari.md) << Önceki / Sonraki >> [Yardım alma komutları -whatis-](./tr_komutlar-yardim-alma-komutlari-whatis-.md)

