## **Terminal & Kabuk -Shell- Komutları**

### Metin İşleme Komutları 

#### **cat** -Concatenate-


</br>

**cat** komutu; Bir veya birden çok dosya içeriğini kaynağa ekrana -sdtout- yazar. Birden fazla dosya belirtilmiş ise bu içerikler standard çıktıya kaynağına -stdout- birleştirilerek yazılır. Bu içerikler "**>", ">>"** karakterleri ile bir dosyaya yönlendirilebilir. 
<br>

Komutun argümanlarına geçmeden en temel kullanım şekillerine bakabiliriz.

1.) Dosya içeriklerini yazdırma </br>


``` {echo}
cat file_name
```

Bu kullanım, file_name ile belirtilen dosyanın içeriğini görüntüler. </br>

2.) Dosya içeriklerini birleştirme

``` {echo}
cat file-1 file-2 file-3 
```

Bu kullanımda file[1-3] dosyaları standart çıktıya birleştirilir. Birleştirilmiş içeriği bir dosyaya yazmak için **>, >>** kullanılabilir.

``` {echo}
cat file-1 file-2 file-3 > file-123
```

3.) Dosya içeriğini bir programa gönderme.

``` {echo}
cat file-123 | sort
```

Bu kullanımlardaki yönlendirmeler cat komutuna özgü olmayıp daha önceki stdout, stderr yönlendirme başlığında örnekler ile incelemiştik. 

</br>

**Komutun dizilimi;**


```
cat [OPTIONS] [FILE] [FILE] ...
```

<br>

Komut seçenekleri : -**OPTIONS**- [-AbsentTEuv --help --version] 

| Seçenek | | Açıklama |
|--|:--:|--|
| -E, --show-ends | » | Satır sonlarını -linefeed_LF- **$** ile görüntüler. |
| -T, --show-tabs | » | **tab** karakterlerini **^I** olarak görüntüler  |
| -v, --show-nonprinting | » | Basılamayan karakterler **^** ve **M-** ile öncelenerek gösterilir. Sekme ve satırsonu -**LFD**- hariç. |
| -A, --show-all | » |  Dosyanın içerisindeki tüm karakterleri görüntüler. **tab, boşluk, enter, ...**  |
| -b, --number-noblank | » | Boş olmayan satırları numaralandırarak yazar. |
| **-n, --number** | » | Tüm satırları numaralandırarak yazar. |
| -s, --squeeze-blank | » | ardışık boş satırları **tek** satır olarak görüntüler. |
| -, -- | » |  |
| -, -- | » |  |
| -, -- | » |  |
| -, -- | » |  |

|||





**cat** çıktı Örnekleri:

Öncelikle aşağıdaki komut ile sistemimizde FLD, TAB, TR karakterleri içeren Pardus isminde bir dosya oluşturalım.

``` {.sh}
echo -e "Merhaba Dünya\n\n\nPardus\n\tAnadolu\n\t\tParsı" > Pardus
```
**ls** komutu ile dosyamızı görebilir **cat** komutu ile içeriğini yazdırabiliriz.


``` {.sh}
ls
```


---

``` {.sh}
cat Pardus
```

**cat** komutu ile alacağımız çıktıda görüntü şu şekilde olacaktır:

```
Merhaba Dünya


Pardus
	Anadolu
		Parsı
```
---

Aynı çıktıyı cat komutunun bazı argümanları ile alalım:


Tüm satırlar numaralandırııyor;

``` {.sh}
cat -n Pardus
```


```
     1	Merhaba Dünya
     2	
     3	
     4	Pardus
     5		Anadolu
     6			Parsı
```

---

Boş olan satırlar atlanarak numaralandırılıyor;

``` {.sh}
cat -b Pardus
```


```
     1	Merhaba Dünya


     2	Pardus
     3		Anadolu
     4			Parsı
```

---
Ardışık boş satırlar tek satır halinde görüntülenerek numaralandırılıyor;

``` {.sh}
cat -ns Pardus
```

```
     1	Merhaba Dünya
     2	
     3	Pardus
     4		Anadolu
     5			Parsı
```

---

Satırsonu -**LFD**-- karakteri olarak **$** yazdırılıyor;

``` {.sh}
cat -E Pardus
```

```
Merhaba Dünya$
$
$
Pardus$
	Anadolu$
		Parsı$
```
---

Sekme -**TAB**- karakteri **^I** şeklinde yazdırılarak görüntüleniyor;

``` {.sh}
cat T- Pardus
```

```
Merhaba Dünya


Pardus
^IAnadolu
^I^IParsı
```

---

Sekme -**TAB**- ve satırsonu -**LFD**- hariç basılamayan karakterler ile görüntüleniyor; 

``` {.sh}
cat T- Pardus
```

```
Merhaba DM-CM-<nya


Pardus
	Anadolu
		ParsM-DM-1
```

Basılmayan karakterleri web üzerinde "non printable characters" ifadesiyle aramama yaparak ulaşabilirsiniz.
Bu çıktıda Türkçe karakterlerin gösterimine dikkatli bakın.

---

Tüm içeriği görüntüleniyor; 

``` {.sh}
cat A- Pardus
```

```
Merhaba DM-CM-<nya$
$
$
Pardus$
^IAnadolu$
^I^IParsM-DM-1$
```
---
</br>

>**cat** komutu ile dosya oluşturabiliriz. Aşağıdaki kullanımda içeriği girdikten sonra dosyayı sonlandırmak için **Ctrl**+**D** tuşlarını kulllanın.

```
cat > newfile
```

Dosyayı sonlandırdığımızda "newfile" isimli dosyayı **ls** ile listeleyebiliriz..

---

</br>

Sistemimizdeki birkaç dosyayı cat ile görüntüleyelim:

</br>

Kullanıcı dosyası:

```
cat /etc/passwd
```

Grup dosyası:

```
cat /etc/group
```

**passwd** dosyasında **root** içeren satırlar:

```
cat /etc/passwd | grep root
```


</br>

---

 [Sistem & Durum Bilgisi Komutları -df-](../sistem-durum-bilgisi-komutlari/tr_komutlar-sistem-durum-bilgisi-komutlari-df-.md) << Önceki / Sonraki >> [Metin İşleme Komutları/Text Manipulation -more-](./tr_komutlar-metin-isleme-komutlari-more-.md)

