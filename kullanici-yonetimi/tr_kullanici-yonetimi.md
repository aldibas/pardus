# **Terminal & Kabuk -Shell- Komutları**

## Kullanıcı Yönetimi

</br>

Kullanıcı hesapları, kullanıcının kimliği, parolası, ev dizini, kullanıcının grupları gibi özellikleri içerir.

“Kullanıcı ve Gruplar” ile kullanıcı bilgilerimizi değiştirebiliriz. Varsa yetkimiz dahilinde şu işlemleri de gerçekleştirebiliriz;
* Yeni kullanıcı ekleme -**adduser-**/**-useradd**-,
* Sistemdeki bir kullanıcıyı silme **deluser-**/**-userdel**-,
* Kullanıcı Bilgileri ve Parola Değiştirme -**usermod**-/**passwd**-,
* Kullanıcı Hesap Tipini Değiştirme,
* Grup Ekleme -**addgroup**-/-**groupadd**-,
* Grup Silme -**groupdel**-,
* Kullanıcıyı Gruba Ekleme **newgrp**.



Kullanıcılar ile ilgili dosyalar:
---

</br>

>Kullanıcı dosyası **/etc** dizinindeki **passwd** dosyasıdır.

``` {.sh}
cat /etc/passwd
```

"**passwd**" dosyasından örnek bir satır -kayıt-.

``` {echo}
senol:x:1000:1000:Senol ALDIBAS,,,:/home/senol:/bin/bash
```

Dosyadaki alanların açıklaması
- Kullanıcı adı
- x (Artık shadow dosyasında tutulan parola alanı)
- Kullanıcı numarası(ID)
- Grup numarası(GID)
- Kullanıcı açıklaması
- Ev dizini
- Kullanıcı kabuğu (SHELL)

> `man 5 passwd` komutu ile dosya içeriği ile ilgili detaylı bilgi alabilirsiniz.

---

>Kullanıcı grupları  **/etc** dizinindeki **group** dosyasındadır.

``` {.sh}
cat /etc/group
```

"**group**" dosyasından örnek birkaç satır -kayıt-.

``` {echo}
root:x:0:
sudo:x:27:senol
audio:x:29:pulse,senol
lpadmin:x:118:senol
senol:x:1000:
```
</br>
---
</br>

>Kullanıcı parolaları  **/etc** dizinindeki **shadow** dosyasıdır.

</br>

Parola ve parola kullanım süresi, değiştirme süresi gibi tanımlar ise **/etc/shadow** dosyasında tutulmaktadır. **/etc/passwd** dosyasını kullanıcılar okuyabiliyorken **/etc/shadow** dosyasına sadece root kullanıcısı erişebilmektedir.



``` {.sh}
cat /etc/shadow
```

Komut çıktısı:
``` {.echo}
root:*:19104:0:99999:7:::
guest:$y$j9T$AZ3ODu1UVqFU2cTwdmtvL1$/iq1y5KqApS/aFViskCnLR98VFWIa1mL1CsKMqWPId7:19411:0:99999:7:::
```



- Kullanıcı adı
- Şifrelenmiş parola
- Parolanın en son değişim tarihi
- Asgari parola değiştirme periyodu
- En uzun parola geçerlilik süresi
- Parolanın son kullanma tarihi
- Parolanın etkisizleştirilmesinden sonraki toplam gün sayısı


> `man 5 shadow` komutu ile dosya içeriği ile ilgili detaylı bilgi alabilirsiniz.




</br>
---
</br>

Kullanıcılar ile ilgili önemili nottalardan biri de kullanıcı taslak dosyalarının bulunduğu "**/etc/skel**" dizinidir.

"**adduser**" komutu ile her yeni kullanıcı açıldığında kullanıcı ev dizinine bu "**/etc/skel**" dizinindeki dosyalar otomatik olarak kopyalanır.




Bu klasördeki varsayılan dosyalar:


``` {.sh}
ls -a /etc/skel
```

``` {echo}
.  ..  .bash_logout  .bashrc  .config  .profile
```

---


### **Kullanıcı Ekleme** -adduser- & -useradd-

Sistem yöneticileri, yeni kullanıcı hesapları ekleyebilir veya mevcut hesapları silebilir.

``` {.sh}
useradd cuneyt
```
komutu ile **cuneyt** isminde bir kullanıcı ekleyebilir.

``` {.sh}
useradd -s /bin/bash -m -d /home/senol -g root senol
```
komutu ile **bash**, **ev** ve **group** bilgileri tanımlanarak **senol** isminde kullanıcı oluşturabilirsiniz.


Dosyadaki alanların açıklaması

Sisteme kullanıcı eklemek için grafik arayüzü araçları kullanılabileceği gibi kabukta useradd komutu kullanılabilir. Bu komut root kullanıcısı tarafından çalıştırılır. Parametre olarak sadece kullanıcı adı verilirse aynı kullanıcı adına ait bir grup da oluşturulup kullanıcı grubu olarak bu grup tanımlanacaktır. Komutun genel parametreleri şunlardır.

- **m** kullanıcı ev dizinini oluştur
- **d** kullanıcı ev dizini yolu
- **s** kullanıcı kabuğu
- **g** kullanıcı grubu
- **c** Açıklama

Belirtilmeyen parametrelerle ilgili ön tanımlı değerler **/etc/login.defs** dosyasından alınır.

