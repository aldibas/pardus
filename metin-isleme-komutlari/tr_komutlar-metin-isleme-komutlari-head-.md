## **Terminal & Kabuk -Shell- Komutları**

### Metin İşleme Komutları 

#### **head** 


</br>

</br>

**head** komutu; bir dosyanın ilk birkaç satırını gösterir. Başlık komutu, bir dosyanın içeriğini hızlı bir şekilde gözden geçirmenizi ve dosyanın genel yapısını anlamanızı sağlar.


</br>
Başlık komutu, varsayılan olarak dosyanın ilk 10 satırını gösterir. Ancak, kullanıcılar farklı bir satır sayısı belirtebilirler. Komutun kullanımı oldukça basittir:

kullanımı şu şekildedir:
``` {.sh}
head file_name
```

<br>

Bu komut, varsayılan olarak belirtilen dosyanın ilk 10 satırını görüntüler. Kullanıcılar, komuta "-n" seçeneği ile farklı bir sayı belirterek farklı bir satır sayısı belirleyebilirler. Örneğin:

```
head -n 20 file.txt
```
Bu komut, "file.txt" dosyasının ilk 20 satırını görüntüler.

<br>

Ayrıca, kullanıcılar birden fazla dosyayı aynı anda görüntülemek için birden fazla dosya adını da komuta ekleyebilirler. Örneğin:

```
head file1.txt file2.txt
```

Bu komut, "file1.txt" ve "file2.txt" dosyalarının her birinin ilk 10 satırını görüntüler.

<br>

Başlık komutu aynı zamanda "tail" komutu ile birlikte kullanılarak dosyanın belirli bir bölümünü görüntülemek için de kullanılabilir. Örneğin:  

```
head -n 20 file.txt | tail -n 10
```

Bu komut, "file.txt" dosyasının ilk 20 satırını gösterir ve daha sonra bu 20 satırın son 10 satırını alarak gösterir.

<br>


**Komutun dizilimi;**

```
head [OPTIONS] FILE
```

Komut seçenekleri : -**OPTIONS**- [-cnqvz]


| Seçenek | | Açıklama |
|:--:|:--:|--|
| -n --lines| » |  Belirtilen dosyanın ilk, girilen sayıdaki satırını ekrana yazdırır. "n" sayısı, 1'den büyük bir tam sayı olmalıdır.|
| -c --byte| » | Belirtilen dosyanın ilk, girilen sayıdaki byte'ını (bayt) ekrana yazdırır.|
| -q | » | Belirtilen dosyaların başlıklarını görmezden gelerek, ilk 10 satırını her biri için ekrana yazdırır.|
| -v | » | Dosyanın adını başlık olarak görüntüler ve ardından ilk 10 satırını ekrana yazdırır.|
| -z | » | Dosyanın adını görmezden gelerek, null karakteriyle biten ilk satırı ekrana yazdırır. Bu seçenek genellikle binary dosyalarla çalışmak için kullanılır.|
|||

<br>

>**Bazı Örnekler:**

<br>

"updatedb.conf" dosyasının ilk 5 satırını görüntüleme:

```
head -n 2 /etc/updatedb.conf
```
ayrıca -n komutu kullanmadan da komut girilebilir. Yani yalnızca

```
head -2 /etc/updatedb.conf
```
şeklinde de çalışabilir.

<br>

Ekran çıktısı şu şekilde olacaktır:

```
PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"

```

"head" komutu, bir dosyanın başlangıcından belirli bir sayıda satırı görüntülemek için kullanılan bir araçtır. Yukarıdaki örneklerde de gösterildiği gibi, "head" komutu farklı parametrelerle kullanılabilir ve özellikle büyük dosyaları hızlı bir şekilde gözden geçirmek için kullanışlıdır. Bu nedenle, "head" komutunu öğrenmek, dosya işleme ve yönetimi ile ilgili birçok görevde faydalı olacaktır.



</br>

---

 [Metin işleme komutları -wc-](./tr_komutlar-sistem-durum-bilgisi-komutlari-wc-.md) << Önceki / Sonraki >> [Metin işleme komutları -tail-](./tr_komutlar-metin-isleme-komutlari-tail-.md)

