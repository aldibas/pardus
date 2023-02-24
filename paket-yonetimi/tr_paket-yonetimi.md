# **Terminal & Kabuk -Shell- Komutları**

## Paket Yönetimi

</br>

Pardus, 2012 yılında Debian tabanlı paket sistemine geçiş yapmış ve 2013 yılında Debian tabanlı ilk sürümünü çıkartmıştır. Bu konuyu "Pardus Hakkında" kısmında ele almıştık.

Debian ile ilgili detaylı bilgi için [buraya tıklayarak sitesini ziyaret edebilirsiniz. ](https://www.debian.org/)

Debian, özgür bir işletim sistemi olarak, açık kaynak kodlu yazılımlardan oluşan birçok paketi içeren bir depo sistemine sahiptir. Bu paketler, kullanıcıların Debian işletim sistemlerine kolayca kurulum yapabilmelerini sağlar. Bu depo sistemini yönetmek, paketlerin güncellenmesi, depoya yeni paketlerin eklenmesi veya mevcut paketlerin kaldırılması gibi işlemleri kapsar.

Debian paketleri .deb uzantısı ile ifade edilir. 

Debian ile ilgili detaylı bilgi için [buraya tıklayarak sitesini ziyaret edebilirsiniz. ](https://www.debian.org/)

Pardus’ta kullanılacak depoları **/etc/apt/sources.list** dosyasında tanımlanır. Paketlerin internet üzerinde tutulduğu yerlere **depo(repository)** adı verilir.

`cat` komutu ile "**sources.list**" dosyasının içeriğini görüntüleyelim.


``` {.sh}
cat /etc/apt/sources.list
```

"**sources.list**" dosya içeriği:

``` {.echo}
### Official Pardus Package Repositories ###

deb https://depo.pardus.org.tr/pardus yirmibir main contrib non-free
deb-src http://depo.pardus.org.tr/pardus yirmibir main contrib non-free

deb https://depo.pardus.org.tr/guvenlik yirmibir main contrib non-free
deb-src http://depo.pardus.org.tr/guvenlik yirmibir main contrib non-free
```


</br>


</br>

### **apt**

</br>

"**`apt`**" (Advanced Package Tool), Debian ve Debian tabanlı işletim sistemlerinde kullanılan bir paket yönetim aracıdır. APT, depolarda bulunan paketlerin kurulumunu, kaldırılmasını, güncellenmesini ve bağımlılıklarını yönetmek için kullanılır. APT, hem grafiksel kullanıcı arayüzü hem de komut satırı arayüzü (Terminal) üzerinden kullanılabilir.


</br>

### **dpkg** 

</br>

"**`dpkg`**" (Debian Package) komutu, Debian veya Debian tabanlı işletim sistemlerinde, paketlerin kurulumu, kaldırılması ve yönetimi için kullanılan bir araçtır. "dpkg" komutu, "apt" aracından daha düşük seviyede çalışır ve paketlerin işlem sürecinde kullanılan temel komutlardan biridir.

"dpkg" komutunun temel kullanımı şu şekildedir:

Paketin kurulumu:
sudo dpkg -i <paket-adı> : Belirtilen paketi yükler.

Paketin kaldırılması:
sudo dpkg -r <paket-adı> : Belirtilen paketi kaldırır.
sudo dpkg --purge <paket-adı> : Belirtilen paketi ve bağımlılıklarını kaldırır.

Paket bilgilerini görüntüleme:
dpkg -s <paket-adı> : Belirtilen paketin durumunu ve bilgilerini görüntüler.

Kurulu paketlerin listesi:
dpkg -l : Sistemde yüklü olan paketlerin listesini görüntüler.

Paketlerin kontrolü:
sudo dpkg --configure -a : Yüklenemeyen veya kurulumu tamamlanamayan paketleri yapılandırır.

Bu temel komutların yanı sıra, "dpkg" komutunun farklı parametreleri ve seçenekleri de mevcuttur. Bunları görmek için "man dpkg" komutu kullanılabilir.

Ancak, "dpkg" komutunun doğrudan kullanımı, bağımlılıkları yönetme konusunda sınırlıdır. Bu nedenle, "apt" aracı, "dpkg" komutunu otomatik olarak çağırarak, bağımlılıkları dağıtmak için kullanılır. Bu nedenle, "apt" aracı, paket yönetimi için daha uygun ve kullanımı daha kolay bir araçtır.

</br>

### **Paket Güncelleme**
</br>

`apt-get update` ya da `apt update` komutu ile gerçek manada bir paket güncellemesi yapılmaz. Sadece paketin indeks dosyaları ve kaynakları güncellenir. `apt-get upgrade` ile de yeni sürümler kurulur. 


>Paket kurma, paket kaldırma gibi işlemler yetki gerektirdiğinen paket yönetimi ile  ilgili işlemlerde genellikle "**`su`**" komutu ile "**root**" kullanıcısına geçmeniz ya da komutu başına "**sudo**" yazarak (**`sudo apt update`**) çalıştırmanız gerekir. Buradaki Pardus docker imajında ise yetkili -**root**- olarak oturum açmış durumdasınız.


Pardus depolarından -**repository**- en son değişiklikleri çekelim. 

``` {.sh}
apt update
```

`apt upgrade` komutu ile yukarıda "**update**" opsiyonu ile paket veritabanına göre yeni sürümleri kuralım.

``` {.sh}
apt upgrade
```
</br>

>`apt upgrade` kurulu paketlerin kaldırılmasını gerektiren paketleri güncellemez. Tüm sistemi güncellemek için `apt full-upgrade` komutu kullanılabilir.


>Tek bir paketi güncellemek için **upgrade** seçeneğinden sonra paket adı girin.

</br>

>`apt update && apt upgrade` komutları ile düzenli olarak sistemi güncellemek sisteminizin güvenliği için önemlidir.

</br>

### **Paket Kurulumu** -**apt/dpkg**-

</br>

**apt-get install** parametresi veya **dpkg --install** ile Aşağıdaki komutlarla paket kurulabilir.

>apt install package-1 package-1 ...

>apt-get install package-1 package-1 ...

>apt-get install [PATH]/package-name.deb

>dpkg -i package-name.deb

</br>

Paket kurulumunu örneklemek için basit bir program olan `hello` paketini kuralım. 


``` {.sh}
apt install hello
```

>Kurulum işleminde onay istenmemesi için "**-y**" seçeneği ya da "**--allow** ile başlayan seçeneklerden tercih yapılabilir.

>Onay işlemlerinde sunulan "**[Y/n]**", "**[E/h]**" gibi tercihlerde BÜYÜK HARF ile gösterilmiş olan tercih varsayılan tercihtir. Yani "Enter" tuşu ile geçmeniz halinde büyük harf ile gösterilen seçimi tercih etmiş olursunuz.


Kurduğumuz "**hello**" uygulamasını çalıştıralım.

``` {.sh}
hello
```

GNU-Linux/Unix sistemlerde ihtiyacınız olan uygulamalar genellikle depolarda bulunur ve üstteki örnek ile aynı biçimde bunları kurabilirsiniz.   Depolarda bulunmayan paketler ya da depolarda olsa bile güncel sürümünü kullanmak istediğiniz uygulamaları yine `apt` ya da `dpkg`
komutları ile kurabilirsiniz.

---

Örnek oması için screenfetch uygulamasını sistemimize indirerek kuralım.

screenfetch dosyasını `wget` komutu ile indirelim:

``` {.sh}
wget https://depo.pardus.org.tr/pardus/pool/main/s/screenfetch/screenfetch_3.9.1-2_all.deb
```

`ls` komutu ile indirme işleminden sonra gelen dosyanın ismini listeleyelim.

`apt` ya da `dpkg` komutlarından birini tercih ederek paketi kuralım.

``` {.sh}
apt install ./screenfetch_3.9.1-2_all.deb
```

``` {.sh}
dpkg -i screenfetch_3.9.1-2_all.deb
```

Paketi çalıştıralım...

``` {.sh}
screenfetch
```

---

</br>



### Paket Sorgulama 

</br>

`dpkg -l` ya da `dpkg --list` komutu ile sayesinde kurulu paket listesini alabilirsiniz. Bu listede uygulamaların;
* Adı  -Name-,
* Versiyonu -Version-,
* Mimarisi -Architecture-,
* Açıklama -Description-

bilgileri bulunur.


``` {.sh}
dpkg -l
```

Komut çıktısı:
``` {.echo}
||/ Name     Version     Architecture Description
+++-========-===========-============-===========
ii  acl      2.2.53-10   amd64        access control..
ii  adduser  3.118       all          add and remove.. 
...
...
```

>Kurulun paket listesinde `grep` ile filtreleme yaparak bir paketin kurulu olup olmadığını kontrol edebilir,  kurulu ise bilgilerini görebilirsiniz.

``` {.sh}
dpkg -l | grep hello
```


``` {echo}
ii hello  2.10-2  amd64  example package based on GNU hello
```

Bir uygulamanın hangi paket tarafından kurulduğu "**-S** ya da **--search**" parametresi ile sorgulanabilir.


``` {.sh}
dpkg -S /usr/bin/man
```

Yardım almak için kullandığımız `man` komutunun "**man-db**" paketi ile geldiği aşağıdaki çıktıda görülebilir.

``` {.echo}
man-db: /usr/bin/man
```

Bir uygulamaya ait dosya konumları "**-L** ya da **--list-files**" parametresi ile listelenebilir.

``` {.sh}
dpkg -L hello
```

`hello` komutu ve diğer dosya konumları:

``` {.echo}
/usr/bin/hello
/usr/share/doc/hello/copyright
/usr/share/man/man1/hello.1.gz
...
```

`apt` komutunda "**depends**" seçeneği ile bir paketin ihtiyaç duyduğu tüm bağımlılıklar listelenebilir.

``` {.sh}
apt-cache depends hello
```

Bağımlılıklar:

``` {.echo}
hello
  Depends: libc6
  Conflicts: hello-traditional
  Breaks: <hello-debhelper>
  Replaces: <hello-debhelper>
  Replaces: hello-traditional
```

`apt` komutunda "**search**" seçeneği ile bir uygulama depolarda aranabilir.

"**2048**" oyununun tanımlı depolarda bulunup bulunmadığına bakalım.

``` {.sh}
apt-cache search 2048
```

"2048" ifadesine göre arama sonuçları:

``` {.echo}
2048 - Slide and add puzzle game for text mode
2048-qt - mathematics based puzzle game
gnome-2048 - sliding tile puzzle game
```

Terminalde ounamak için "text mode" olan paketi kuralım.


``` {.sh}
apt install 2048
```

``` {.sh}
2048
```

2048 oyununu başlatamıyorsanız "games" konumuna yol -path- tanımı yapılmamış olabilir. PATH değişkenini düzenleyebilir ya da konum bilgisiyle çalıştırabilirsiniz.

Örneğin;

``` {.sh}
/usr/games/2048
```
</br>

### **Paket Kaldırma**

</br>

**`dpkg`** komutunda  "**-r**", **`apt`** komutunda ise **remove** ve **purge** opsiyonları ile paketleri kaldırabiliriz.

</br>

>"**remove**" ve "**purge**" opsiyonları arasındaki fark için komut opsiyonlarına bakabilirsiniz.

</br>

``` {.sh}
apt remove hello
```



``` {.sh}
dpkg -r screenfetch
```