Kullanıcı tanımlandıktan sonra parola ataması yapılmalıdır. 

``` {.sh}
passwd cuneyt
```
komutu ile parola tanımlayabilirsiniz.

Kullanıcı oluşturulduktan sonra aşağıdaki komutlarla kullanıcı ayarlarında değişiklik yapılabilir.

### usermod

Bu komut ile kullanıcı ilave gruplara eklenebilir , mevcut kullanıcı adı başka bir kullanıcı ile değiştirilebilir, kullanıcı hesabı kilitlenebilir veya hesap kilidi kaldırılabilir.

**cuneyt** kullanıcısının hesabını kilitlemek için **-L** parametresi kullanılır.

Örnek kullanımı:
``` {.sh}
usermod -L cuneyt
```

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




Kullanıcı parolaları: Kullanıcılar, parola oluşturma, değiştirme ve sıfırlama işlemleri yapabilirler. "passwd" komutu, kullanıcı parolalarını değiştirmek için kullanılır.


### userdel

**userdel** komutu ile kullanıcı silebilirsiniz.

``` {.sh}
userdel cuneyt
```
komutu ile **cuneyt** kullanıcısını silebilirsiniz.

Yukarıdaki komut çalıştırıldığında ev dizini silinmez. Kullanıcıyı ev dizinindeki dosyalarla birlikte tamamen silmek için **-r** parametresi kullanılır.

### Kullanıcı Girişlerini Kısıtlama

**Root** dışındaki kullanıcıların geçici olarak sisteme girişini engellemek için **/etc/nologin** dosyası oluşturmak yeterlidir. Kullanıcı giriş yapmaya çalıştığında bu dosyadaki yazan metin ekrana yazılacak kullanıcının girişine izin verilmeyecektir. Eğer tek bir kullanıcının giriş yapması engellenmek isteniyorsa usermode **-L** veya **passwd -l** komutu ile kullanıcı hesabı kilitlenebilir. Veya kabuğu **/sbin/nologin** yapılabilir. FTP yapabilsin, fakat ssh yapamasın isteniyorsa da kullanıcı kabuğunun **/bin/false** olarak değiştirilmesi gerekir. 



``` {.sh}
adduser can
```
komutu ile can isminde bir kullanıcı oluşturalım.


``` {.sh}
ls -al /home/can/
```
komutu ile **can** kullanıcısının ev dizini listeleyelim:

Komut çıktısı:

``` {.echo}
drwxr-xr-x 2 can  can    57 Jan 27 07:50 .
drwxr-xr-x 1 root root   17 Jan 27 07:50 ..
-rw-r--r-- 1 can  can   220 Jan 27 07:50 .bash_logout
-rw-r--r-- 1 can  can  3691 Jan 27 07:50 .bashrc
-rw-r--r-- 1 can  can   807 Jan 27 07:50 .profile
```

``` {.sh}
touch /etc/skel/merhaba
```
komutu ile **/etc/skel/** dizini içerisine **merhaba** isminde bir dosya oluştularım:



``` {.sh}
adduser ayse
```
komutu ile **ayse** isminde bir kullanıcı oluşturalım.


``` {.sh}
ls -al /home/ayse/
```
komutu ile **ayse** kullanıcısının ev dizini listeleyelim:

Komut çıktısı:



``` {echo}
.  ..  .bash_logout  .bashrc   .profile   merhaba
```




**merhaba** dosyasını oluşturmadan önce **can** kullanıcısını oluşturduğumuz için, **can** kullanıcısın ev dizininde **merhaba** isminde dosya <u>**bulunmamaktadır.**</u>

**merhaba** dosyasını oluşturduktan sonra **ayşe** kullanıcısını  oluşturduğumuz için, **ayşe** kullanıcısını ev dizininde **merhaba** isminde dosya <u>**bulunmaktadır.**</u>

>Bu dizine <u>(/etc/skel/)</u> açılacak her bir yeni dosya yeni kullanıcıların ev dizinine kullanıcı hakları ile kopyalanacaktır.

### su ve sudo komutu
**su** komutu mevcut kabukta iken çıkmadan başka bir kullanıcı hakları ile kabuk açmak için kullanılır. Geçiş yapılmak istenen kullanıcı ise genelde **root** kullanıcısıdır. Bu komutun en yaygın parametresi **-** dir. 

Bu parametre kabuk geçişinde yeni kullanıcının çevre değişkenleri ile geçiş yapılmasını sağlar. 
``` {.sh}
su -
```

Komut çıktısı:
``` {.echo}
Parola:
```
Parola kısmına hedef (burada root) kullanıcısının parolası girilmelidir. Bu durumda **root** haklarına sahip olmak isteyen herkesin root parolasını bilmesi gerekecekir. Root parolasının birden fazla kişi tarafından bilinmesi güvenlik zaafiyeti oluşturacağı için **su** komutuna alternatif olarak **sudo** komutu geliştirilmiştir.

**Sudo** komutunun **su** komutundan en önemli farkı kullanıcıya verilen yetkileri yine kullanıcı kendi parolasını girerek kullanabilmektedir. Bu sayede kullanıcıların root parolasını bilmesine gerek kalmadan root gibi işlemler yapabilmektedir. **/etc/sudoers** dosyasında izin verilen komutları çalıştırmak için ilgili komutun başına sudo komutunu eklemek yeterli olacaktır.


----
